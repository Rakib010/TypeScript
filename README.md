## Explain the difference between any, unknown, and never types in TypeScript.

# any
any মানে: যেকোনো ধরনের মান রাখা যাবে।
any টাইপ চেকিং অফ করে দেয়, তাই TypeScript আর কোনো সতর্কতা দেয় না।
example -
```
  let anything: any = "hello";
  anything = 42; 
  anything = true; 

```

# unknown
unknown হলো TypeScript-এর একটি safe "any" টাইপ।
এই ভ্যারিয়েবলের মান কী হবে আমি এখন জানি না, পরে যাচাই করে ব্যবহার করবো।
example:
```
  const getSpeedInMeterSecond = (value: unknown) => {
  if (typeof value === "number") {
  const convertedSpeed = (value _ 1000) / 3600;
  console.log(convertedSpeed);
  } else if (typeof value === "string") {
  const [result, unit] = value.split(" ");
  const convertedSpeed = (parseFloat(result) _ 1000) /3600;
  console.log(convertedSpeed);
  } else {
  console.log("wrong input");
  }
  };
  getSpeedInMeterSecond("1000");

  ```

# Never
never টাইপ এমন একটা টাইপ, যেটা কোনো কিছুরই return করে না মানে:
এই টাইপের মান কখনো আসেই না এটি এমন function বা variable এর জন্য যেগুলো কখনো শেষ হয় না (infinite loop), বা সবসময় error করে।
```
function throwError(msg: string): never {
throw new Error(msg);
}
```
