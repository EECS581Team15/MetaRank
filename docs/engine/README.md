MetaRank Engine
===============

## Overview

The MetaRank Engine generates specifications and interpreters for random programming languages. In addition, it provides input validation for user-written programs.


```plantuml
@startuml
actor UI
database LanguageCache

group Generation
UI->LanguageGen: Generation Request
LanguageGen->LanguageCache: Language Definition
LanguageGen<-LanguageCache: Language Id
UI<-LanguageGen: Language Id
end

group Documentation
UI->DocBuilder: Language Id
UI<-DocBuilder: Language Documentation
end

group Evaluation
UI->LanguageCache: Language Id
UI<-LanguageCache: Language Definition
UI->Parser: (Raw Program, \nLanguage Definition)
Parser->Sanitizer: (AST, \nLanguage\nDefinition)
Sanitizer->Elaborator: (Sanitized AST,\nLanguage\nDefinition)
Elaborator->Interpreter: Core\nProgram
UI<-Interpreter: Program Result
end
@enduml
```

## Components

* [LanguageCache](./LanguageCache.md)
* [LanguageGen](./LanguageGen.md)
* [DocBuilder](./DocBuilder.md)
* [Parser](./Parser.md)
* [Sanitizer](./Sanitizer.md)
* [Elaborator](./Elaborator.md)
* [Interpreter](./Interpreter.md)

## Data Types

* [Language Definition](./LanguageDefinition.md)
* [Full AST](./FullAST.md)
* [Core AST](./CoreAST.md)