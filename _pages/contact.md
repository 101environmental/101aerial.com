---
title: "Contact"
permalink: /contact/
---

<form action="https://getsimpleform.com/messages?form_api_token=28e20c67cc9bbaf1effae2eaff6004d3" method="post">
  <input type='hidden' name='redirect_to' value='https://101aerial.com/contact_thanks/' />
  Your name:<input type='text' name='client_name' />
  Your email:<input type='text' name='client_email' />
  Your phone: <input type='text' name='client_phone' />
  Your message: <textarea name="message"></textarea>
  <button type='submit'>Send</button>
</form>

<!-- modify this form HTML and place wherever you want your form -->

<form id="my-form"
  action="https://formspree.io/mjvgaywl"
  method="POST"
>
  <label>Email:</label>
  <input type="email" name="email" />
  <label>Message:</label>
  <input type="text" name="message" />
  <button id="my-form-button">Submit</button>
  <p id="my-form-status"></p>
</form>

<!-- Place this script at the end of the body tag -->

<script>
  window.addEventListener("DOMContentLoaded", function() {

    // get the form elements defined in your form HTML above

    var form = document.getElementById("my-form");
    var button = document.getElementById("my-form-button");
    var status = document.getElementById("my-form-status");

    // Success and Error functions for after the form is submitted

    function success() {
      form.reset();
      button.style = "display: none ";
      status.innerHTML = "Thanks!";
    }

    function error() {
      status.innerHTML = "Oops! There was a problem.";
    }

    // handle the form submission event

    form.addEventListener("submit", function(ev) {
      ev.preventDefault();
      var data = new FormData(form);
      ajax(form.method, form.action, data, success, error);
    });
  });

  // helper function for sending an AJAX request

  function ajax(method, url, data, success, error) {
    var xhr = new XMLHttpRequest();
    xhr.open(method, url);
    xhr.setRequestHeader("Accept", "application/json");
    xhr.onreadystatechange = function() {
      if (xhr.readyState !== XMLHttpRequest.DONE) return;
      if (xhr.status === 200) {
        success(xhr.response, xhr.responseType);
      } else {
        error(xhr.status, xhr.response, xhr.responseType);
      }
    };
    xhr.send(data);
  }
</script>
