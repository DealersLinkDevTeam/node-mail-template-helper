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

console.log(mailTemplateHelper.getFilledTemplate('Test2', {
  testData1: 'a',
  testData2: 'b',
  bodyData: 'test',
  embedded: {
    value: 'qwerty'
  }
}));
```

# [API Reference](#api)
<a name="api"></a>

## MailTemplatesHelper constructor(templates) ⇒ instanceof MailTemplatesHelper
Create an instance of MailTemplatesHelper with the `templates` collection provided.

## MailTemplatesHelper.getTemplate(templateName) ⇒ object(mail template) / null
Returns the template with the `templateName` provided or `null` if the template does not exist

## MailTemplatesHelper.getFilledSubject(templateName, data) ⇒ string / null
Returns the template subject from the `templateName` provided, using the `data` to fill any `{}` placeholders, or `null` if no template by that name exists.

## MailTemplatesHelper.getFilledBody(templateName, data) ⇒ string / null
Returns the template body from the `templateName` provided, using the `data` to fill any `{}` placeholders, or `null` if no template by that name exists.

## MailTemplatesHelper.getCustomFilled(template, data) ⇒ string / null
Returns custom `template` filled using the `data` to fill any `{}` placeholders, or `null` if the `template` is `null` or `undefined`

# [Templates and Collections](#templates)
<a name="templates"></a>

## Template
A template is just a string with `{}` placeholders for data in data dictionary. The placeholders can reference nested data objects and array indices.

```js
const template = 'This is a template with { data }. Hello { name }.';
```

## Mail Template
A mail template is an object which contains two template strings labelled `body` and `subject`.

```js
const mailTemplate = {
  subject: 'Mail Subject -- { data1 }',
  body: 'This is a template with { data }. Hello { name }.'
};
```

## Template Collection
A template collection is an object with named indices which each contain a Mail Template.

```js
const templates = {
  ['Test1']: {
    subject: 'Mail Subject -- { data1 }',
    body: 'This is a template with { data }. Hello { name }.'
  },
  ['Test2']: {
    subject: 'Mail Subject -- { data1 }',
    body: 'This is a template with { data }. Hello { name }.'
  }
};
```
