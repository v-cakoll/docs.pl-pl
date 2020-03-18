---
title: '#define - Odwołanie do języka C#'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: c08d6f42c11184a4d14aa6712f9f0f8706a72cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173435"
---
# <a name="define-c-reference"></a>#define (odwołanie w C#)
Symbol `#define` służy do definiowania symbolu. Użycie symbolu jako wyrażenia przekazanego do [#if](./preprocessor-if.md) dyrektywy, wyrażenie `true`będzie oceniane , jak pokazano w poniższym przykładzie:  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Dyrektywy `#define` nie można użyć do deklarowania stałych wartości, jak zwykle odbywa się w C i C++. Stałe w języku C# są najlepiej zdefiniowane jako statyczne elementy członkowskie klasy lub struktury. Jeśli masz kilka takich stałych, rozważ utworzenie oddzielnej klasy "Stałe", aby je przytrzymać.  
  
 Symbole mogą służyć do określania warunków kompilacji. Możesz przetestować symbol z [#if](./preprocessor-if.md) lub [#elif](./preprocessor-elif.md). Można również użyć <xref:System.Diagnostics.ConditionalAttribute> do wykonania kompilacji warunkowej.  
  
 Można zdefiniować symbol, ale nie można przypisać wartości do symbolu. Dyrektywa `#define` musi pojawić się w pliku przed użyciem żadnych instrukcji, które nie są również dyrektywy preprocesora.  
  
 Można również zdefiniować symbol z opcją [-define](../compiler-options/define-compiler-option.md) kompilatora. Można cofnąć definicję symbolu za pomocą [#undef](./preprocessor-undef.md).  
  
 Symbol, który można `-define` zdefiniować `#define` z lub z nie kolidów ze zmienną o tej samej nazwie. Oznacza to, że nazwa zmiennej nie powinny być przekazywane do dyrektywy preprocesora i symbol może być oceniane tylko przez dyrektywy preprocesora.  
  
 Zakres symbolu, który został utworzony `#define` przy użyciu jest plik, w którym symbol został zdefiniowany.  
  
 Jak pokazano w poniższym `#define` przykładzie, należy umieścić dyrektywy w górnej części pliku.  
  
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
  
 Aby zapoznać się z przykładem jak cofnąć definicję symbolu, zobacz [#undef](./preprocessor-undef.md).  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
- [const](../keywords/const.md)
- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
