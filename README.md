# Data-collect
This page is basically for the study purpose and this page is use for the data collection 
<!DOCTYPE html>
<html lang="en">
 
<head>
    <meta charset="UTF-8">
    <title>Collecting Data</title>
    <script src=
"https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js">
    </script>
 
    <link rel="stylesheet" href=
"https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css"
        integrity=
"sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2"
        crossorigin="anonymous">
</head>
 
<body class="container" style="margin-top: 50px;
    width: 50%; height:auto;">
     
    <h2 class="text-primary" style=
        "margin-left: 15px; margin-bottom: 10px">
        Hey There,Help Us In Collecting Data
    </h2>
     
    <form class="container" id="contactForm">
        <div class="card">
            <div class="card-body">
                <div class="form-group">
                    <label for="exampleFormControlInput1">
                        Enter Your Name
                    </label>
                     
                    <input type="text" class="form-control"
                    id="name" placeholder="Enter your name">
                </div>
 
                <div class="form-group">
                    <label for="exampleFormControlInput1">
                        Email address
                    </label>
                     
                    <input type="email" class="form-control"
                    id="email" placeholder="name@example.com">
                </div>
            </div>
            <button type="submit" class="btn btn-primary"
                style="margin-left: 15px; margin-top: 10px">
                Submit
            </button>
        </div>
    </form>
 
    <script src=
"https://www.gstatic.com/firebasejs/3.7.4/firebase.js">
    </script>
     
    <script>
        let firebaseConfig = {
            apiKey: "Use Your Api Key Here",
            authDomain: "Use Your authDomain Here",
            databaseURL: "Use Your databaseURL Here",
            projectId: "Use Your projectId Here",
            storageBucket: "Use Your storageBucket Here",
            messagingSenderId: "Use Your messagingSenderId Here",
            appId: "Use Your appId Here"
        };
 
        firebase.initializeApp(firebaseConfig);
 
        let messagesRef = firebase.database()
            .ref('Collected Data');
         
        document.getElementById('contactForm')
            .addEventListener('submit', submitForm);
 
        function submitForm(e) {
            e.preventDefault();
 
            // Get values
            let name = getInputVal('name');
            let email = getInputVal('email');
 
            saveMessage(name, email);
            document.getElementById('contactForm').reset();
        }
 
        // Function to get form values
        function getInputVal(id) {
            return document.getElementById(id).value;
        }
 
        // Save message to firebase
        function saveMessage(name, email) {
            let newMessageRef = messagesRef.push();
            newMessageRef.set({
                name: name,
                email: email,
            });
        }
    </script>
</body>
 
</html>
