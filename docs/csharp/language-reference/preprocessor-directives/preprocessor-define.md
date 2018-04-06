---
title: "#Zdefiniuj (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae72a1b6c19421c51348a0d93691ba3fe29a191c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-reference"></a>#define (odwołanie w C#)
Możesz użyć `#define` do definiowania symbolu. Jeżeli używasz symbolu jako wyrażenie, które jest przekazywane do dyrektywy [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), wyrażenie zostanie ocenione jako `true`, jak pokazano na poniższym przykładzie:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  `#define` Dyrektywy nie można użyć do zadeklarowania stałej wartości, co jest zazwyczaj wykonywane w C i C++. Stałe języka C# najlepiej są definiowane jako statyczne elementy członkowskie klasy lub struktury. Jeśli masz kilka takich stałych, należy rozważyć utworzenie oddzielnej klasy, aby je przechowywać.  
  
 Symbole mogą służyć do określenia warunków dla kompilacji. Możesz przetestować symbol przy użyciu [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Można również użyć atrybut `conditional`, aby przeprowadzić kompilację warunkową.  
  
 Symbol mozna zdefiniować, ale nie można do niego przypisać wartości. Dyrektywa  `#define` musi występować w pliku zanim skkorzystasz z innych instrukcji, które nie są również dyrektywami preprocesora.  
  
 Możesz również definiować symbol przy pomocy opcji kompilatora [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). Można cofnąć definicję symbolu przy pomocy [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Symbol, zdefiniowany przez `/define` lub `#define` nie powoduje konfliktu ze zmienną o takiej samej nazwie. To znaczy, że nazwa zmiennej nie powinien zostać przekazana do dyrektywy preprocesora i symbol będzie możliwy do obliczenia tylko w dyrektywie preprocesora.  
  
 Zakresem symbolu, który został utworzony przy użyciu `#define` jest plik, w którym został zdefiniowany.  
  
 Jak pokazano na poniższym przykładzie, musisz umieścić dyrektywy `#define` w górnej części pliku.  
  
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
  
 Jeżeli chcesz zapoznać się z przykładem cofania definicji symbolu, zobacz [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [Const](../../../csharp/language-reference/keywords/const.md)  
 [Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
