# Migration Guide: From Gradle Groovy to Kotlin DSL - Android

**Android** configuration files have used **Gradle Groovy** since the beginning, but in recent years with the appearance of **Kotlin**, these files can be written taking advantage of the full power of this language.

Therefore, **Gradle** has decided to support **Kotlin** for these configuration files using the **Kotlin DSL** variant.

Here are the changes you need to migrate from Groovy to Kotlin easily:

## Build Gradle file (:app)

### Adapt dependencies in build.gradle

*   Replace all single quotation marks (' ') by double quotation marks (" ")
    
*   You must indicate parentheses where there are function calls.
    

%[https://gist.github.com/figonzal1/e53d9490700368ec45eb91be0d7d80ff] 

### Adapt plugins inside the files

*   The plugins will now go inside a `plugins` function together with the `id` function
    

%[https://gist.github.com/figonzal1/aedb5ae3646804c4d7f509b1b18fbf28] 

### Build types configuration

*   Now the *buildTypes* must be defined with the function `getByName`
    
*   Verify that the property values are now assigned with an `=`
    

%[https://gist.github.com/figonzal1/ef568988ba0a2de0c6b2c597d83b07ac] 

### Defaults Configs

*   Package configurations, SDK and version names have minor changes
    

%[https://gist.github.com/figonzal1/15fe6d40d33220f2f9d0f3221aa1d5b9] 

## Build Gradle file (MyApp)

### Adapt classpath dependencies

*   Again note double quotation marks and the use of parentheses.
    

%[https://gist.github.com/figonzal1/053f722e3df25cf0f7cddf7d87b11dd1] 

### Changes in Task Clean function

%[https://gist.github.com/figonzal1/88aa881fd67bab57445fab2d5736ba7b] 

### Adapt Settings.gradle

The settings.gradle file should be written in the following way

%[https://gist.github.com/figonzal1/8d4e2051c6352aa5e55337329b3d8cfb] 

### Finally, change the extension in all files

You must add to each file the extension `.kts` , the files would look like this:

*   app/build.gradle.kts
    
*   build.gradle.kts
    
*   settings.gradle.kts
    

It's as simple as that!

## BONUS ZONE

### Load information from `keystore`

To generate the `release` signature using the Keystore file you can load the variables in the following way

%[https://gist.github.com/figonzal1/ac05b1c66fd406f51fa0add691630172] 

### Load variables from `local.properties` and exclude library within a dependency

If you have any properties that you need to load from the local file or you need to exclude some library inside of a dependency, you can do it in the following way

%[https://gist.github.com/figonzal1/f6ddb3d46cb76969ce7161a2a2a442d8] 

That's all for today, I hope your migration to Kotlin will be made easier with this article ❤.

If you liked the article, feel free to give a thumbs up. You will motivate me to write more articles like this one. Thanks!