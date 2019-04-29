---
title: Niejawnie wpisane tablice - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 7aa820d87ec36f1963183b7e4e2e46de998a08c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61652016"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="e6e38-102">Niejawnie wpisane tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e6e38-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="e6e38-103">Można utworzyć tablicę niejawnie wpisany, w którym Typ wystąpienia tablicy jest wnioskowany z elementami określonymi w inicjatorze tablicy.</span><span class="sxs-lookup"><span data-stu-id="e6e38-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="e6e38-104">Reguły dotyczące niejawnie typizowanej zmiennej dotyczą również niejawnie wpisane tablice.</span><span class="sxs-lookup"><span data-stu-id="e6e38-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="e6e38-105">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="e6e38-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="e6e38-106">Niejawnie wpisane tablice są zazwyczaj używane w wyrażeniach zapytań oraz typy anonimowe i inicjatory obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e6e38-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="e6e38-107">W poniższych przykładach pokazano, jak utworzyć tablicę niejawnie wpisany:</span><span class="sxs-lookup"><span data-stu-id="e6e38-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="e6e38-108">W poprzednim przykładzie należy zauważyć, że z niejawnie wpisane tablice żadne nawiasy kwadratowe są używane po lewej stronie instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="e6e38-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="e6e38-109">Należy zauważyć, że Tablice nieregularne są inicjowane za pomocą `new []` podobnie jak w przypadku tablic jednego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="e6e38-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="e6e38-110">Niejawnie wpisane tablice w inicjatorach obiektu</span><span class="sxs-lookup"><span data-stu-id="e6e38-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="e6e38-111">Podczas tworzenia typu anonimowego, które zawiera tablicę tablicy musi być wpisana niejawnie w inicjatorze obiektu typu.</span><span class="sxs-lookup"><span data-stu-id="e6e38-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="e6e38-112">W poniższym przykładzie `contacts` jest niejawnie wpisany tablicą typów anonimowych, z których każdy zawiera tablicę o nazwie `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="e6e38-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="e6e38-113">Należy pamiętać, że `var` — słowo kluczowe nie jest używany w inicjatorach obiektów.</span><span class="sxs-lookup"><span data-stu-id="e6e38-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="e6e38-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6e38-114">See also</span></span>

- [<span data-ttu-id="e6e38-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e6e38-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e6e38-116">Jawnie wpisane zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="e6e38-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="e6e38-117">Tablice</span><span class="sxs-lookup"><span data-stu-id="e6e38-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="e6e38-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="e6e38-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="e6e38-119">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="e6e38-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="e6e38-120">var</span><span class="sxs-lookup"><span data-stu-id="e6e38-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)
- [<span data-ttu-id="e6e38-121">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="e6e38-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
