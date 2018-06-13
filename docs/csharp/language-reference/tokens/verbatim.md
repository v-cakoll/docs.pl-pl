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
# <a name="-c-reference"></a><span data-ttu-id="886b6-102">@ (Odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="886b6-102">@ (C# Reference)</span></span>

<span data-ttu-id="886b6-103">`@` Znak specjalny służy jako identyfikator dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="886b6-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="886b6-104">Mogą być używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="886b6-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="886b6-105">Aby włączyć słowa kluczowe języka C# ma być używany jako identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="886b6-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="886b6-106">`@` Znak prefiksy element kodu, które kompilator jest interpretowany jako identyfikator zamiast słowo kluczowe języka C#.</span><span class="sxs-lookup"><span data-stu-id="886b6-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="886b6-107">W poniższym przykładzie użyto `@` znak, aby zdefiniować identyfikator o nazwie `for` używającej w `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="886b6-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="886b6-108">Wskazuje, że literału ciągu jest interpretowane verbatim.</span><span class="sxs-lookup"><span data-stu-id="886b6-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="886b6-109">`@` Definiuje znaków w tym wystąpieniu *literał ciągu dosłownego wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="886b6-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="886b6-110">Sekwencje unikowe proste (takich jak `"\\"` dla ukośnik odwrotny) szesnastkową sekwencje specjalne (takie jak `"\x0041"` a wielkie litery) i sekwencje specjalne Unicode (takich jak `"\u0041"` a wielkie litery) będą interpretowane jako literału.</span><span class="sxs-lookup"><span data-stu-id="886b6-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="886b6-111">Tylko sekwencja specjalna oferta (`""`) nie jest interpretowany jako literału; generuje pojedynczy cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="886b6-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="886b6-112">Ponadto w przypadku dosłownego wyrażenia [interpolowane ciąg](interpolated.md) nawiasu klamrowego sekwencje specjalne (`{{` i `}}`) nie będą interpretowane jako literału; wygenerowanie nawiasu klamrowego pojedynczy znaki.</span><span class="sxs-lookup"><span data-stu-id="886b6-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="886b6-113">W poniższym przykładzie zdefiniowano dwie ścieżki pliku identyczne, za pomocą literału ciągu regularnych, a druga za pomocą literału ciągu dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="886b6-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="886b6-114">Jest to jeden z najczęściej używa literałów ciągu dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="886b6-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="886b6-115">Poniższy przykład ilustruje efekt definiowania literału ciągu regularnych i zawierających sekwencje znaków identyczne literału ciągu dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="886b6-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="886b6-116">Aby włączyć kompilatora odróżnić atrybutów w przypadku konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="886b6-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="886b6-117">Atrybut jest typu pochodzącego od <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="886b6-117">An attribute is a type that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="886b6-118">Jego nazwa typu zwykle zawiera sufiks **atrybutu**, mimo że kompilator nie wymusza tę Konwencję.</span><span class="sxs-lookup"><span data-stu-id="886b6-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="886b6-119">Ten atrybut można odwoływać w kodu przez jego pełną nazwę typu (na przykład `[InfoAttribute]` lub jego skróconą nazwę (na przykład `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="886b6-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="886b6-120">Jednak wystąpi konflikt nazw, jeśli dwa skrócony atrybutu nazwy typów są identyczne, i zawiera jedną nazwę typu **atrybutu** sufiks, ale druga nie.</span><span class="sxs-lookup"><span data-stu-id="886b6-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="886b6-121">Na przykład następujący kod nie powiedzie się skompilować kompilator nie może ustalić czy `Info` lub `InfoAttribute` atrybut jest stosowany do `Example` klasy.</span><span class="sxs-lookup"><span data-stu-id="886b6-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span>

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

   <span data-ttu-id="886b6-122">Jeśli identyfikator dosłownego wyrażenia służy do identyfikowania `Info` atrybutu przykładzie kompiluje pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="886b6-122">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a><span data-ttu-id="886b6-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="886b6-123">See Also</span></span>  
 [<span data-ttu-id="886b6-124">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="886b6-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="886b6-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="886b6-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="886b6-126">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="886b6-126">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
