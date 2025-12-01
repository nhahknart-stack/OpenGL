# OpenGLApp

This is an OpenGL project written in C++ using GLFW, GLAD, and CMake.

---

## 🚀 Requirements

* CMake ≥ 3.10
* A C/C++ compiler (MinGW or MSVC recommended)
* GLFW (`glfw3.dll` must be located in the `bin/` folder)
* GLAD (included in the source)

---

## 📁 Project Structure

```
OpenGLApp/
│── src/
│     ├── main.cpp
│     ├── glad.c
│     └── ...
│── include/
│     ├── glad/glad.h
│     ├── GLFW/glfw3.h
│── bin/
│     └── glfw3.dll      # Only this file is pushed to GitHub
│── CMakeLists.txt
│── README.md
```

---

## 🛠 Building the Project

### **Windows (MinGW)**

```powershell
mkdir build
cd build
cmake -G "MinGW Makefiles" ..
mingw32-make
```

### **Windows (MSVC)**

```powershell
mkdir build
cd build
cmake ..
cmake --build .
```

---

## ▶ Running the Application

After building, the executable will be located at:

```
build/OpenGLApp.exe
```

If you encounter a `missing glfw3.dll` error, make sure:

* `glfw3.dll` is in the same folder as the executable, or
* The `bin` folder is added to your **PATH** environment variable

---

## 📌 Notes

* The `build/` folder is ignored and not pushed to GitHub.
* Only the `glfw3.dll` library in `bin/` is pushed to allow the project to run easily.
