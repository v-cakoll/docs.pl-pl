---
title: object (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199254"
---
# <a name="object-c-reference"></a><span data-ttu-id="947e2-102">object (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="947e2-102">object (C# Reference)</span></span>
<span data-ttu-id="947e2-103">`object` Typu jest aliasem dla <xref:System.Object> w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="947e2-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="947e2-104">W systemie zunifikowany typ w języku C#, wszystkie typy, wstępnie zdefiniowanych i zdefiniowanych przez użytkownika typy odwołań i typy wartości dziedziczyć bezpośrednio lub pośrednio <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="947e2-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="947e2-105">Można przypisać wartości dowolnego typu do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="947e2-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="947e2-106">Kiedy zmienną typu wartości jest konwertowany na obiekt, jest określany jako *opakowany*.</span><span class="sxs-lookup"><span data-stu-id="947e2-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="947e2-107">Zmienną obiektu typu jest konwertowany na typ wartości, jest określane jako *rozpakowany*.</span><span class="sxs-lookup"><span data-stu-id="947e2-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="947e2-108">Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="947e2-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="947e2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="947e2-109">Example</span></span>  
 <span data-ttu-id="947e2-110">Następujące przykładowe pokazuje, jak zmienne typu `object` może akceptować wartości dowolnego typu danych i w jaki sposób zmienne typu `object` można użyć metod na <xref:System.Object> z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="947e2-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="947e2-111">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="947e2-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="947e2-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="947e2-112">See Also</span></span>  
 [<span data-ttu-id="947e2-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="947e2-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="947e2-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="947e2-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="947e2-115">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="947e2-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="947e2-116">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="947e2-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="947e2-117">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="947e2-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
