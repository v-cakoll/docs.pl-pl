---
title: This — odwołanie C# do tego słowa kluczowego
ms.custom: seodec18
description: this — słowoC# kluczowe (odwołanie)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 4a3342e73fef3effd54f72e68283eb6085eef5b5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608443"
---
# <a name="this-c-reference"></a><span data-ttu-id="c5217-103">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c5217-103">this (C# Reference)</span></span>

<span data-ttu-id="c5217-104">`this` Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy i jest również używane jako modyfikator pierwszego parametru metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c5217-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="c5217-105">W tym artykule omówiono użycie `this` z wystąpieniami klas.</span><span class="sxs-lookup"><span data-stu-id="c5217-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="c5217-106">Aby uzyskać więcej informacji o używaniu metod rozszerzających, zobacz [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c5217-106">For more information about its use in extension methods, see [Extension Methods](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="c5217-107">Poniżej przedstawiono typowe zastosowania `this`:</span><span class="sxs-lookup"><span data-stu-id="c5217-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="c5217-108">Aby zakwalifikować członków ukrytych przy użyciu podobnych nazw, na przykład:</span><span class="sxs-lookup"><span data-stu-id="c5217-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="c5217-109">Aby przekazać obiekt jako parametr do innych metod, na przykład:</span><span class="sxs-lookup"><span data-stu-id="c5217-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="c5217-110">Aby zadeklarować indeksatory, na przykład:</span><span class="sxs-lookup"><span data-stu-id="c5217-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="c5217-111">Statyczne funkcje członkowskie, ponieważ istnieją na poziomie klasy, a nie jako część obiektu, nie mają `this` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c5217-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="c5217-112">Wystąpił błąd podczas odwoływania się `this` do w metodzie statycznej.</span><span class="sxs-lookup"><span data-stu-id="c5217-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="c5217-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5217-113">Example</span></span>

<span data-ttu-id="c5217-114">W tym przykładzie `this` jest używany do `Employee` kwalifikowania elementów członkowskich `name` klasy i `alias`, które są ukryte przez podobne nazwy.</span><span class="sxs-lookup"><span data-stu-id="c5217-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="c5217-115">Jest on również używany do przekazywania obiektu do metody `CalcTax`, która należy do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="c5217-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="c5217-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c5217-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c5217-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5217-117">See also</span></span>

- [<span data-ttu-id="c5217-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c5217-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5217-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c5217-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c5217-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c5217-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c5217-121">base</span><span class="sxs-lookup"><span data-stu-id="c5217-121">base</span></span>](base.md)
- [<span data-ttu-id="c5217-122">Metody</span><span class="sxs-lookup"><span data-stu-id="c5217-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
