---
title: Base — słowo kluczowe (odwołanie w C#)
description: Więcej informacji na temat base — słowo kluczowe, które umożliwia dostęp do elementów członkowskich klasy bazowej z poziomu klasy pochodnej w języku C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 8719ab79273701173530760ad1bec837c4f4302d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077895"
---
# <a name="base-c-reference"></a><span data-ttu-id="0090e-103">base (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0090e-103">base (C# Reference)</span></span>

<span data-ttu-id="0090e-104">`base` Słowo kluczowe jest używane do dostępu do składowych klasy bazowej z poziomu klasy pochodnej:</span><span class="sxs-lookup"><span data-stu-id="0090e-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="0090e-105">Wywołania metody w klasie bazowej, która została zastąpiona przy użyciu innej metody.</span><span class="sxs-lookup"><span data-stu-id="0090e-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="0090e-106">Określ, powinna być wywoływana konstruktora klasy bazowej, podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0090e-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="0090e-107">Dostęp klasy bazowej jest dozwolona tylko w konstruktorem, metodą wystąpienia lub metody dostępu właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0090e-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="0090e-108">Jest to błąd, aby użyć `base` — słowo kluczowe z wewnątrz metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="0090e-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="0090e-109">Klasa bazowa, która jest dostępna jest klasa bazowa, określonym w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="0090e-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="0090e-110">Na przykład, jeśli określisz `class ClassB : ClassA`, członkowie ClassA są dostępne z ClassB, niezależnie od tego, klasa bazowa ClassA.</span><span class="sxs-lookup"><span data-stu-id="0090e-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="0090e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0090e-111">Example</span></span>

<span data-ttu-id="0090e-112">W tym przykładzie, zarówno klasy bazowej, `Person`i klasy pochodnej `Employee`, ma metodę o nazwie `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="0090e-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="0090e-113">Za pomocą `base` — słowo kluczowe, jest możliwe do wywołania `Getinfo` metody w klasie bazowej, z poziomu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0090e-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="0090e-114">Aby uzyskać więcej przykładów, zobacz [nowe](../../../csharp/language-reference/keywords/new.md), [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), i [zastąpienia](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="0090e-114">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="0090e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0090e-115">Example</span></span>

<span data-ttu-id="0090e-116">Ten przykład przedstawia sposób określania konstruktora klasy bazowej, wywoływana podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0090e-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="0090e-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0090e-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0090e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0090e-118">See also</span></span>

- [<span data-ttu-id="0090e-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0090e-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0090e-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0090e-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0090e-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0090e-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="0090e-122">this</span><span class="sxs-lookup"><span data-stu-id="0090e-122">this</span></span>](../../../csharp/language-reference/keywords/this.md)