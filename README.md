## Explain the difference between any, unknown, and never types in TypeScript.

- any
any মানে: যেকোনো ধরনের মান রাখা যাবে। any টাইপ চেকিং অফ করে দেয়, তাই TypeScript আর কোনো সতর্কতা দেয় না।
example -
```
  let anything: any = "hello";
  anything = 42; 
  anything = true; 

  anything.toUpperCase(); // এটি ভুল হলেও TypeScript কিছু বলবে না

```

- unknown
unknown হলো TypeScript-এর একটি safe "any" টাইপ।
এই ভ্যারিয়েবলের মান কী হবে আমি এখন জানি না, পরে যাচাই করে ব্যবহার করবো।
example:
```
 let uncertain: unknown = "hello";

// correct code 
if (typeof uncertain === "string") {
    uncertain.toUpperCase(); 
}

let uncertain: unknown = "hello";
uncertain.toUpperCase(); // টাইপ চেক ছাড়াই সরাসরি ব্যবহার করা যাচ্ছে না

  ```

-Never
never টাইপ এমন একটা টাইপ, যেটা কোনো কিছুরই return করে না মানে: এই টাইপের মান কখনো আসেই না এটি এমন function বা variable এর জন্য যেগুলো কখনো শেষ হয় না (infinite loop), বা সবসময় error করে।
```
function error(message: string): never {
    throw new Error(message);
}
function infiniteLoop(): never {
    while (true) {}
}
// never টাইপ, কারণ একই সাথে string এবং number হওয়া অসম্ভব
type StringAndNumber = string & number;`
```

## 