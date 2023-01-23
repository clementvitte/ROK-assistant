<template>
    <body>
        <div class="container">
            <h2>Register/login</h2>
            <input type="text" placeholder="Username" id="username" />
            <input type="password" placeholder="Password" id="password" />
            <button id="submit">Submit</button>
            <p id="message-ref">Sign Up Succesfully !</p>
        </div>
        
        <!--<button data-text="Awesome" class="button">
                    <span class="actual-text">
                        &nbsp;Hello World!&nbsp;
                    </span>
                    <span class="hover-text" aria-hidden="true">
                        &nbsp;Hello World!&nbsp;
                    </span>
                </button> -->
    </body>
</template>

<style lang="css">
@import url("https://fonts.googleapis.com/css2?familly=Poppins:wght@400;600&display=swap");

* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: "Poppins", sans-serif;
}

body {
    background-color: #180148;
}

.container {
    width: 31.25em;
    background-color: #f8f8f8;
    padding: 1.4em;
    position: absolute;
    transform: translate(-50%, -50%);
    top: 50%;
    left: 50%;
    border-radius: 0.7em;
    box-shadow: 0 1em 4em rgba(71, 50, 4, 0.3);
}

h2 {
    text-align: center;
    font-size: 32px;
    margin-bottom: 25px;
    color: rgba(6, 74, 127);
}

input,
#submit {
    border: none;
    outline: none;
    display: block;
}

input {
    width: 100%;
    background-color: transparent;
    margin-bottom: 2em;
    font-size: 20px;
    padding: 1em 0 0.5em 0.5em;
    border-bottom: 2px solid #202020;
}

#submit {
    position: relative;
    left: 0;
    font-size: 1em;
    width: 7em;
    background-color: #096292;
    color: white;
    padding: 0.8em 0;
    margin-top: 2em;
    border-radius: 0.3em;
}

#message-ref {
    font-size: 1em;
    margin-top: 1.5em;
    color: #34bd34;
    visibility: hidden;
}
</style>

<script lang="js">
let usernameRef = document.getElementById('username');
let passwordRef = document.getElementById('password');
let submitBtn = document.getElementById('submit');
let messageRef = document.getElementById('message-ref');

let isUsernameValid = () => {
    const usernameRegex = /^[a-zA-Z][a-za-Z0-9]{3,32}/gi;
    return usernameRegex.test(usernameRef.value);
}

let isPasswordValid = () => {
    const passwordRegex = /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[a-zA-Z]).{8,}$/gm;
    return passwordRegex.test(passwordRef.value);
}

usernameRef.addEventListener("input", () => {
    if (!isUsernameValid()) {
        messageRef.style.visibility = "hidden";
        usernameRef.style.cssText =
            "border-color : #fe2e2e; background-color : #ffc2c2";
    } else {
        usernameRef.style.cssText =
            "border-color : #34bd34; background-color: #c2ffc2";
    }
});

passwordRef.addEventListener("input", () => {
    if (!isPasswordValid()) {
        messageRef.style.visibility = "hidden";
        passwordRef.style.cssText =
            "border-color: #fe2e2e; background-color: #ffc2c2";
    } else {
        passwordRef.style.cssText =
            "border-color: #34bd34; background-color: #c2ffc2";
    }
});

submitBtn.addEventListener("mouseover", () => {
    if (!isUsernameValid() || !isPasswordValid()) {
        let containerReact = document.querySelector("container").getBoundingClientRect();
        let submitReact = submitBtn.getBoundingClientRect();
        let offset = submitReact.left - containerReact.left;
        console.log("offset");
        if (offset <= 100) {
            submitBtn.style.transform = "translateX(16.25em)";
        } else {
            submitBtn.style.transform = "translateX(0)";
        }
    }
});
submitBtn.addEventListener("click", () => {
    messageRef.style.visibility = "visible";
});
</script>


