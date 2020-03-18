---
title: to słowo kluczowe — odwołanie do języka C#
description: to słowo kluczowe (Odwołanie do języka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715108"
---
# <a name="this-c-reference"></a><span data-ttu-id="ecae5-103">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ecae5-103">this (C# Reference)</span></span>

<span data-ttu-id="ecae5-104">Słowo `this` kluczowe odnosi się do bieżącego wystąpienia klasy i jest również używany jako modyfikator pierwszego parametru metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ecae5-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="ecae5-105">W tym artykule omówiono użycie z `this` wystąpieniami klasy.</span><span class="sxs-lookup"><span data-stu-id="ecae5-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="ecae5-106">Aby uzyskać więcej informacji na temat jego użycia w metodach [rozszerzeń,](../../programming-guide/classes-and-structs/extension-methods.md)zobacz Metody rozszerzenia .</span><span class="sxs-lookup"><span data-stu-id="ecae5-106">For more information about its use in extension methods, see [Extension Methods](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="ecae5-107">Oto typowe `this`zastosowania:</span><span class="sxs-lookup"><span data-stu-id="ecae5-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="ecae5-108">Aby zakwalifikować członków ukrytych pod podobnymi nazwami, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ecae5-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="ecae5-109">Aby przekazać obiekt jako parametr do innych metod, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ecae5-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="ecae5-110">Aby zadeklarować indeksatory, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ecae5-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="ecae5-111">Funkcje statyczne elementu członkowskiego, ponieważ istnieją na poziomie klasy, a `this` nie jako część obiektu, nie mają wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ecae5-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="ecae5-112">Jest to błąd, `this` do wyniku do niego w metodzie statycznej.</span><span class="sxs-lookup"><span data-stu-id="ecae5-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="ecae5-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecae5-113">Example</span></span>

<span data-ttu-id="ecae5-114">W tym `this` przykładzie jest używany `Employee` do `name` zakwalifikowania członków klasy i `alias`, które są ukryte pod podobnymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="ecae5-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="ecae5-115">Jest również używany do przekazywania obiektu `CalcTax`do metody , która należy do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="ecae5-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="ecae5-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ecae5-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ecae5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecae5-117">See also</span></span>

- [<span data-ttu-id="ecae5-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="ecae5-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ecae5-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ecae5-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ecae5-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ecae5-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ecae5-121">base</span><span class="sxs-lookup"><span data-stu-id="ecae5-121">base</span></span>](base.md)
- [<span data-ttu-id="ecae5-122">Metody</span><span class="sxs-lookup"><span data-stu-id="ecae5-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
