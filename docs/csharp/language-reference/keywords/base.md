---
title: podstawowe słowo kluczowe C# — odwołanie
description: Dowiedz się więcej o słowie kluczowym Base, które służy do uzyskiwania dostępu do elementów członkowskich klasy bazowej z C#poziomu klasy pochodnej w.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713769"
---
# <a name="base-c-reference"></a><span data-ttu-id="4a0fc-103">base (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4a0fc-103">base (C# Reference)</span></span>

<span data-ttu-id="4a0fc-104">Słowo kluczowe `base` służy do uzyskiwania dostępu do składowych klasy bazowej z poziomu klasy pochodnej:</span><span class="sxs-lookup"><span data-stu-id="4a0fc-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="4a0fc-105">Wywołaj metodę w klasie bazowej, która została zastąpiona przez inną metodę.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="4a0fc-106">Określ, który Konstruktor klasy bazowej powinien być wywoływany podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="4a0fc-107">Dostęp do klasy podstawowej jest dozwolony tylko w konstruktorze, metodzie wystąpienia lub akcesorze właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="4a0fc-108">Wystąpił błąd, aby użyć słowa kluczowego `base` z metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="4a0fc-109">Dostępną klasą bazową jest klasa bazowa określona w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="4a0fc-110">Na przykład jeśli określisz `class ClassB : ClassA`, członkowie ClassA są dostępni z ClassB, niezależnie od klasy bazowej ClassA.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="4a0fc-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a0fc-111">Example</span></span>

<span data-ttu-id="4a0fc-112">W tym przykładzie zarówno Klasa bazowa, `Person`, jak i Klasa pochodna, `Employee`, mają metodę o nazwie `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="4a0fc-113">Za pomocą słowa kluczowego `base` można wywołać metodę `Getinfo` w klasie bazowej z poziomu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="4a0fc-114">Aby uzyskać więcej przykładów, zobacz [nowe](new-modifier.md), [wirtualne](virtual.md)i [przesłonięcie](override.md).</span><span class="sxs-lookup"><span data-stu-id="4a0fc-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="4a0fc-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a0fc-115">Example</span></span>

<span data-ttu-id="4a0fc-116">Ten przykład pokazuje, jak określić Konstruktor klasy bazowej wywoływany podczas tworzenia wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="4a0fc-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="4a0fc-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4a0fc-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4a0fc-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a0fc-118">See also</span></span>

- [<span data-ttu-id="4a0fc-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4a0fc-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4a0fc-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4a0fc-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4a0fc-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4a0fc-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4a0fc-122">this</span><span class="sxs-lookup"><span data-stu-id="4a0fc-122">this</span></span>](./this.md)
