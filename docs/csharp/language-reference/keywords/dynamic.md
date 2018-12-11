---
title: dynamiczne - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: 7ac9c04da277af6a03a6a8994763451146adefc8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243312"
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="823ee-102">dynamic (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="823ee-102">dynamic (C# Reference)</span></span>

<span data-ttu-id="823ee-103">`dynamic` Typ umożliwia operacje, w których występuje Pomiń sprawdzanie typów w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="823ee-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="823ee-104">Zamiast tego te operacje są rozwiązywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="823ee-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="823ee-105">`dynamic` Typu upraszcza dostęp do interfejsów API modelu COM, takich jak Office interfejsów API usługi Automation i również dynamiczne interfejsy API, takich jak biblioteki IronPython i do HTML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="823ee-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="823ee-106">Typ `dynamic` zachowuje się jak typ `object` w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="823ee-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="823ee-107">Jednak operacje, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typ sprawdzana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="823ee-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="823ee-108">Pakiety kompilatora, które razem informacje na temat operacji, a te informacje później użyte do oceny operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="823ee-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="823ee-109">W ramach procesu, a zmienne typu `dynamic` są kompilowane do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="823ee-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="823ee-110">W związku z tym, wpisz `dynamic` istnieje tylko w czasie kompilacji, nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="823ee-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="823ee-111">Poniższy przykład zachowanie różni się od zmiennej typu `dynamic` do zmiennej typu `object`.</span><span class="sxs-lookup"><span data-stu-id="823ee-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="823ee-112">Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w `WriteLine` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="823ee-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="823ee-113">Funkcja IntelliSense pokazuje **dynamiczne** dla `dyn` i **obiektu** dla `obj`.</span><span class="sxs-lookup"><span data-stu-id="823ee-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="823ee-114">`WriteLine` Instrukcji prezentuje typy środowiska wykonawczego `dyn` i `obj`.</span><span class="sxs-lookup"><span data-stu-id="823ee-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="823ee-115">W tym momencie mają ten sam typ, liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="823ee-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="823ee-116">Są następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="823ee-116">The following output is produced:</span></span>

`System.Int32`

`System.Int32`

<span data-ttu-id="823ee-117">Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze między deklaracjami i `WriteLine` instrukcji w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="823ee-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="823ee-118">Błąd kompilatora jest zgłaszany, próba dodanie całkowitą, a obiekt w wyrażeniu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="823ee-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="823ee-119">Jednak błąd nie jest zgłaszany, `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="823ee-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="823ee-120">Wyrażenie, które zawiera `dyn` nie jest sprawdzana w czasie kompilacji, ponieważ typ `dyn` jest `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="823ee-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

## <a name="context"></a><span data-ttu-id="823ee-121">Kontekst</span><span class="sxs-lookup"><span data-stu-id="823ee-121">Context</span></span>

<span data-ttu-id="823ee-122">`dynamic` — Słowo kluczowe może znajdować się bezpośrednio lub jako składnik skonstruowanego typu w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="823ee-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>

- <span data-ttu-id="823ee-123">W deklaracjach typu właściwości, pola, indeksowanie, parametr zwracają wartość, zmienna lokalna lub typ ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="823ee-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="823ee-124">Następujące klasy definicja używa `dynamic` w kilku różnych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="823ee-124">The following class definition uses `dynamic` in several different declarations.</span></span>

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- <span data-ttu-id="823ee-125">W jawnych konwersji typów, jako typ docelowy konwersji.</span><span class="sxs-lookup"><span data-stu-id="823ee-125">In explicit type conversions, as the target type of a conversion.</span></span>

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- <span data-ttu-id="823ee-126">W dowolnym kontekście, gdy typy służyć jako wartości, takich jak na prawej krawędzi `is` operatora lub `as` operatora, lub jako argument `typeof` jako część skonstruowanego typu.</span><span class="sxs-lookup"><span data-stu-id="823ee-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="823ee-127">Na przykład `dynamic` mogą być używane w następujących wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="823ee-127">For example, `dynamic` can be used in the following expressions.</span></span>

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a><span data-ttu-id="823ee-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="823ee-128">Example</span></span>

<span data-ttu-id="823ee-129">W poniższym przykładzie użyto `dynamic` w kilka deklaracji.</span><span class="sxs-lookup"><span data-stu-id="823ee-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="823ee-130">`Main` Metoda również zachowanie różni się od typu w czasie kompilacji sprawdzania ze sprawdzaniem typu run-time.</span><span class="sxs-lookup"><span data-stu-id="823ee-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

<span data-ttu-id="823ee-131">Aby uzyskać więcej informacji i przykładów, zobacz [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="823ee-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="823ee-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="823ee-132">See also</span></span>

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
- [<span data-ttu-id="823ee-133">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="823ee-133">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [<span data-ttu-id="823ee-134">object</span><span class="sxs-lookup"><span data-stu-id="823ee-134">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
- [<span data-ttu-id="823ee-135">is</span><span class="sxs-lookup"><span data-stu-id="823ee-135">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="823ee-136">as</span><span class="sxs-lookup"><span data-stu-id="823ee-136">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
- [<span data-ttu-id="823ee-137">typeof</span><span class="sxs-lookup"><span data-stu-id="823ee-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
- [<span data-ttu-id="823ee-138">Instrukcje: Bezpieczne rzutowanie za pomocą dopasowywania do wzorca, jak i operatory</span><span class="sxs-lookup"><span data-stu-id="823ee-138">How to: Safely cast Using pattern matching, as, and is Operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)  
- [<span data-ttu-id="823ee-139">Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie</span><span class="sxs-lookup"><span data-stu-id="823ee-139">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
