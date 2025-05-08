## Explain the difference between any, unknown, and never types in TypeScript.

- any মানে: যেকোনো ধরনের মান রাখা যাবে। any টাইপ চেকিং অফ করে দেয়, তাই TypeScript আর কোনো সতর্কতা দেয় না।
example -
```
  let anything: any = "hello";
  anything = 42; 
  anything = true; 

  anything.toUpperCase(); // এটি ভুল হলেও TypeScript কিছু বলবে না

```

- unknown হলো TypeScript-এর একটি safe "any" টাইপ।
এই ভ্যারিয়েবলের মান কী হবে আমি এখন জানি না, পরে যাচাই করে ব্যবহার করবো।
example:
```
 let uncertain: unknown = "hello";

// correct code 
if (typeof uncertain === "string") {
    uncertain.toUpperCase(); 
}

// wrong code 
let uncertain: unknown = "hello";
uncertain.toUpperCase(); // টাইপ চেক ছাড়াই সরাসরি ব্যবহার করা যাচ্ছে না

  ```

- never টাইপ এমন একটা টাইপ, যেটা কোনো কিছুরই return করে না মানে: এই টাইপের মান কখনো আসেই না এটি এমন function বা variable এর জন্য যেগুলো কখনো শেষ হয় না (infinite loop), বা সবসময় error করে।
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

## How does TypeScript help in improving code quality and project maintainability?

- TypeScript হলো JavaScript-এর উপরে নির্মিত একটি স্ট্যাটিক টাইপড সুপারসেট, যা JavaScript-এর সমস্ত ফিচার তো দেয়ই, তার সঙ্গে টাইপ সেফটির সুবিধাও দেয়। এটি বড় প্রজেক্টে কাজ করার সময় কোডকে আরও  পরিষ্কার ও মেইনটেনযোগ্য করে তোলে

1. Static Typing
- TypeScript কম্পাইল করার আগেই বলে দেয় আপনার কোডে কোন টাইপের ভুল আছে।
- টাইপ চেকিংয়ের কারণে ভুলগুলো ডেভেলপমেন্ট টাইমেই ধরা পড়ে, প্রোডাকশনে যাওয়ার আগে ঠিক করা যায়।
 ``` 
 function add(a: number, b: number): number {
  return a + b;
}
//  টাইপ এরর: string দেওয়া যাবে না
add("10", 20);

```
2. Auto-completion and intelligence
- TypeScript তে অটো সাজেশন দেয়, ফাংশনের প্যারামিটার কী কী লাগবে, কোন প্রপার্টিগুলো অ্যাভেইলেবল — সবই দেখায়।
- ভুল কম হয় | কোড লেখা দ্রুত হয় | নতুন ডেভেলপারও সহজে বুঝতে পারে কী করতে হবে

3. Improved documentation
- টাইপ গুলোর মাধ্যমে আপনার ফাংশনের ইনপুট ও আউটপুট সম্পর্কে আগে থেকেই ধারণা পাওয়া যায়।
```
type User = {
  name: string;
  age: number;
};

function greet(user: User): string {
  return `Hello, ${user.name}`;
}
 ``` 
4. Code Safety and Bug Prevention
 - JavaScript-এর সবচেয়ে বড় সমস্যা হলো টাইপ সংক্রান্ত বাগ। TypeScript এসব বাগ অনেক আগেই ধরিয়ে দেয়, তাই প্রোডাকশনে সমস্যা কম হয়।

