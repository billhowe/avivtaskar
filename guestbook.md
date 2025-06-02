---
layout: page
title: Guestbook
permalink: /guestbook/
---

<form id="guestbook-form">
  <label for="name">Name:</label><br>
  <input type="text" id="name" name="name" required><br>

  <label for="message">Message:</label><br>
  <textarea id="message" name="message" rows="5" required></textarea><br>

  <label for="image">Image URL (optional):</label><br>
  <input type="url" id="image" name="image"><br><br>

  <button type="submit">Submit</button>
</form>

<p id="response"></p>

<script>
document.getElementById('guestbook-form').addEventListener('submit', async function(e) {
  e.preventDefault();
  const payload = {
    name: document.getElementById('name').value,
    message: document.getElementById('message').value,
    image: document.getElementById('image').value
  };

  const res = await fetch("https://your-netlify-site.netlify.app/.netlify/functions/submit-guestbook", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(payload)
  });

  const result = await res.text();
  document.getElementById('response').textContent = result;
  document.getElementById('guestbook-form').reset();
});
</script>
