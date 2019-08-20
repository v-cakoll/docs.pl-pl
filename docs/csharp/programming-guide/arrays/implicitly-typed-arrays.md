---
title: Niejawnie wpisane tablice C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 36ca18adc392643107b43a947656846f3b94a2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597344"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="a04ec-102">Niejawnie wpisane tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a04ec-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="a04ec-103">Można utworzyć tablicę z określonym niejawnie, w której typ wystąpienia tablicy jest wywnioskowany na podstawie elementów określonych w inicjatorze tablicy.</span><span class="sxs-lookup"><span data-stu-id="a04ec-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="a04ec-104">Reguły dla dowolnej zmiennej o typie określonym niejawnie mają zastosowanie również do tablic o typie określonym niejawnie.</span><span class="sxs-lookup"><span data-stu-id="a04ec-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="a04ec-105">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="a04ec-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="a04ec-106">Tablice o typie określonym niejawnie są zwykle używane w wyrażeniach zapytań wraz z typami anonimowymi i inicjatorami obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a04ec-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="a04ec-107">W poniższych przykładach pokazano, jak utworzyć tablicę o typie określonym niejawnie:</span><span class="sxs-lookup"><span data-stu-id="a04ec-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="a04ec-108">W poprzednim przykładzie Zwróć uwagę, że z tablicami z niejawnie określonym typem, w lewej części instrukcji inicjowania nie są używane żadne nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="a04ec-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="a04ec-109">Zwróć uwagę na to, że tablice nieregularne są `new []` inicjowane przy użyciu podobnie jak w przypadku tablic jednowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="a04ec-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="a04ec-110">Tablice o typie określonym niejawnie w inicjatorach obiektów</span><span class="sxs-lookup"><span data-stu-id="a04ec-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="a04ec-111">Podczas tworzenia typu anonimowego, który zawiera tablicę, Tablica musi być niejawnie wpisana w inicjatorze obiektu typu.</span><span class="sxs-lookup"><span data-stu-id="a04ec-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="a04ec-112">W poniższym przykładzie `contacts` jest tablicą typów anonimowych niejawnie, z których każdy zawiera tablicę o nazwie `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="a04ec-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="a04ec-113">Należy zauważyć, `var` że słowo kluczowe nie jest używane wewnątrz inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="a04ec-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="a04ec-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a04ec-114">See also</span></span>

- [<span data-ttu-id="a04ec-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a04ec-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a04ec-116">Jawnie wpisane zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="a04ec-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="a04ec-117">Tablice</span><span class="sxs-lookup"><span data-stu-id="a04ec-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="a04ec-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="a04ec-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="a04ec-119">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="a04ec-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="a04ec-120">var</span><span class="sxs-lookup"><span data-stu-id="a04ec-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="a04ec-121">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="a04ec-121">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
