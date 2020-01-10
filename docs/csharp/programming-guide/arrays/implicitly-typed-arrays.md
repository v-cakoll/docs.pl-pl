---
title: Niejawnie wpisane tablice C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705720"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="10ab4-102">Niejawnie wpisane tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="10ab4-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="10ab4-103">Można utworzyć tablicę z określonym niejawnie, w której typ wystąpienia tablicy jest wywnioskowany na podstawie elementów określonych w inicjatorze tablicy.</span><span class="sxs-lookup"><span data-stu-id="10ab4-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="10ab4-104">Reguły dla dowolnej zmiennej o typie określonym niejawnie mają zastosowanie również do tablic o typie określonym niejawnie.</span><span class="sxs-lookup"><span data-stu-id="10ab4-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="10ab4-105">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="10ab4-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="10ab4-106">Tablice o typie określonym niejawnie są zwykle używane w wyrażeniach zapytań wraz z typami anonimowymi i inicjatorami obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="10ab4-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="10ab4-107">W poniższych przykładach pokazano, jak utworzyć tablicę o typie określonym niejawnie:</span><span class="sxs-lookup"><span data-stu-id="10ab4-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="10ab4-108">W poprzednim przykładzie Zwróć uwagę, że z tablicami z niejawnie określonym typem, w lewej części instrukcji inicjowania nie są używane żadne nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="10ab4-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="10ab4-109">Należy zauważyć, że tablice nieregularne są inicjowane przy użyciu `new []` podobnie jak w przypadku tablic jednowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="10ab4-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="10ab4-110">Tablice o typie określonym niejawnie w inicjatorach obiektów</span><span class="sxs-lookup"><span data-stu-id="10ab4-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="10ab4-111">Podczas tworzenia typu anonimowego, który zawiera tablicę, Tablica musi być niejawnie wpisana w inicjatorze obiektu typu.</span><span class="sxs-lookup"><span data-stu-id="10ab4-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="10ab4-112">W poniższym przykładzie `contacts` jest tablicą typów anonimowych niejawnie, z których każdy zawiera tablicę o nazwie `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="10ab4-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="10ab4-113">Należy zauważyć, że słowo kluczowe `var` nie jest używane wewnątrz inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="10ab4-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="10ab4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10ab4-114">See also</span></span>

- [<span data-ttu-id="10ab4-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="10ab4-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="10ab4-116">Jawnie wpisane zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="10ab4-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="10ab4-117">Tablice</span><span class="sxs-lookup"><span data-stu-id="10ab4-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="10ab4-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="10ab4-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="10ab4-119">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="10ab4-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="10ab4-120">var</span><span class="sxs-lookup"><span data-stu-id="10ab4-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="10ab4-121">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="10ab4-121">LINQ in C#</span></span>](../../linq/index.md)
