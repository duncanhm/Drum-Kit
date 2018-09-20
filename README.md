# JavaScript Drum Kit

Defined `data-key` values to audio clips, then wrote the following funcitons to play the sounds and remove transitions to return the styling of the button images to their beginning state:

Play the audio coresponding to data-key value:
```javascript
    function playSound(e) {
        const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
        const key = document.querySelector(`.key[data-key="${e.keyCode}"]`);
        if(!audio) return; // stop the function from running
        audio.currentTime = 0; // restart audio instantly
        audio.play();
        key.classList.add('playing');
    }
```
Remove the transition:
```javascript
    function removeTransition(e) {
        if(e.propertyName !== 'transform') return; // skip it if it's not a transform
        this.classList.remove('playing');
    }
```
Play audio on keydown & remove transition after the CSS transition period has ended:
```javascript
    window.addEventListener('keydown', playSound);
    
    const keys = document.querySelectorAll('.key');
    keys.forEach(key => key.addEventListener('transitionend', removeTransition));
```
