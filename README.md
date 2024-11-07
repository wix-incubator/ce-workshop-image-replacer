# Image Replacer Chrome Extension Workshop

Welcome to the **Image Replacer** Chrome Extension workshop! In this workshop, you will learn how to build a Chrome extension using **Manifest v3**. This extension, called "imageReplacer," allows users to save URLs of custom images and automatically replace images on specific websites with randomly chosen images from their list.

## Overview

The *Image Replacer* extension includes a simple user interface for managing a list of image URLs and allows users to enable or disable the image replacement functionality. When active, the extension will replace all images on [ynet.co.il](https://www.ynet.co.il) with a random image from the user's saved list.

### Features

- Save, view, and manage a list of image URLs directly from the extension popup.
- Enable or disable the image replacement feature.
- Replace all images on `ynet.co.il` with random images from the user's list.
- Simple and responsive UI for ease of use.

## Workshop Steps

Below are the steps you’ll need to follow to build the *Image Replacer* Chrome extension. By the end, you will have a fully functional extension that you can publish to the Chrome Web Store!

---

### Steps to Build the Image Replacer Extension

#### 1. Clone the Boilerplate Repo
   - Start by cloning the boilerplate repository provided for the workshop. This repository includes basic files and folders set up for a Chrome extension.
   - Run the following command in your terminal:
     ```bash
     git clone https://github.com/wix-incubator/ce-workshop-image-replacer.git
     cd imageReplacer
     ```

#### 2. Understand the Manifest File
   - The `manifest.json` file is the backbone of your Chrome extension. It tells Chrome what the extension does, what permissions it needs, and which scripts to load.
   - Open `manifest.json` and review its structure. Make sure to set the name of the extension to "imageReplacer" and specify the permissions required (like `storage` and `scripting`).

#### 3. Install the Extension in Chrome
   - Now it’s time to load your extension into Chrome to test it.
   - Go to `chrome://extensions`, enable "Developer mode," click on "Load unpacked," and select your project folder. The extension should appear in your list of installed extensions, and you can open it to test functionality.

#### 4. Write the Content Script
   - Create a `content.js` file that will handle image replacement on the specified website. This script will select all images on the page and replace their `src` attributes with a randomly selected URL from the user's list.

#### 5. Enable Image Replacement on Specific Sites
   - Update `manifest.json` to include the URL patterns where the extension should work, such as `*://www.ynet.co.il/*`. This ensures the content script only runs on specified domains.
   - Test the extension by visiting `www.ynet.co.il` with replacement enabled to see if the images are replaced.

#### 6. Add Storage handling for URLs 
   - Use the `chrome.storage.local` API to save the list of image URLs and the enable/disable setting.
   - Modify `popup.js` to save the list to storage whenever a new URL is added or removed, and retrieve the list when the popup is opened.

#### 7. Load the URLs from the storage to the screen
   - Add a logic that upon loading the popover script, read the URLs that are saved in the local storage and add them to the screen  

#### 8. Add an Enable/Disable Toggle
   - In the popup, add a toggle to enable or disable the image replacement feature. When toggled, update the setting in `chrome.storage` and reload the tab to reflect the change.

#### 9. Debug Your Code
   - Use Chrome DevTools to inspect, debug, and refine your code.
   - You can access DevTools by right-clicking your extension in `chrome://extensions` and selecting "Inspect popup" or by using the Console and Network tabs to view logs and network requests.

#### 10. Publish to the Chrome Web Store
   - Once your extension is working and polished, package it for the Chrome Web Store.
   - Go to the [Chrome Web Store Developer Dashboard](https://chrome.google.com/webstore/developer/dashboard), create an account, and follow the steps to publish.
   - Ensure you have a detailed description, screenshots, and icon for your extension. Once approved, users can install your extension directly from the Chrome Web Store.


By completing these steps, you’ll have created a fully functional Chrome extension that allows users to transform their browsing experience with custom images!

---

### Bonus Tasks

Once you've completed the basic steps, try adding these bonus features to enhance your extension's functionality!

1. **Add Badge to Indicate Replacement Status**
   - Display a badge on the extension icon to show if image replacement is active or inactive. Update this badge in real-time when the replacement setting is toggled.

2. **Use Random Image API**
   - Instead of relying solely on the user-provided list, integrate a random image API (like Unsplash or PlaceKitten) to retrieve images dynamically if the user's list is empty.

3. **Time-Based Replacement Toggle**
   - Add a feature to enable image replacement only during specific hours or days. This setting can be configured in the popup and saved in storage.

4. **Domain Whitelist/Blacklist**
   - Allow users to specify which sites should (or should not) have image replacement. Add fields in the popup for users to manage this list and apply the rules in the content script.

5. **Image Replacement Frequency Setting**
   - Add an option to replace images at a specific frequency (e.g., every few seconds), refreshing the images on the page based on user preferences. 

6. **Display Image Count in Badge**
   - Show the total number of URLs saved by the user in a badge on the extension icon. Update the badge count whenever the list is modified.

7. **Enable Replacement on Multiple Domains**
   - Extend the replacement functionality to work on multiple specified domains (not just `ynet.co.il`). Provide an option in the popup for users to manage the list of domains where the extension should be active.
   
8. **Persistent Notification for Active Replacement**
   - When replacement is enabled, show a notification as a reminder when the user visits a target site. This could help prevent confusion if images look unexpected due to the extension.

Try implementing one or more of these features to challenge yourself and enhance your skills!
