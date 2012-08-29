node-printer
============

A tool to print document or data. Based on "lp" binary.

## Quick Examples

```js
var printer = require ("./src/printer");
var options = {
    destination: "EPSON_SX510",
};

var text = "package.json";
var file = "package.json";

var jobText = printer.printText(text, options, "text_demo");
var jobFile = printer.printFile(file, options, "file_demo");

var onJobEnd = function () {
    console.log(this.identifier + ", job finish");
};

var onJobError = function (message) {
    console.log(this.identifier + ", error: " + message);
};

jobText.on("end", onJobEnd);
jobText.on("error", onJobError);

jobFile.on("end", onJobEnd);
jobFile.on("error", onJobError);
```