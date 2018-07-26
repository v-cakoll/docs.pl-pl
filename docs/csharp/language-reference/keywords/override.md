---
title: override (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199267"
---
# <a name="override-c-reference"></a><span data-ttu-id="6ed82-102">override (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6ed82-102">override (C# Reference)</span></span>
<span data-ttu-id="6ed82-103">`override` Modyfikator jest wymagane, aby rozszerzyć lub zmodyfikować implementacji abstrakcyjne lub wirtualne dziedziczonej metody, właściwości, indeksatora lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6ed82-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ed82-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ed82-104">Example</span></span>  
 <span data-ttu-id="6ed82-105">W tym przykładzie `Square` klasa musi dostarczać implementację zgodnym z przesłoniętą `Area` ponieważ `Area` jest dziedziczony z abstrakcyjnej `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="6ed82-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 <span data-ttu-id="6ed82-106">`override` Metoda dostarcza nową implementację elementu członkowskiego, który jest dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="6ed82-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="6ed82-107">Metoda, która została zastąpiona przez `override` deklaracji jest znany jako przesłonięte metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="6ed82-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="6ed82-108">Zastąpione metody podstawowej musi mieć taką samą sygnaturę jak `override` metody.</span><span class="sxs-lookup"><span data-stu-id="6ed82-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="6ed82-109">Aby uzyskać informacji na temat dziedziczenia, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="6ed82-109">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="6ed82-110">Nie można zastąpić niewirtualną lub statycznej metody.</span><span class="sxs-lookup"><span data-stu-id="6ed82-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="6ed82-111">Zastąpione metody podstawowej musi być `virtual`, `abstract`, lub `override`.</span><span class="sxs-lookup"><span data-stu-id="6ed82-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="6ed82-112">`override` Deklaracji nie można zmienić dostępności `virtual` metody.</span><span class="sxs-lookup"><span data-stu-id="6ed82-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="6ed82-113">Zarówno `override` metody i `virtual` metoda musi mieć takie same [modyfikator dostępu dla poziomu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="6ed82-113">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="6ed82-114">Nie można użyć `new`, `static`, lub `virtual` Modyfikatory do modyfikowania `override` metody.</span><span class="sxs-lookup"><span data-stu-id="6ed82-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="6ed82-115">Przesłanianie deklaracja właściwości należy określić jako właściwość dziedziczona dokładnie tych samych modyfikator dostępu, typ i nazwa i właściwości musi być `virtual`, `abstract`, lub `override`.</span><span class="sxs-lookup"><span data-stu-id="6ed82-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="6ed82-116">Aby uzyskać więcej informacji o sposobie używania `override` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [użycie przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="6ed82-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ed82-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ed82-117">Example</span></span>  
 <span data-ttu-id="6ed82-118">Ten przykład definiuje klasę bazową, o nazwie `Employee`, a klasa pochodna o nazwie `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="6ed82-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="6ed82-119">`SalesEmployee` Klasa zawiera dodatkowe właściwości `salesbonus`i zastępuje metodę `CalculatePay` niezbędny do konta.</span><span class="sxs-lookup"><span data-stu-id="6ed82-119">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6ed82-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ed82-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6ed82-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ed82-121">See Also</span></span>  
 [<span data-ttu-id="6ed82-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ed82-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6ed82-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6ed82-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6ed82-124">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="6ed82-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="6ed82-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6ed82-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6ed82-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6ed82-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="6ed82-127">abstract</span><span class="sxs-lookup"><span data-stu-id="6ed82-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="6ed82-128">virtual</span><span class="sxs-lookup"><span data-stu-id="6ed82-128">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="6ed82-129">new</span><span class="sxs-lookup"><span data-stu-id="6ed82-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="6ed82-130">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="6ed82-130">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
