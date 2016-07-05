# Cocos-2dx

# 1. Installation [^1]

Item: `Cocos-2dx 3.9`, `Visual Studio 2013 Ultimate`, `Python 2.7`

Step 1: Download and install items

Step 2: Add `environment variables`

```
export COCOS_CONSOLE_ROOT=cocos2d-x-3.9\tools\cocos2d-console\bin
export COCOS_TEMPLATES_ROOT=cocos2d-x-3.9\templates
```

Step 3: Install Cocos-2dx

```
cd cocos2d-x-3.9
python setup.py
```


# 2. Hello World [^2]

## 2.1 Create `hello world` project

```
cocos new MyGame -p com.MyCompany.MyGame -l cpp -d ~/MyCompany
```

> Be Patience! It takes me 2 minutes

## 2.2 Run project

```
cocos run -s ~/MyCompany/MyGame -p ios
```

> Be Patience! It takes me 5 minutes

## 3. Physic Engines: Box2D

[Cocos2d-x C++ Physics Tutorial 1 - What Is A Physics Engine?, Sonar Systems](https://www.youtube.com/watch?v=C1sAi_YTZHk&list=PLRtjMdoYXLf4dOgNrnQCw1DyIFGUhnVtZ)

## 4. Graphics and Sounds

http://kenney.nl/assets

## Texture Packer

[^1]: [cocos2d-x.org, PreRequisites](http://www.cocos2d-x.org/wiki/Prerequisites)
[^2]: [cocos2d-x.org, CREATING A NEW EXAMPLE PROJECT](http://www.cocos2d-x.org/wiki/Creating_A_New_Example_Project)