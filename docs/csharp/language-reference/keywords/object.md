---
title: "object (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0fcced75d3a86fd700e642e48b7e325e554cae53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-c-reference"></a><span data-ttu-id="cc231-102">object (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cc231-102">object (C# Reference)</span></span>
<span data-ttu-id="cc231-103">`object` Typu jest aliasem <xref:System.Object> w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc231-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="cc231-104">W systemie typów ujednoliconego C#, wszystkie typy, typy referencyjne wstępnie zdefiniowanych i zdefiniowanych przez użytkownika i typów wartości, dziedziczy pośrednio ani bezpośrednio po <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cc231-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="cc231-105">Można przypisać wartości dowolnego typu do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="cc231-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="cc231-106">Gdy zmienna typu wartości jest konwertowana na obiekt, jest określany jako *opakowany*.</span><span class="sxs-lookup"><span data-stu-id="cc231-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="cc231-107">Gdy zmienna typu obiektu jest konwertowany na typ wartości, jest określany jako *rozpakowany*.</span><span class="sxs-lookup"><span data-stu-id="cc231-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="cc231-108">Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="cc231-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc231-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc231-109">Example</span></span>  
 <span data-ttu-id="cc231-110">Następujące przykładowe pokazuje, jak zmiennych typu `object` może akceptować wartości każdego typu danych i w jaki sposób zmienne typu `object` można używać metod na <xref:System.Object> z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc231-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="cc231-111">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cc231-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cc231-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc231-112">See Also</span></span>  
 [<span data-ttu-id="cc231-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="cc231-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cc231-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cc231-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cc231-115">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cc231-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="cc231-116">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="cc231-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="cc231-117">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="cc231-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
