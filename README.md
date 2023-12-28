# 🚀 Multithreading with Shared Memory in PHP
## _🛠️ Efficient Threading & Memory Management for PHP Applications_

![Build Status](https://img.shields.io/badge/build-passing-brightgreen) ![PHP Version](https://img.shields.io/badge/php-^8.4-blue) 

🤔 Facing threading challenges in PHP? Let's tackle them together! My journey in developing a function for complex computations in PHP revealed several threading hurdles. These issues, such as deadlocks and inefficient I/O executions, often hampered performance. To combat this, I've innovated a PHP threading solution utilizing shared memory, aimed at speedy and effective data handling.

- 🧵 Implement multithreading in PHP
- 💾 Utilize shared memory for top-notch data access
- 🛡️ Sidestep common deadlocks and boost performance
- ✨ Craft a Robust & Scalable solution ✨

## 📖 Solution Overview

Unlock threading prowess with the `Threads` class in the `NameSpaceThreads` namespace. This gem works alongside the `SharedMemoryHandler` for slick inter-process communication. Expect quicker data access and smooth management of concurrent tasks. 

### 🌟 Key Features

- **🔄 Efficient Process Management**: Dynamically juggles multiple processes.
- **💽 Shared Memory**: Harnesses shared memory for swift data access. Dealing with loads of data? Modify `$default_size = 1000000;` to your needs, but watch out for resource Ops! 🚨
- **📊 Dynamic Task Allocation**: Smartly assigns tasks to threads, balancing the load. Imagine running 30 processes with the system intelligently distributing tasks to avoid overloading.
- **⚙️ Concurrency Control**: I've adopted a savvy concurrency control strategy using `fork()`. This approach clones data, facilitating simultaneous thread execution sans inter-thread chatter. The result? Blazing-fast, streamlined processing with jaw-dropping outcomes.
- **🛠️ Resource Management**: Keeps a tight rein on resources to prevent leaks. As well as proper handling of pid termination.

### 🔫 Error Handling
- **⛔ Thread Collapse**: Despite the fact that threads may occasionally drop out of execution due to various reasons such as buggy functions and resource constraints, the threads operate independently of one another and continue to perform their assigned tasks with no communication between them.

## 📲 Installation and Usage

Make sure PHP is up and running with `pcntl` and `posix` extensions on board.

```sh
git clone git@github.com:cuthbert-lwinga/php-threading.git
```
## 🖥️ How to Use

To harness the power of multithreading in PHP with this library, follow these simple steps:

### Include the Files

Ensure that you include the necessary library files in your Php.

```php
include_once("SharedMemoryHandler.php");
include_once("Threads.php");
use NameSpaceThreads\Threads;
```

## 🌐 Define Your Threaded Function

Create a function that you want to execute in parallel. Make sure it accepts parameters as an array. Here's an example function:

```php
function testbackground($param = 1) {
    sleep(1);

    if ($param % 1000 == 0) {
        echo "\n $param EXECUTED\n";
    }
}
```

## 📑 Add Tasks

Use the Threads::addTask method to add tasks to the queue. Pass your function name and parameters as an array to this method. For example:

```php
for ($i = 0; $i < 7200; $i++) {
    Threads::addTask("testbackground", [$i]);
}

```

## Run Threads

Finally, start the threads using the Threads::run method. Specify the number of threads you want to run concurrently as an argument. For example, to run 800 threads simultaneously

```php
Threads::run($Threads = 800);
```

With these simple steps, you can efficiently utilize multithreading in PHP to boost performance and handle concurrent tasks effectively. 🚀
