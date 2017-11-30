---
title: "dynamic (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e3bf51ab62e195f7a5d1f0641f62380977c731ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="f260f-102">dynamic (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f260f-102">dynamic (C# Reference)</span></span>
<span data-ttu-id="f260f-103">`dynamic` Typ umożliwia operacje, w których występuje Pomiń sprawdzanie typów w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f260f-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="f260f-104">Jednak te operacje zostaną rozwiązane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f260f-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="f260f-105">`dynamic` Typu ułatwiają dostęp do interfejsów API modelu COM, takich jak Office interfejsów API automatyzacji i również do dynamicznego interfejsów API, takich jak biblioteki IronPython oraz do HTML modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="f260f-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="f260f-106">Typ `dynamic` zachowuje się jak typ `object` w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="f260f-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="f260f-107">Jednak operacje, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typ sprawdzana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="f260f-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="f260f-108">Pakiety kompilatora razem informacje na temat operacji, a tych informacji jest później używany do oceny operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f260f-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="f260f-109">W trakcie procesu zmiennych typu `dynamic` są kompilowane do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="f260f-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="f260f-110">W związku z tym wpisz `dynamic` istnieje tylko w czasie kompilacji, nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f260f-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>  
  
 <span data-ttu-id="f260f-111">Poniższy przykład zachowanie różni się od zmiennej typu `dynamic` do zmiennej typu `object`.</span><span class="sxs-lookup"><span data-stu-id="f260f-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="f260f-112">Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w `WriteLine` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="f260f-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="f260f-113">Pokazuje IntelliSense **dynamiczne** dla `dyn` i **obiektu** dla `obj`.</span><span class="sxs-lookup"><span data-stu-id="f260f-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 <span data-ttu-id="f260f-114">`WriteLine` Instrukcje prezentuje typy środowiska wykonawczego `dyn` i `obj`.</span><span class="sxs-lookup"><span data-stu-id="f260f-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="f260f-115">W tym momencie mają ten sam typ, liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f260f-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="f260f-116">Są następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f260f-116">The following output is produced:</span></span>  
  
 `System.Int32`  
  
 `System.Int32`  
  
 <span data-ttu-id="f260f-117">Różnice między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze między deklaracjami i `WriteLine` instrukcje w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f260f-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 <span data-ttu-id="f260f-118">Błąd kompilatora jest zgłaszany, próba dodania całkowitą i obiektu w wyrażeniu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="f260f-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="f260f-119">Jednak nie będzie zgłaszany błąd dla `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="f260f-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="f260f-120">Wyrażenie, które zawiera `dyn` nie są sprawdzane w czasie kompilacji, ponieważ typ `dyn` jest `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="f260f-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>  
  
## <a name="context"></a><span data-ttu-id="f260f-121">Kontekst</span><span class="sxs-lookup"><span data-stu-id="f260f-121">Context</span></span>  
 <span data-ttu-id="f260f-122">`dynamic` — Słowo kluczowe może występować bezpośrednio lub jako składnik skonstruowanego typu w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="f260f-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>  
  
-   <span data-ttu-id="f260f-123">W deklaracjach jako typ właściwości, pola, indeksatora, parametr zwracają wartość zmiennej lokalnej lub ograniczenie typu.</span><span class="sxs-lookup"><span data-stu-id="f260f-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="f260f-124">Następujące klasy używa definicji `dynamic` w kilka różnych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f260f-124">The following class definition uses `dynamic` in several different declarations.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   <span data-ttu-id="f260f-125">Podczas konwersji typu jawnego jako typ docelowy konwersji.</span><span class="sxs-lookup"><span data-stu-id="f260f-125">In explicit type conversions, as the target type of a conversion.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   <span data-ttu-id="f260f-126">W dowolnym kontekście, gdy typy służyć jako wartości, takich jak prawej strony `is` operator lub `as` , operator lub jako argument `typeof` jako część skonstruowanego typu.</span><span class="sxs-lookup"><span data-stu-id="f260f-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="f260f-127">Na przykład `dynamic` mogą być używane w następujących wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="f260f-127">For example, `dynamic` can be used in the following expressions.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="f260f-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f260f-128">Example</span></span>  
 <span data-ttu-id="f260f-129">W poniższym przykładzie użyto `dynamic` w wielu deklaracjach.</span><span class="sxs-lookup"><span data-stu-id="f260f-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="f260f-130">`Main` Metody różnic między Sprawdzanie typu run-time sprawdzenia typu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f260f-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 <span data-ttu-id="f260f-131">Aby uzyskać dodatkowe informacje i przykłady, zobacz [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="f260f-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f260f-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f260f-132">See Also</span></span>  
 <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [<span data-ttu-id="f260f-133">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="f260f-133">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="f260f-134">obiekt</span><span class="sxs-lookup"><span data-stu-id="f260f-134">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
 [<span data-ttu-id="f260f-135">jest</span><span class="sxs-lookup"><span data-stu-id="f260f-135">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="f260f-136">jako</span><span class="sxs-lookup"><span data-stu-id="f260f-136">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="f260f-137">TypeOf</span><span class="sxs-lookup"><span data-stu-id="f260f-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="f260f-138">Porady: bezpieczne rzutowanie za pomocą jako operatorów i is</span><span class="sxs-lookup"><span data-stu-id="f260f-138">How to: Safely Cast by Using as and is Operators</span></span>](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
 [<span data-ttu-id="f260f-139">Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie</span><span class="sxs-lookup"><span data-stu-id="f260f-139">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
