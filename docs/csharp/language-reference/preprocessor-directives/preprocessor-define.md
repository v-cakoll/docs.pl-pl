---
title: '#Zdefiniuj - C# odwołania'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 7be2a2d00e96b4b734e1a68f6dc63180bcbe5e82
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244976"
---
# <a name="define-c-reference"></a>#define (odwołanie w C#)
Dyrektywa `#define` umożliwia zdefiniowanie symbolu. Jeżeli używasz symbolu jako wyrażenia, które jest przekazywane do dyrektywy [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), wyrażenie zostanie oszacowane jako `true`, jak pokazano na poniższym przykładzie:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Dyrektywy `#define` nie można użyć do deklarowania wartości stałych, co jest zazwyczaj wykonywane w językach C i C++. Stałe języka C# najlepiej definiować jako statyczne elementy członkowskie klasy lub struktury. Jeśli masz kilka takich stałych, rozważ utworzenie oddzielnej klasy, aby je przechowywać.  
  
 Symbole mogą służyć do określenia warunków dla kompilacji. Można przetestować symbol przy użyciu dyrektywy [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Można również użyć <xref:System.Diagnostics.ConditionalAttribute> Aby przeprowadzić warunkową kompilację.  
  
 Symbol można zdefiniować, ale nie można do niego przypisać wartości. Dyrektywa `#define` musi występować w pliku, zanim będzie można wykonać instrukcje, które nie są również dyrektywami preprocesora.  
  
 Można również zdefiniować symbol za pomocą [— Zdefiniuj](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora. Aby anulować definicję symbolu, użyj dyrektywy [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Symbol zdefiniowany z użyciem opcji `-define` lub `#define` nie powoduje konfliktu ze zmienną o takiej samej nazwie. Oznacza to, że nazwa zmiennej nie powinna być przekazywana do dyrektywy preprocesora i symbol będzie można oszacować tylko przy użyciu tej dyrektywy.  
  
 Zakresem symbolu utworzonego przy użyciu dyrektywy `#define` jest plik, w którym został zdefiniowany symbol.  
  
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
  
 Aby zapoznać się z przykładem anulowania definicji symbolu, zobacz [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [const](../../../csharp/language-reference/keywords/const.md)  
- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
- [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
- [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
