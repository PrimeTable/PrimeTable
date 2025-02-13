<script>
document.getElementById("bookingForm").addEventListener("submit", function(event) {
    event.preventDefault();
    
    var name = document.getElementById("name").value;
    var email = document.getElementById("email").value;
    var guests = document.getElementById("guests").value;
    var datetime = document.getElementById("datetime").value;

    var bookingData = {
        name: name,
        email: email,
        guests: guests,
        datetime: datetime
    };

    fetch("[YOUR_WEBHOOK_URL_HERE](https://script.google.com/macros/s/AKfycbz-sKIAtCZLrM0rz_U4R1lwv-aUlNEYcES0SVMXm60iScHS0ce1wX0zgD8tWxqJZhX6Zg/exec)", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(bookingData)
    })
    .then(response => response.text())
    .then(data => {
        document.getElementById("confirmationMessage").innerText = "Your table has been booked successfully!";
        document.getElementById("confirmationMessage").style.display = "block";
        document.getElementById("bookingForm").reset();
    })
    .catch(error => console.error("Error:", error));
});
</script>

