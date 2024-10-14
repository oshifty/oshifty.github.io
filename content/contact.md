---
title: Contact
date: 2021-12-18T03:10:36.000Z
draft: false
language: en
description: A test with @tailwindcss/typography & Prose
---

<!-- @format -->

<section class="lg:pb-24">
  <div class="max-w-screen-md px-4 mx-auto">
      <p class="mb-8 font-light text-center text-gray-500 lg:mb-16 dark:text-gray-400 sm:text-xl">Got some ideas or opinions on SHIFTY? Want to send feedback? Like to test or contribute? Let us know.</p>
      <form name="contact" class="space-y-8" action="https://api.web3forms.com/submit" method="POST">
        <input type="hidden" name="access_key" value="1964445e-7fb0-476c-8253-ff61fcdeaeb8" />
        <input type="hidden" name="subject" value="SHIFTY Contact Form Submission" />
        <input type="checkbox" name="botcheck" class="hidden" style="display: none;">
        <input type="hidden" name="redirect" value="https://oshifty.vision/contact/thanks">
        <input type="hidden" name="from_name" value="SHIFTY" />
            <div class="my-4">
              <label for="email" class="block mb-2 font-medium text-gray-900 text-md dark:text-gray-300"><strong>Your Email:</strong></label>
              <input name="email" type="email" id="email" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-md rounded-lg focus:ring-indigo-500 focus:border-indigo-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-indigo-500 dark:focus:border-indigo-500 dark:shadow-sm-light" placeholder="name@example.com" required>
          </div>
          <div class="my-4">
              <label for="title" class="block mb-2 font-medium text-gray-900 text-md dark:text-gray-300"><strong>Subject:</strong></label>
              <input name="title" type="text" id="title" class="block w-full p-3 text-gray-900 border border-gray-300 rounded-lg shadow-sm text-md bg-gray-50 focus:ring-indigo-500 focus:border-indigo-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-indigo-500 dark:focus:border-indigo-500 dark:shadow-sm-light" placeholder="Let us know how we can help you" required>
          </div>
          <div class="my-4 sm:col-span-2">
              <label for="message" class="block mb-2 font-medium text-gray-900 text-md dark:text-gray-400"><strong>Your message:</strong></label>
              <textarea name="message" id="message" rows="6" class="block p-2.5 w-full text-md text-gray-900 bg-gray-50 rounded-lg shadow-sm border border-gray-300 focus:ring-indigo-500 focus:border-indigo-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-indigo-500 dark:focus:border-indigo-500" placeholder="Leave a comment..."></textarea>
          </div>
          <div class="mt-6 lg:pb-16">
             <button type="submit" class="px-5 py-3 font-bold text-center text-white bg-indigo-600 rounded-lg text-md sm:w-fit hover:bg-indigo-800 focus:ring-4 focus:outline-none focus:ring-indigo-300 dark:bg-indigo-600 dark:hover:bg-indigo-700 dark:focus:ring-indigo-800">Send Message</button>
          </div>
      </form>

  </div>
</section>

<script>
    // onload fill email field with user's email from get parameter email
    window.onload = function() {
        const urlParams = new URLSearchParams(window.location.search);
        const email = urlParams.get('email');
        if (email) {
            document.getElementById('email').value = email;
            // focus on subject field
            document.getElementById('subject').focus();
        }
    }
</script>
