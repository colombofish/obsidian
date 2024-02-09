Constructor function ex:
function HouseKeeper(name, workExperience, tasksToBeDone) {
    this.name = name;
    this.workExperience = workExperience, 
    this.tasksToBeDone = tasksToBeDone
} // initialize via
var houseKeeper2 = new HouseKeeper("Jane", 12, ["dish washing", "arranging kitchen"]);
To include a method to the constructor f-n above include the following:
this.moveSuitcase: function () {
	pickupSuitcase();
	moveIt();
}
*make sure to call the function with (). ex: houseKeeper2.moveSuitcase()*
*recollect the audio methods declared below*
	var audio = new Audio('sounds/tom-3.mp3');
	audio.play();
*keydown eventListener*
[Event reference | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/Events)
addEventListener("keydown", (event) => {
  handleClick(event.key);
})

*Passing functions as parameters / callbacks. Meaning a f-n take another f-n as in input*
example above the addEventListener is called Higher Order F-n. The f-n which is passed in is called a callback f-n.
*timeout callback f-n*
setTimeout(() => {
    document.querySelector(`.${key}`).classList.toggle("pressed");
    console.log('0.3 sec delay');
  }, 300);