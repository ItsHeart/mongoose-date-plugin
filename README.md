# mongoose-date-plugin

### INSTALL
```
npm install mongoose-date-plugin --save
```

### USE

#### 1. define schema:
```
'use strict';

module.exports = app => {
  const mongoose = app.mongoose;

  const UserSchema = new mongoose.Schema({
    username: { type: String, required: true },
    birthdate: { type: Date, default: new Date() },
    ...
  });

  return mongoose.model('User', UserSchema);
};

```
#### 2. added plugin:
```
'use strict';

const mongooseDatePlugin = require('mongoose-date-plugin');

module.exports = app => {
  const mongoose = app.mongoose;

  const UserSchema = new mongoose.Schema({
    username: { type: String, required: true },
    birthdate: { type: Date,  format: "YYYY-MM-DD" },
    ...
  });
  
  UserSchema.plugin(mongooseDatePlugin);  // format: YYYY-MM-DD
  return mongoose.model('User', UserSchema);
};
```


#### 3. response format:
```
{
  username: 'test',
  birthdate: '2018-02-12',
  ...
}
```
more format looking for at [moment](https://github.com/moment/moment)