# How to decide which mobile framework to use

## Decision flowchart

```mermaid
flowchart TD
    TargetOS["I target only one operating system"] -->|yes| Native["Native"]
    TargetOS -->|no| LimitedBudget["I have a very limited budget"]
    
    LimitedBudget -->|yes| CrossPlatformDependencies["Every dependency I will use has a cross platform implementation"]
    LimitedBudget -->|no| PerformanceTuning["I want to fine-tune my application performance"]
    
    PerformanceTuning -->|yes| CodebaseSharing["I am willing to learn an additional framework and complexify my codebase to share my domain and data layer"]
    PerformanceTuning -->|no| NativeAPIUsage["My application will use many native APIs"]
    
    CodebaseSharing -->|no| Native
    CodebaseSharing -->|yes| DeveloperSkills["Developers are willing to work with Kotlin and Android Studio"]
    
    DeveloperSkills -->|no| Native
    DeveloperSkills -->|yes| UIFrameworkSharing["I am ready to use an additional beta framework to share at least part of my user interface between the targeted operating systems"]
    
    UIFrameworkSharing -->|yes| ComposeMultiplatform["Compose Multiplatform"]
    UIFrameworkSharing -->|no| KotlinMultiplatform["Kotlin Multiplatform"]
    
    NativeAPIUsage -->|yes| CodebaseSharing
    NativeAPIUsage -->|no| LibraryReliance["I do not want to rely on community maintained libraries"]
    
    LibraryReliance -->|yes| CodebaseSharing
    LibraryReliance -->|no| OSAPIImplementation["I want to implement new operating system APIs as quickly as possible"]
    
    OSAPIImplementation -->|yes| CodebaseSharing
    OSAPIImplementation -->|no| AppResponsiveness["Application responsiveness is a competitive advantage"]
    
    AppResponsiveness -->|yes| CodebaseSharing
    AppResponsiveness -->|no| ListComplexity["The application displays many nested non standard elements in lists"]
    
    ListComplexity -->|yes| CodebaseSharing
    ListComplexity -->|no| UserExperienceOptimization["I want an operating system optimized user experience"]
    
    UserExperienceOptimization -->|no| TerminalFleetManagement["I manage my terminal fleet"]
    UserExperienceOptimization -->|yes| CodebaseSharing
    
    TerminalFleetManagement -->|no| TechnicalStackMaintenance["I want to ensure my technical stack will be maintained for the longest possible time"]
    TerminalFleetManagement -->|yes| TerminalSDKDependency["I depend on native software development kit provided by my terminals manufacturers"]
    
    TerminalSDKDependency -->|yes| CodebaseSharing
    TerminalSDKDependency -->|no| TechnicalStackMaintenance
    
    TechnicalStackMaintenance -->|yes| CodebaseSharing
    TechnicalStackMaintenance -->|no| CrossPlatformDependencies
    
    CrossPlatformDependencies -->|yes| DesignCriticality["Pixel perfect design is critical for my application"]
    CrossPlatformDependencies -->|no| NativeLibrarySkills["I have skills to develop my own native libraries"]
    
    NativeLibrarySkills -->|no| LibraryCriticality["The aforementioned libraries are critical for my application"]
    
    LibraryCriticality -->|yes| CodebaseSharing
    LibraryCriticality -->|no| DesignCriticality
    
    DesignCriticality -->|yes| Flutter["Flutter"]
    DesignCriticality -->|no| CompiledLanguagePreference["I absolutely want to work with a compiled programming language"]
    
    CompiledLanguagePreference -->|yes| Flutter
    CompiledLanguagePreference -->|no| EcosystemCapitalization["I absolutely want to capitalize on the Javascript and React ecosystem already present in my company"]
    
    EcosystemCapitalization -->|yes| ReactNative["React Native"]
    EcosystemCapitalization -->|no| DependencyUpgradeAvoidance["I want to avoid investing time in upgrading dependency clusters"]
    
    DependencyUpgradeAvoidance -->|yes| Flutter
    DependencyUpgradeAvoidance -->|no| ApplicationBootstrapping["I absolutely want to use a ready to use tool to bootstrap my application"]
    
    ApplicationBootstrapping -->|yes| ReactNative
    ApplicationBootstrapping -->|no| LearningEase["I want the cross platform framework that is easiest to become familiar with"]
    
    LearningEase -->|yes| Flutter
    LearningEase -->|no| WebEcosystemPreference["I like the web ecosystem"]
    
    WebEcosystemPreference -->|yes| ReactNative
    WebEcosystemPreference -->|no| Flutter
```

## Explanation

According to us, there are many keypoints that make crossplatform development risky.
We like native apps, and most of all we like that our clients can be autonomous when they develop.
We typically don't develop basic mobile apps without much complexity. We instead target mobile applications that may scale.

These apps require a well defined architecture and organization.
To us, we have to avoid many traps that are typically not shown when we begin mobile development :-)
