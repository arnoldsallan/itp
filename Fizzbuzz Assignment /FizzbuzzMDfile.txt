For this assignement I did utilize Chat GPT to have it write the code properly, but I asked it do it in a step by step format, which I will list below, as well as attach screenshots in the folder.  

The first thing I did was ask GPT to start with a for loop.  I did this to go through 1 to 100.  The loop inits from i to 1 in increments by 1 on each iteration.  

This was the code for first part. 

for (let i = 1; i <= 100; i++) {
    console.log(i);
}

I then asked GPT to check if its divisible by 3 and 5 by using conditions.  

Updated Code: for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log(i + " is divisible by both 3 and 5");
    }
}

If thats true print fizz buzz

Updated Code: for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    }
}
	
Next step is if this is false, move to next one.  It checks if it's divisble by 3 but not by 5.  

Updated Code: for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) {
        console.log("Fizz");
    }
}
	
Then it checked if i is divisble by 5 

Updated Code: for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) {
        console.log("Fizz");
    } else if (i % 5 === 0) {
        console.log("Buzz");
    }
}
	
Next was to print number if none of the things were true. 
	
Updated Code: for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) {
        console.log("Fizz");
    } else if (i % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(i);
    }
}

Last step was to have it repeat until it reaches 100.  The loop will go repeating all the steps until it reaches the number. 

Final Code: for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) {
        console.log("Fizz");
    } else if (i % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(i);
    }
}

I then went to check the code using the Java sandbox you showed us in class.  


The reason I decided to use GPT for this assignment is so I didn't mess up typing out the code line for line.  It definitely helped me understand how to use loops and conditions in this format.  I made sure to check the code myself to see if it ran properly, which it seemed like it did.  I see the value of using a GPT like thing to help with these kinds of things, especially for someone like myself who is really bad with numbers and math, but I also see that you can't just trust it wholeheartedly, and that you need to triple check your work! 

