---
title: "#<a name=\"define-c-reference\"></a>Zdefiniuj (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#define'
helpviewer_keywords: '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae72a1b6c19421c51348a0d93691ba3fe29a191c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-reference"></a>#define (odwołanie w C#)
Możesz użyć `#define` do definiowania symbolu. Jeśli używasz symbol jako wyrażenie, które są przekazywane do [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy, wyrażenie, które będą oceniać do `true`, jak pokazano na poniższym przykładzie:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  `#define` Dyrektywy nie można użyć do zadeklarowania stałe wartości, co jest zazwyczaj wykonywane w C i C++. Stałe języka C# najlepiej są definiowane jako statyczne elementy członkowskie klasy lub struktury. Jeśli masz kilka takich stałe, należy rozważyć utworzenie oddzielnych klasę "Stałe", aby je przechowywać.  
  
 Symbole może służyć do określenia warunków dla kompilacji. Możesz przetestować dla symbolu przy użyciu jednej [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Można również użyć `conditional` atrybutu przeprowadzić kompilacji warunkowej.  
  
 Można zdefiniować symbol, ale nie można przypisać wartości do symbolu. `#define` Dyrektywa musi występować w pliku, aby korzystać z żadnych instrukcji, które nie są również dyrektywy preprocesora.  
  
 Możesz również definiować symbol [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora. Można nie zdefiniowany symbol [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Symbol, który definiuje z `/define` lub `#define` nie powoduje konfliktu z zmienna o takiej samej nazwie. To, że nazwa zmiennej nie powinien zostać przekazany do dyrektywy preprocesora i symbol będzie możliwe tylko w dyrektywie preprocesora.  
  
 Zakres symbol, który został utworzony przy użyciu `#define` jest plikiem, w którym symbol został zdefiniowany.  
  
 Jak pokazano na poniższym przykładzie, możesz umieścić `#define` dyrektywy w górnej części pliku.  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 Na przykład sposobu usuń symbol zobacz [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [Const](../../../csharp/language-reference/keywords/const.md)  
 [Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
