# Bing Utils

[![AI Friendly](https://img.shields.io/badge/AI-Friendly-pink?style=for-the-badge)](https://github.com/mefengl/made-by-ai)
[![AI Assisted Maybe](https://img.shields.io/badge/AI%20Assisted-Maybe-yellow?style=for-the-badge)](https://github.com/mefengl/made-by-ai)
[![Commit Messages by AI](https://img.shields.io/badge/Commit%20Messages%20by-AI-green?style=for-the-badge)](https://github.com/mefengl/made-by-ai)

## Notice

this repo has been put into `chatkit`, you can find more about it in [chat-play/packages/chatkit/bingchat](https://github.com/mefengl/chat-play).

## Description

getSubmitButton, getTextarea, getRegenerateButton, getNewChatButton...

## Usage

just copy and paste the code below

```js
function getActionBar() {
  return document.querySelector("cib-serp")?.shadowRoot?.querySelector("cib-action-bar")?.shadowRoot;
};
```

```js
function getSubmitButton() {
  const actionBar = getActionBar();
  if (!actionBar) { return null; }
  return actionBar.querySelector('button[aria-label="Submit"]');
};
```

```js
function getTextarea() {
  const actionBar = getActionBar();
  if (!actionBar) { return null; }
  return actionBar.querySelector('textarea');
};
```

```js
function getStopGeneratingButton() {
  const actionBar = getActionBar();
  if (!actionBar) { return null; }
  const stopGeneratingButton = actionBar.querySelector('cib-typing-indicator')?.shadowRoot?.querySelector('button[aria-label="Stop Responding"]');
  if (!stopGeneratingButton) { return null; }
  if (stopGeneratingButton.disabled) { return null; }
  return stopGeneratingButton;
};
```

```js
function getNewChatButton() {
  const actionBar = getActionBar();
  if (!actionBar) { return null; }
  return actionBar.querySelector('button[aria-label="New topic"]');
};
```

```js
function getConversation() {
  return document.querySelector("cib-serp")?.shadowRoot?.querySelector("cib-conversation")?.shadowRoot;
};
```

```js
function getChatTurns() {
  const conversation = getConversation();
  if (!conversation) { return null; }
  return Array.from(conversation.querySelectorAll('cib-chat-turn')).map(t => t.shadowRoot);
};
```

```js
function getLastChatTurn() {
  const chatTurns = getChatTurns();
  if (!chatTurns) { return null; }
  return chatTurns[chatTurns.length - 1];
};
```

```js
function getLastResponse() {
  const lastChatTurn = getLastChatTurn();
  if (!lastChatTurn) { return null; }
  return lastChatTurn.querySelectorAll('cib-message-group')[1]?.shadowRoot;
};
```

```js
function getLastResponseText() {
  const lastResponse = getLastResponse();
  if (!lastResponse) { return null; }
  return Array.from( lastResponse.querySelectorAll('cib-message') )
    .map(m => m.shadowRoot)
    .find(m => m.querySelector('cib-shared'))
    .textContent.trim();
};
```

```js
function send(text) {
  const textarea = getTextarea();
  if (!textarea) { return null; }
  textarea.value = text;
  textarea.dispatchEvent(new Event('input'));
  const submitButton = getSubmitButton();
  if (!submitButton) { return null; }
  submitButton.click();
};
```

## Contributing

Contributions, issues and feature requests are welcome!

## License

This project is licensed under the terms of the [MIT license](/LICENSE).
