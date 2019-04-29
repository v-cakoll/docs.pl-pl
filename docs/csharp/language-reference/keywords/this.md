---
title: this — słowo kluczowe - C# odwołania
ms.custom: seodec18
description: this — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: af39ba6e20fb1a7c9e1a356ef5015afd885dbbca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660583"
---
# <a name="this-c-reference"></a><span data-ttu-id="13353-103">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="13353-103">this (C# Reference)</span></span>

<span data-ttu-id="13353-104">`this` — Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy, a także jest używane jako modyfikator pierwszy parametr metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="13353-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="13353-105">W tym artykule omówiono używanie `this` przy użyciu wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="13353-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="13353-106">Aby uzyskać więcej informacji na temat jej użycia w metody rozszerzenia zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="13353-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="13353-107">Poniżej znajdują się najczęstsze zastosowania usługi `this`:</span><span class="sxs-lookup"><span data-stu-id="13353-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="13353-108">Aby zakwalifikować się elementy członkowskie ukrywane podobnych nazwach, na przykład:</span><span class="sxs-lookup"><span data-stu-id="13353-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="13353-109">Aby przekazać obiekt jako parametr do innych metod, na przykład:</span><span class="sxs-lookup"><span data-stu-id="13353-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="13353-110">Aby zadeklarować indeksatorów, na przykład:</span><span class="sxs-lookup"><span data-stu-id="13353-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="13353-111">Statyczne funkcje Członkowskie, ponieważ istnieją na poziomie klasy, a nie jako część obiektu, nie masz `this` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="13353-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="13353-112">Jest to błąd do odwoływania się do `this` w metodzie statycznej.</span><span class="sxs-lookup"><span data-stu-id="13353-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="13353-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="13353-113">Example</span></span>

<span data-ttu-id="13353-114">W tym przykładzie `this` są używane do kwalifikowania `Employee` składowych, klasy `name` i `alias`, które są ukrywane o podobnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="13353-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="13353-115">Służy również przekazać obiekt do metody `CalcTax`, która należy do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="13353-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="13353-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="13353-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="13353-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13353-117">See also</span></span>

- [<span data-ttu-id="13353-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="13353-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13353-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="13353-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13353-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="13353-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="13353-121">base</span><span class="sxs-lookup"><span data-stu-id="13353-121">base</span></span>](base.md)
- [<span data-ttu-id="13353-122">Metody</span><span class="sxs-lookup"><span data-stu-id="13353-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
