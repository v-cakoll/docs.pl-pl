---
title: Tablice niejawnie wpisane — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705720"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="adb47-102">Niejawnie wpisane tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="adb47-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="adb47-103">Można utworzyć tablicę niejawnie wpisaną, w której typ wystąpienia tablicy jest wywnioskowany z elementów określonych w inicjatorze tablicy.</span><span class="sxs-lookup"><span data-stu-id="adb47-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="adb47-104">Reguły dla dowolnej zmiennej niejawnie wpisane stosuje się również do tablic niejawnie wpisane.</span><span class="sxs-lookup"><span data-stu-id="adb47-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="adb47-105">Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="adb47-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="adb47-106">Tablice niejawnie typu są zwykle używane w wyrażeniach kwerend y wraz z typami anonimowymi oraz inicjazatory obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="adb47-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="adb47-107">W poniższych przykładach przedstawiono sposób tworzenia tablicy wpisanej niejawnie:</span><span class="sxs-lookup"><span data-stu-id="adb47-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="adb47-108">W poprzednim przykładzie należy zauważyć, że z tablic wpisanych niejawnie, nawiasy kwadratowe są używane po lewej stronie instrukcji inicjowania.</span><span class="sxs-lookup"><span data-stu-id="adb47-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="adb47-109">Należy również zauważyć, że postrzępione `new []` tablice są inicjowane przy użyciu takich jak tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="adb47-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="adb47-110">Tablice wpisane niejawnie w inicjatorach obiektów</span><span class="sxs-lookup"><span data-stu-id="adb47-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="adb47-111">Podczas tworzenia typu anonimowego, który zawiera tablicę, tablica musi być niejawnie wpisany w inicjatorze obiektu typu.</span><span class="sxs-lookup"><span data-stu-id="adb47-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="adb47-112">W poniższym `contacts` przykładzie jest niejawnie wpisany tablicy typów anonimowych, `PhoneNumbers`z których każdy zawiera tablicę o nazwie .</span><span class="sxs-lookup"><span data-stu-id="adb47-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="adb47-113">Należy zauważyć, że `var` słowo kluczowe nie jest używany wewnątrz inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="adb47-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="adb47-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adb47-114">See also</span></span>

- [<span data-ttu-id="adb47-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="adb47-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="adb47-116">Jawnie wpisana zmienna lokalna</span><span class="sxs-lookup"><span data-stu-id="adb47-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="adb47-117">Tablice</span><span class="sxs-lookup"><span data-stu-id="adb47-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="adb47-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="adb47-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="adb47-119">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="adb47-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="adb47-120">Var</span><span class="sxs-lookup"><span data-stu-id="adb47-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="adb47-121">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="adb47-121">LINQ in C#</span></span>](../../linq/index.md)
