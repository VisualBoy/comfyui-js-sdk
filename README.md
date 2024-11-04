
# ComfyUI JS SDK

This repository provides a JavaScript SDK for interacting with ComfyUI through its REST API. It allows you to control ComfyUI from external JavaScript applications, enabling you to:

- Connect to a running ComfyUI instance.
- Send prompts and trigger workflow execution.
- Monitor execution progress and retrieve results.
- Manage available workflows and nodes.

## Installation

You can install the SDK using npm:

```bash
npm install comfyui-js-sdk
```

## Usage

```javascript
const Comfy = require('comfyui-js-sdk');

const comfy = new Comfy("http://localhost:8181");

comfy.queuePrompt({
  // ... workflow definition and parameters ...
}).then(executionId => {
  console.log("Workflow started with ID:", executionId);

  // Monitor progress
  setInterval(() => {
    comfy.getProgress(executionId).then(progress => {
      console.log("Progress:", progress);
    });
  }, 1000);

  // Get output image when workflow is completed
  comfy.getOutputImage(executionId).then(image => {
    // ... do something with the image ...
  });
});
```

## API Reference

### `Comfy(apiUrl)`

Creates a new ComfyUI instance.

- `apiUrl`: The URL of the ComfyUI API.

### `getWorkflows()`

Returns a list of available workflows.

### `queuePrompt(prompt)`

Queues a prompt for execution.

- `prompt`: An object describing the workflow and input parameters.

Returns the execution ID.

### `getOutputImage(executionId)`

Retrieves the output image for a given execution ID.

### `getProgress(executionId)`

Retrieves the progress of a given execution ID.

### `cancelExecution(executionId)`

Cancels the execution of a given execution ID.

### `getNodes()`

Returns a list of available nodes.


## Contributing

Contributions are welcome! Please open an issue or submit a pull request if you have any suggestions or improvements.

## License

This project is licensed under the MIT License.

