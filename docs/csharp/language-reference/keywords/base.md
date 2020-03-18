---
title: podstawowe słowo kluczowe - Odwołanie do języka C#
description: Dowiedz się więcej o podstawowym senie kluczowym, które służy do uzyskiwania dostępu do członków klasy podstawowej z poziomu klasy pochodnej w języku C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713769"
---
# <a name="base-c-reference"></a><span data-ttu-id="cc2c5-103">base (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cc2c5-103">base (C# Reference)</span></span>

<span data-ttu-id="cc2c5-104">Słowo `base` kluczowe służy do uzyskiwania dostępu do elementów członkowskich klasy podstawowej z poziomu klasy pochodnej:</span><span class="sxs-lookup"><span data-stu-id="cc2c5-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="cc2c5-105">Wywołaj metodę w klasie podstawowej, która została zastąpiona przez inną metodę.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="cc2c5-106">Określ, który konstruktor klasy podstawowej powinien być wywoływany podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="cc2c5-107">Dostęp klasy podstawowej jest dozwolone tylko w konstruktora, metody wystąpienia lub akcesor właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="cc2c5-108">Jest to błąd, `base` aby użyć słowa kluczowego z wewnątrz metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="cc2c5-109">Klasa podstawowa, która jest dostępna jest klasa podstawowa określona w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="cc2c5-110">Na przykład, jeśli `class ClassB : ClassA`określisz, członkowie ClassA są dostępne z ClassB, niezależnie od klasy podstawowej ClassA.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="cc2c5-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc2c5-111">Example</span></span>

<span data-ttu-id="cc2c5-112">W tym przykładzie zarówno klasa `Person`podstawowa, jak `Employee`i klasa pochodna , mają metodę o nazwie `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="cc2c5-113">Za pomocą `base` słowa kluczowego, można `Getinfo` wywołać metodę na klasie podstawowej, z poziomu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="cc2c5-114">Aby uzyskać dodatkowe przykłady, zobacz [nowe](new-modifier.md), [wirtualne](virtual.md)i [zastąp](override.md).</span><span class="sxs-lookup"><span data-stu-id="cc2c5-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="cc2c5-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc2c5-115">Example</span></span>

<span data-ttu-id="cc2c5-116">W tym przykładzie pokazano, jak określić konstruktora klasy podstawowej wywoływane podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="cc2c5-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="cc2c5-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cc2c5-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cc2c5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc2c5-118">See also</span></span>

- [<span data-ttu-id="cc2c5-119">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="cc2c5-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cc2c5-120">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="cc2c5-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cc2c5-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cc2c5-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="cc2c5-122">względem tego ruchu</span><span class="sxs-lookup"><span data-stu-id="cc2c5-122">this</span></span>](./this.md)
