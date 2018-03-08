# node-mail-template-helper

`node-mail-template-helper` is a helper module to assist with compilation of email templates.

# [Installation](#installation)
<a name="installation"></a>

```shell
npm install @dealerslink/node-mail-template-helper
```

# [Usage](#usage)
<a name="usage"></a>

```js
const MailTemplatesHelper = require('@dealerslink/node-mail-template-helper');

const templates = {
  ['Test2']: {
    subject: '{testData1} {testData2}',
    template: '{bodyData} - {testData2} -- {embedded.value}'
  }
};

const mailTemplateHelper = new MailTemplatesHelper(templates);
```

See wiki for more details.
