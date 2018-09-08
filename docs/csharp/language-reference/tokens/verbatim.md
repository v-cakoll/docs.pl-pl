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
ms.openlocfilehash: 7dbab5a743b4f9fed759210e8410cd6e3459efac
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214631"
---
# <a name="-c-reference"></a>@ (Odwołanie w C#)

`@` Znak specjalny służy jako identyfikator dosłownego wyrażenia. Mogą być używane w następujący sposób:

1. Aby włączyć słowa kluczowe języka C#, aby można używać jako identyfikatorów. `@` Znak prefiksy element kodu, który kompilator ma interpretować jako identyfikator zamiast słowa kluczowego języka C#. W poniższym przykładzie użyto `@` znak definiują identyfikatora o nazwie `for` używającej w `for` pętli.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Aby wskazać, że literał ciągu ma być interpretowany dosłownie. `@` Definiuje znak, w tym wystąpieniu *verbatim literału ciągu*. Proste sekwencje ucieczki (takich jak `"\\"` dla ukośnik odwrotny) szesnastkową sekwencje unikowe (takich jak `"\x0041"` a wielkie litery) i sekwencje unikowe Unicode (takich jak `"\u0041"` wielkie litery a) jest interpretowany dosłownie. Tylko sekwencja unikowa oferty (`""`) nie jest interpretowany dosłownie; generuje pojedynczy znak cudzysłowu. Ponadto w przypadku verbatim [ciągiem interpolowanym](interpolated.md) sekwencje unikowe nawiasu klamrowego (`{{` i `}}`) nie jest interpretowany dosłownie; produkują znaki pojedynczy nawias klamrowy. W poniższym przykładzie zdefiniowano dwie ścieżki identyczny plik za pomocą literału ciągu regularnych, a druga za pomocą literału ciągu verbatim. Jest to jedna z bardziej powszechne zastosowania verbatim literałów.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Poniższy przykład ilustruje efekt Definiowanie regularne literału ciągu i ciąg verbatim literał, która zawiera sekwencje znaków identyczne.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Aby umożliwić kompilatorowi rozróżnienie między atrybutami w przypadku konfliktu nazw. Atrybut jest typu, która pochodzi od klasy <xref:System.Attribute>. Nazwa jej typu obejmują zazwyczaj sufiks **atrybutu**, mimo że kompilator nie wymusza tę Konwencję. Ten atrybut może odwoływać w kodzie przez jego pełna nazwa typu (na przykład `[InfoAttribute]` lub jego skróconą nazwę (na przykład `[Info]`). Jednak konflikt nazw występuje, jeśli dwa skrócone nazwy typu atrybutu są identyczne, i zawiera jedną nazwę typu **atrybut** sufiks, ale innych nie. Na przykład, poniższy kod nie zostanie skompilowany, ponieważ kompilator nie może określić czy `Info` lub `InfoAttribute` atrybut jest stosowany do `Example` klasy.

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

   Jeśli identyfikator dosłownego wyrażenia jest używany do identyfikowania `Info` atrybutu przykład pomyślnie wykonuje kompilację.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Znaki specjalne języka C#](../../../csharp/language-reference/tokens/index.md)
