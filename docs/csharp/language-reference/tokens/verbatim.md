---
title: "@ (Odwołanie w C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b62231afc3014f9fc2b9ac7bd39168f40e12c8d
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="-c-reference"></a><span data-ttu-id="3cea7-102">@ (Odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3cea7-102">@ (C# Reference)</span></span>

<span data-ttu-id="3cea7-103">`@` Znak specjalny służy jako identyfikator dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3cea7-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="3cea7-104">Mogą być używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3cea7-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="3cea7-105">Aby włączyć słowa kluczowe języka C# ma być używany jako identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="3cea7-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="3cea7-106">`@` Znak prefiksy element kodu, które kompilator jest interpretowany jako identyfikator zamiast słowo kluczowe języka C#.</span><span class="sxs-lookup"><span data-stu-id="3cea7-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="3cea7-107">W poniższym przykładzie użyto `@` znak, aby zdefiniować identyfikator o nazwie `for` używającej w `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="3cea7-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="3cea7-108">Wskazuje, że literału ciągu jest interpretowane verbatim.</span><span class="sxs-lookup"><span data-stu-id="3cea7-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="3cea7-109">`@` Definiuje znaków w tym wystąpieniu *literał ciągu dosłownego wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="3cea7-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="3cea7-110">Sekwencje unikowe proste (takich jak `"\\"` dla ukośnik odwrotny) szesnastkową sekwencje specjalne (takie jak `"\x0041"` A wielkich i Unicode sekwencjach specjalnych, takich jak `"\u0041"` a wielkie litery, będą interpretowane jako literału.</span><span class="sxs-lookup"><span data-stu-id="3cea7-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A, and Unicode escape sequences, such as `"\u0041"` for an uppercase A, are interpreted literally.</span></span> <span data-ttu-id="3cea7-111">Tylko sekwencja specjalna oferta (`""`) nie jest interpretowany jako literału; generuje pojedynczy cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="3cea7-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="3cea7-112">W poniższym przykładzie zdefiniowano dwie ścieżki pliku identyczne, za pomocą literału ciągu regularnych, a druga za pomocą literału ciągu dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3cea7-112">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="3cea7-113">Jest to jeden z najczęściej używa literałów ciągu dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3cea7-113">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="3cea7-114">Poniższy przykład ilustruje efekt definiowania literału ciągu regularnych i zawierających sekwencje znaków identyczne literału ciągu dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3cea7-114">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="3cea7-115">Aby włączyć kompilatora odróżnić atrybutów w przypadku konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="3cea7-115">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="3cea7-116">Atrybut jest typu pochodzącego od <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="3cea7-116">An attribute is a type that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="3cea7-117">Jego nazwa typu zwykle zawiera sufiks **atrybutu**, mimo że kompilator nie wymusza tę Konwencję.</span><span class="sxs-lookup"><span data-stu-id="3cea7-117">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="3cea7-118">Ten atrybut można odwoływać w kodu przez jego pełną nazwę typu (na przykład `[InfoAttribute]` lub jego skróconą nazwę (na przykład `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="3cea7-118">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="3cea7-119">Jednak wystąpi konflikt nazw, jeśli dwa skrócony atrybutu nazwy typów są identyczne, i zawiera jedną nazwę typu **atrybutu** sufiks, ale druga nie.</span><span class="sxs-lookup"><span data-stu-id="3cea7-119">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="3cea7-120">Na przykład następujący kod nie powiedzie się skompilować kompilator nie może ustalić czy `Info` lub `InfoAttribute` atrybut jest stosowany do `Example` klasy.</span><span class="sxs-lookup"><span data-stu-id="3cea7-120">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span>

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

   <span data-ttu-id="3cea7-121">Jeśli identyfikator dosłownego wyrażenia służy do identyfikowania `Info` atrybutu przykładzie kompiluje pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3cea7-121">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a><span data-ttu-id="3cea7-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cea7-122">See Also</span></span>  
 [<span data-ttu-id="3cea7-123">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3cea7-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3cea7-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3cea7-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3cea7-125">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="3cea7-125">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
