---
title: '@ (Odwołanie w C#)'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdf8735894594acab31586e539f90e426db97f24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289181"
---
# <a name="-c-reference"></a>@ (Odwołanie w C#)

`@` Znak specjalny służy jako identyfikator dosłownego wyrażenia. Mogą być używane w następujący sposób:

1. Aby włączyć słowa kluczowe języka C# ma być używany jako identyfikatory. `@` Znak prefiksy element kodu, które kompilator jest interpretowany jako identyfikator zamiast słowo kluczowe języka C#. W poniższym przykładzie użyto `@` znak, aby zdefiniować identyfikator o nazwie `for` używającej w `for` pętli.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Wskazuje, że literału ciągu jest interpretowane verbatim. `@` Definiuje znaków w tym wystąpieniu *literał ciągu dosłownego wyrażenia*. Sekwencje unikowe proste (takich jak `"\\"` dla ukośnik odwrotny) szesnastkową sekwencje specjalne (takie jak `"\x0041"` a wielkie litery) i sekwencje specjalne Unicode (takich jak `"\u0041"` a wielkie litery) będą interpretowane jako literału. Tylko sekwencja specjalna oferta (`""`) nie jest interpretowany jako literału; generuje pojedynczy cudzysłów. Ponadto w przypadku dosłownego wyrażenia [interpolowane ciąg](interpolated.md) nawiasu klamrowego sekwencje specjalne (`{{` i `}}`) nie będą interpretowane jako literału; wygenerowanie nawiasu klamrowego pojedynczy znaki. W poniższym przykładzie zdefiniowano dwie ścieżki pliku identyczne, za pomocą literału ciągu regularnych, a druga za pomocą literału ciągu dosłownego wyrażenia. Jest to jeden z najczęściej używa literałów ciągu dosłownego wyrażenia.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Poniższy przykład ilustruje efekt definiowania literału ciągu regularnych i zawierających sekwencje znaków identyczne literału ciągu dosłownego wyrażenia.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby włączyć kompilatora odróżnić atrybutów w przypadku konfliktu nazw. Atrybut jest typu pochodzącego od <xref:System.Attribute>. Jego nazwa typu zwykle zawiera sufiks **atrybutu**, mimo że kompilator nie wymusza tę Konwencję. Ten atrybut można odwoływać w kodu przez jego pełną nazwę typu (na przykład `[InfoAttribute]` lub jego skróconą nazwę (na przykład `[Info]`). Jednak wystąpi konflikt nazw, jeśli dwa skrócony atrybutu nazwy typów są identyczne, i zawiera jedną nazwę typu **atrybutu** sufiks, ale druga nie. Na przykład następujący kod nie powiedzie się skompilować kompilator nie może ustalić czy `Info` lub `InfoAttribute` atrybut jest stosowany do `Example` klasy.

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   Jeśli identyfikator dosłownego wyrażenia służy do identyfikowania `Info` atrybutu przykładzie kompiluje pomyślnie.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Znaki specjalne języka C#](../../../csharp/language-reference/tokens/index.md)
