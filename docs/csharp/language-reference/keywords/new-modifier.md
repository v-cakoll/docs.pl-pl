---
title: new — Modyfikator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: b66cfacc2203e0e529c19b5c566abad6c676f149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273971"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="3b8aa-102">new — Modyfikator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3b8aa-102">new Modifier (C# Reference)</span></span>
<span data-ttu-id="3b8aa-103">Gdy jest używany jako modyfikatory deklaracji, `new` — słowo kluczowe jawnie ukrywa element członkowski, który jest dziedziczona z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="3b8aa-104">Ukrycie dziedziczonego elementu członkowskiego pochodnymi wersjami element członkowski zastępuje wersji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="3b8aa-105">Mimo że można ukryć składniki bez użycia `new` modyfikator, zostanie wyświetlone ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="3b8aa-106">Jeśli używasz `new` Aby jawnie ukrywa element członkowski, powoduje pominięcie to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>  
  
 <span data-ttu-id="3b8aa-107">Ukrywa dziedziczony element członkowski, Zadeklaruj ją w klasie pochodnej przy użyciu takiej samej nazwie elementu członkowskiego i zmodyfikuj go przy użyciu `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="3b8aa-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3b8aa-108">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 <span data-ttu-id="3b8aa-109">W tym przykładzie `BaseC.Invoke` jest ukryty przez `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="3b8aa-110">Pole `x` nie ma wpływ, ponieważ nie jest ukryty przez podobną nazwę.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>  
  
 <span data-ttu-id="3b8aa-111">Ukrywanie poprzez dziedziczenie nazwa przyjmuje jeden z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="3b8aa-111">Name hiding through inheritance takes one of the following forms:</span></span>  
  
-   <span data-ttu-id="3b8aa-112">Ogólnie rzecz biorąc stała, pola, właściwości lub typu, która została wprowadzona w klasie lub strukturze powoduje ukrycie wszystkich elementów członkowskich klasy podstawowej, które mają nazwy.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="3b8aa-113">Brak przypadków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-113">There are special cases.</span></span>  <span data-ttu-id="3b8aa-114">Na przykład, jeśli zadeklarować nowe pole o nazwie `N` typu, który nie jest wywoływać i typem bazowym deklaruje `N` jako metodę nowego pola nie ukrywa deklaracji podstawowej w Składnia wywołania.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="3b8aa-115">Zobacz [specyfikacja języka C# w wersji 5.0](https://www.microsoft.com/download/details.aspx?id=7029) szczegółowe (zobacz sekcję "Wyszukiwanie elementu członkowskiego" w sekcji "Wyrażenia").</span><span class="sxs-lookup"><span data-stu-id="3b8aa-115">See the [C# 5.0 language specification](https://www.microsoft.com/download/details.aspx?id=7029) for details (see section "Member Lookup" in section "Expressions").</span></span>  
  
-   <span data-ttu-id="3b8aa-116">Metody wprowadzone w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="3b8aa-117">Ukrywa również wszystkie metody klasy podstawowej, które mają taką samą sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-117">It also hides all base class methods that have the same signature.</span></span>  
  
-   <span data-ttu-id="3b8aa-118">Indeksator wprowadzone w klasie lub strukturze ukrywa wszystkie indeksatory klasy podstawowej, które mają taką samą sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>  
  
 <span data-ttu-id="3b8aa-119">Jest błąd, aby korzystać z obu `new` i [zastąpienia](../../../csharp/language-reference/keywords/override.md) na tym samym użytkownikiem, ponieważ dwie Modyfikatory mają znaczenie wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-119">It is an error to use both `new` and [override](../../../csharp/language-reference/keywords/override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="3b8aa-120">`new` Modyfikator tworzy nowy element członkowski o takiej samej nazwie i powoduje, że oryginalnego elementu na będą ukryte.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="3b8aa-121">`override` Modyfikator rozszerza implementację dla dziedziczonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-121">The `override` modifier extends the implementation for an inherited member.</span></span>  
  
 <span data-ttu-id="3b8aa-122">Przy użyciu `new` modyfikatora w deklaracji, która nie ukrywa dziedziczonego elementu członkowskiego generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b8aa-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b8aa-123">Example</span></span>  
 <span data-ttu-id="3b8aa-124">W tym przykładzie klasa podstawowa, `BaseC`i w klasie pochodnej `DerivedC`, użyj takiej samej nazwy pola `x`, która ukrywa wartość pola dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="3b8aa-125">W przykładzie pokazano użycie `new` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="3b8aa-126">Ilustruje też sposób dostępu do ukrytych elementów członkowskich klasy podstawowej za pomocą ich w pełni kwalifikowane nazwy.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="3b8aa-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b8aa-127">Example</span></span>  
 <span data-ttu-id="3b8aa-128">W tym przykładzie klasa zagnieżdżona ukrywa klasę, która ma taką samą nazwę w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="3b8aa-129">W przykładzie pokazano sposób użycia `new` modyfikator wyeliminować komunikat ostrzegawczy i jak dostęp do członków klasy ukryte przy użyciu ich w pełni kwalifikowane nazwy.</span><span class="sxs-lookup"><span data-stu-id="3b8aa-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 <span data-ttu-id="3b8aa-130">Jeśli usuniesz `new` modyfikator, program będzie nadal skompilować i uruchomić, ale spowoduje następujące ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="3b8aa-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="3b8aa-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3b8aa-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b8aa-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b8aa-132">See Also</span></span>  
 [<span data-ttu-id="3b8aa-133">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3b8aa-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3b8aa-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3b8aa-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3b8aa-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3b8aa-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3b8aa-136">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="3b8aa-136">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="3b8aa-137">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="3b8aa-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="3b8aa-138">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="3b8aa-138">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="3b8aa-139">Użycie przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="3b8aa-139">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
