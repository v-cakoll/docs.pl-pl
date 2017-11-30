---
title: "Niejawnie wpisane tablice (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6e60ff600a04dab47e8b0ed52dda00441e17f25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="0a28e-102">Niejawnie wpisane tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0a28e-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="0a28e-103">Niejawnie wpisane tablicy, w którym jest wywnioskowany Typ wystąpienia tablicy można utworzyć z elementów wymienionych w inicjatorze tablicy.</span><span class="sxs-lookup"><span data-stu-id="0a28e-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="0a28e-104">Zasady dla dowolnej zmiennej o typie określonym niejawnie dotyczą również niejawnie wpisane tablice.</span><span class="sxs-lookup"><span data-stu-id="0a28e-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="0a28e-105">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="0a28e-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="0a28e-106">Niejawnie wpisane tablice są zazwyczaj używane w wyrażeniach kwerend oraz typy anonimowe i inicjatory obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0a28e-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="0a28e-107">W poniższych przykładach pokazano, jak utworzyć tablicy o typie określonym niejawnie:</span><span class="sxs-lookup"><span data-stu-id="0a28e-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 <span data-ttu-id="0a28e-108">W poprzednim przykładzie zwróć uwagę, że z niejawnie wpisane tablice nie nawiasy kwadratowe są używane po lewej stronie instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="0a28e-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="0a28e-109">Należy też zauważyć, że Tablice nieregularne są inicjowane przy użyciu `new []` podobnie jak tablice jednowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="0a28e-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="0a28e-110">Niejawnie wpisane tablice w inicjatorach obiektów</span><span class="sxs-lookup"><span data-stu-id="0a28e-110">Implicitly-typed Arrays in Object Initializers</span></span>  
 <span data-ttu-id="0a28e-111">Po utworzeniu typu anonimowego, który zawiera tablicę tablicy musi niejawnie wpisanych w inicjatorze obiektu typu.</span><span class="sxs-lookup"><span data-stu-id="0a28e-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="0a28e-112">W poniższym przykładzie `contacts` jest niejawnie wpisanych tablicę typy anonimowe, z których każdy zawiera tablicę o nazwie `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="0a28e-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="0a28e-113">Należy pamiętać, że `var` — słowo kluczowe nie jest używany wewnątrz inicjatory obiektów.</span><span class="sxs-lookup"><span data-stu-id="0a28e-113">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0a28e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a28e-114">See Also</span></span>  
 [<span data-ttu-id="0a28e-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0a28e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0a28e-116">Niejawnie wpisane zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="0a28e-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [<span data-ttu-id="0a28e-117">Tablice</span><span class="sxs-lookup"><span data-stu-id="0a28e-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="0a28e-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="0a28e-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="0a28e-119">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="0a28e-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="0a28e-120">var</span><span class="sxs-lookup"><span data-stu-id="0a28e-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="0a28e-121">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="0a28e-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
