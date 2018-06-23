---
title: Base — słowo kluczowe (odwołanie w C#)
description: Więcej informacji na temat base — słowo kluczowe, która umożliwia dostęp do elementów członkowskich klasy podstawowej z w klasie pochodnej w języku C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 94bfcbacd8c222004c1a013cc855ac8d46aab05f
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314662"
---
# <a name="base-c-reference"></a><span data-ttu-id="75d98-103">base (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="75d98-103">base (C# Reference)</span></span>

<span data-ttu-id="75d98-104">`base` Umożliwia dostęp do elementów członkowskich klasy podstawowej z w klasie pochodnej — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="75d98-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="75d98-105">Wywołanie metody w klasie podstawowej, która już została zastąpiona przy użyciu innej metody.</span><span class="sxs-lookup"><span data-stu-id="75d98-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="75d98-106">Określ, które konstruktora klasy podstawowej powinna być wywoływana podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="75d98-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="75d98-107">Dostęp klasa podstawowa jest dozwolony tylko w konstruktorze, metody wystąpienia lub metody dostępu właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75d98-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="75d98-108">Jest błędem `base` — słowo kluczowe z wewnątrz metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="75d98-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="75d98-109">Klasa podstawowa, który jest dostępny jest klasą bazową określony w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="75d98-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="75d98-110">Na przykład jeśli określisz `class ClassB : ClassA`, członkowie ClassA są dostępne z ClassB, niezależnie od tego, w klasie podstawowej ClassA.</span><span class="sxs-lookup"><span data-stu-id="75d98-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="75d98-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="75d98-111">Example</span></span>

<span data-ttu-id="75d98-112">W tym przykładzie zarówno klasę podstawową, `Person`i klasy pochodnej `Employee`, ma metodę o nazwie `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="75d98-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="75d98-113">Za pomocą `base` — słowo kluczowe, jest możliwe do wywołania `Getinfo` metody w klasie podstawowej, za pomocą klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="75d98-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="75d98-114">Dodatkowe przykłady można znaleźć [nowe](../../../csharp/language-reference/keywords/new.md), [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), i [zastąpienia](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="75d98-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="75d98-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="75d98-115">Example</span></span>

<span data-ttu-id="75d98-116">Ten przykład przedstawia sposób określenia konstruktora klasy podstawowej, wywoływana podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="75d98-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="75d98-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="75d98-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="75d98-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75d98-118">See also</span></span>

[<span data-ttu-id="75d98-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="75d98-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="75d98-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="75d98-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="75d98-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="75d98-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="75d98-122">this</span><span class="sxs-lookup"><span data-stu-id="75d98-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)