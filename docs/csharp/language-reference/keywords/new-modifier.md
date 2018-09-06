---
title: New — modyfikator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 496339a7c3b95f16fd13479b096d90058b0799d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747986"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="00f3c-102">New — modyfikator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="00f3c-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="00f3c-103">Stosowania jako modyfikator deklaracji, `new` — słowo kluczowe jawnie ukrywa składową, która jest dziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="00f3c-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="00f3c-104">Po ukryciu dziedziczonego członka, pochodna wersja członka zastępuje wersję klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="00f3c-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="00f3c-105">Chociaż można ukryć elementy członkowskie bez korzystania z `new` modyfikator, zostanie wyświetlone ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="00f3c-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="00f3c-106">Jeśli używasz `new` Aby jawnie ukryć członka, powoduje to pominięcie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="00f3c-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="00f3c-107">Do ukrywania odziedziczonej składowej, Zadeklaruj go w klasie pochodnej przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikuj go za pomocą `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="00f3c-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="00f3c-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="00f3c-108">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="00f3c-109">W tym przykładzie `BaseC.Invoke` jest ukryta przez `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="00f3c-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="00f3c-110">Pole `x` pozostanie niezmienione, ponieważ nie jest ukryty przez podobną nazwę.</span><span class="sxs-lookup"><span data-stu-id="00f3c-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="00f3c-111">Ukrywanie nazw poprzez dziedziczenie ma jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="00f3c-111">Name hiding through inheritance takes one of the following forms:</span></span>

<span data-ttu-id="00f3c-112">Ogólnie rzecz biorąc stała, pole, właściwość lub typ, który został wprowadzony w klasie lub strukturze ukrywa wszystkie składowe klasy podstawowej, które współdzielą jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="00f3c-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="00f3c-113">Istnieją przypadki specjalne.</span><span class="sxs-lookup"><span data-stu-id="00f3c-113">There are special cases.</span></span>  <span data-ttu-id="00f3c-114">Na przykład, jeśli zadeklarujesz nowe pole o nazwie `N` typu, którego nie można wywołać i typ podstawowy deklaruje `N` jako metodę, nowe pole nie powoduje ukrycia podstawowej deklaracji w składni wywołania.</span><span class="sxs-lookup"><span data-stu-id="00f3c-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="00f3c-115">Zobacz [specyfikacji języka C# w wersji 5.0](https://www.microsoft.com/download/details.aspx?id=7029) Aby uzyskać szczegółowe informacje (zobacz sekcję "Wyszukanie członka" w sekcji "Wyrażenia").</span><span class="sxs-lookup"><span data-stu-id="00f3c-115">See the [C# 5.0 language specification](https://www.microsoft.com/download/details.aspx?id=7029) for details (see section "Member Lookup" in section "Expressions").</span></span>

<span data-ttu-id="00f3c-116">Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="00f3c-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="00f3c-117">Ukrywa wszystkie metody klasy podstawowej, które mają taki sam podpis.</span><span class="sxs-lookup"><span data-stu-id="00f3c-117">It also hides all base class methods that have the same signature.</span></span>

<span data-ttu-id="00f3c-118">Indeksator wprowadzony w klasie lub strukturze ukrywa wszystkie indeksatory klas podstawowych, które mają taki sam podpis.</span><span class="sxs-lookup"><span data-stu-id="00f3c-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="00f3c-119">Jest to błąd, można użyć zarówno `new` i [zastąpienia](override.md) na tym samym użytkownikiem, ponieważ modyfikatorów mają znaczenie wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="00f3c-119">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="00f3c-120">`new` Modyfikator tworzy nowy element członkowski o takiej samej nazwie i powoduje, że oryginalny element członkowski będzie ukryty.</span><span class="sxs-lookup"><span data-stu-id="00f3c-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="00f3c-121">`override` Modyfikator rozszerza implementację dla odziedziczonego członka.</span><span class="sxs-lookup"><span data-stu-id="00f3c-121">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="00f3c-122">Za pomocą `new` modyfikatora w deklaracji, która nie ukrywa dziedziczonej składowej generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="00f3c-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="00f3c-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="00f3c-123">Example</span></span>

<span data-ttu-id="00f3c-124">W tym przykładzie klasę bazową `BaseC`i klasę pochodną `DerivedC`, użyj tej samej nazwy pola `x`, która ukrywa wartość odziedziczonego pola.</span><span class="sxs-lookup"><span data-stu-id="00f3c-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="00f3c-125">W przykładzie pokazano użycie `new` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="00f3c-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="00f3c-126">Ilustruje też sposób dostępu do ukrytych członków klasy podstawowej za pomocą ich w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="00f3c-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="00f3c-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="00f3c-127">Example</span></span>

<span data-ttu-id="00f3c-128">W tym przykładzie klasa zagnieżdżona ukrywa klasę, która ma taką samą nazwę w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="00f3c-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="00f3c-129">W przykładzie pokazano sposób użycia `new` modyfikator, aby wyeliminować komunikat ostrzegawczy i instrukcje dostęp do członków ukrytej klasy za pomocą ich w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="00f3c-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="00f3c-130">Jeśli usuniesz `new` modyfikator, program się skompiluje i uruchamiania, ale otrzymasz następujące ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="00f3c-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="00f3c-131">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="00f3c-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="00f3c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00f3c-132">See also</span></span>

- [<span data-ttu-id="00f3c-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="00f3c-133">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="00f3c-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="00f3c-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="00f3c-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="00f3c-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="00f3c-136">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="00f3c-136">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="00f3c-137">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="00f3c-137">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="00f3c-138">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="00f3c-138">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="00f3c-139">Użycie przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="00f3c-139">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
