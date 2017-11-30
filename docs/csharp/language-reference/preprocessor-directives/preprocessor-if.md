---
title: "#<a name=\"if-c-reference\"></a>Jeśli (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a>#if (odwołanie w C#)
Gdy wystąpi kompilatora C# `#if` dyrektywy, a następnie po pewnym czasie przez [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) dyrektywy, go zostanie skompilowany kod między dyrektywami tylko wtedy, gdy zdefiniowano określony symbol.  W przeciwieństwie do C i C++ nie można przypisać wartości numerycznej symbolu; wykonywanie instrukcji #if w języku C# jest wartość logiczna i tylko sprawdzenie, czy symbol został zdefiniowany lub nie. Na przykład  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 Można używać operatorów [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) (równości) [! =](../../../csharp/language-reference/operators/not-equal-operator.md) (nierówność) tylko do testowania [true](../../../csharp/language-reference/keywords/true.md) lub [false](../../../csharp/language-reference/keywords/false.md) . PRAWDA oznacza, że jest zdefiniowany symbol. Instrukcja `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`. Można używać operatorów [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) (a), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (lub) i [!](../../../csharp/language-reference/operators/logical-negation-operator.md) (nie) do oceny, czy zdefiniowano wiele symboli. Można także grupować symbole i operatory w nawiasach.  
  
## <a name="remarks"></a>Uwagi  
 `#if`, wraz z [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), i [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dyrektywy, umożliwia Dołącz lub Wyklucz kodu opartego na istnienie jednego lub więcej symboli. Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub w przypadku kompilowania kodu dla określonej konfiguracji.  
  
 Warunkowe początku dyrektywy z `#if` dyrektywa musi być jawnie zakończona z `#endif` dyrektywy.  
  
 `#define`pozwala zdefiniować symbol, taki sposób, że za pomocą symbolu jako wyrażenie przekazane do `#if` dyrektywy, wyrażenie, które będą oceniać do `true`.  
  
 Możesz również definiować symbol [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora. Można nie zdefiniowany symbol [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Symbol, który definiuje z `/define` lub `#define` nie powoduje konfliktu z zmienna o takiej samej nazwie. To, że nazwa zmiennej nie powinien zostać przekazany do dyrektywy preprocesora i symbol będzie możliwe tylko w dyrektywie preprocesora.  
  
 Zakres symbol utworzone za pomocą `#define` jest plikiem, w którym została zdefiniowana.  
  
## <a name="example"></a>Przykład  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
 **DEBUGOWANIE i test są zdefiniowane**  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
