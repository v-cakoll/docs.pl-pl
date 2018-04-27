---
title: Domyślna wartość wyrażenia (C# przewodnik programowania w języku)
description: Wyrażenia wartości domyślnej tworzy wartości domyślne dla dowolnego typu odwołanie lub typ wartości
ms.date: 04/25/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 174ac79c9e2c4a4e628816b1178d420ec7cfc809
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="8386d-103">Domyślna wartość wyrażenia (C# programowania przewodnik)</span><span class="sxs-lookup"><span data-stu-id="8386d-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="8386d-104">Wyrażenie wartości domyślnej `default(T)` daje wartość domyślna typu `T`.</span><span class="sxs-lookup"><span data-stu-id="8386d-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="8386d-105">W poniższej tabeli przedstawiono wartości, które są tworzone dla różnych typów:</span><span class="sxs-lookup"><span data-stu-id="8386d-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="8386d-106">Typ</span><span class="sxs-lookup"><span data-stu-id="8386d-106">Type</span></span>|<span data-ttu-id="8386d-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="8386d-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="8386d-108">dowolny typ odwołania</span><span class="sxs-lookup"><span data-stu-id="8386d-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="8386d-109">Typ wartości liczbowe</span><span class="sxs-lookup"><span data-stu-id="8386d-109">Numeric value type</span></span>|<span data-ttu-id="8386d-110">Zero</span><span class="sxs-lookup"><span data-stu-id="8386d-110">Zero</span></span>|
|[<span data-ttu-id="8386d-111">bool</span><span class="sxs-lookup"><span data-stu-id="8386d-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="8386d-112">char</span><span class="sxs-lookup"><span data-stu-id="8386d-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="8386d-113">enum</span><span class="sxs-lookup"><span data-stu-id="8386d-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="8386d-114">Wartość utworzonego przez wyrażenie `(E)0`, gdzie `E` to identyfikator wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8386d-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="8386d-115">struct</span><span class="sxs-lookup"><span data-stu-id="8386d-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="8386d-116">Wartość utworzonego przez ustawienie wartości wszystkich pól typu na ich wartości domyślne, a wszystkie odwołania pola typu do `null`.</span><span class="sxs-lookup"><span data-stu-id="8386d-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="8386d-117">Typ dopuszczający wartość null</span><span class="sxs-lookup"><span data-stu-id="8386d-117">Nullable type</span></span>|<span data-ttu-id="8386d-118">Wystąpienie, dla którego <xref:System.Nullable%601.HasValue%2A> właściwość jest `false` i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="8386d-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="8386d-119">Wyrażenia wartości domyślne są szczególnie przydatne w ogólne klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="8386d-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="8386d-120">Jak przypisać wartość domyślną typu sparametryzowane jest jeden problem, który pojawia się przy użyciu typów ogólnych `T` Jeśli nie znasz następujące wcześniej:</span><span class="sxs-lookup"><span data-stu-id="8386d-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="8386d-121">Czy `T` jest typem referencyjnym lub typem wartości.</span><span class="sxs-lookup"><span data-stu-id="8386d-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="8386d-122">Jeśli `T` jest typem wartości, czy jest wartość liczbowa lub struktury.</span><span class="sxs-lookup"><span data-stu-id="8386d-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="8386d-123">Podane zmiennej `t` sparametryzowane typu `T`, instrukcja `t = null` jest prawidłowy tylko jeśli `T` jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="8386d-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="8386d-124">Przypisanie `t = 0` działa tylko dla typów wartości liczbowe, ale nie dla struktury.</span><span class="sxs-lookup"><span data-stu-id="8386d-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="8386d-125">Aby rozwiązać, który, należy użyć wyrażenie wartości domyślnej:</span><span class="sxs-lookup"><span data-stu-id="8386d-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="8386d-126">`default(T)` Wyrażenie nie jest ograniczona do ogólne klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="8386d-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="8386d-127">Domyślna wartość wyrażenia może służyć z dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8386d-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="8386d-128">Dowolne z tych wyrażeń są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="8386d-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="8386d-129">Poniższy przykład z `GenericList<T>` klasa przedstawia sposób użycia `default(T)` operatora w klasie rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="8386d-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="8386d-130">Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="8386d-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="8386d-131">Domyślnie literału i wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="8386d-131">default literal and type inference</span></span>

<span data-ttu-id="8386d-132">Począwszy od C# 7.1, `default` literał może służyć do wyrażenia wartości domyślnej, gdy kompilator może wnioskować o typie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="8386d-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="8386d-133">`default` Literał tworzy taką samą wartość jak odpowiednik `default(T)` gdzie `T` jest wywnioskowany typ.</span><span class="sxs-lookup"><span data-stu-id="8386d-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="8386d-134">Może być kodu bardziej zwięzły zmniejszając nadmiarowość z typem deklarującym więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="8386d-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="8386d-135">`default` Literał mogą być używane w dowolnej z następujących lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="8386d-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="8386d-136">Inicjator zmiennej</span><span class="sxs-lookup"><span data-stu-id="8386d-136">variable initializer</span></span>
- <span data-ttu-id="8386d-137">przypisanie zmiennej</span><span class="sxs-lookup"><span data-stu-id="8386d-137">variable assignment</span></span>
- <span data-ttu-id="8386d-138">deklarowanie wartości domyślnej dla parametru opcjonalnego</span><span class="sxs-lookup"><span data-stu-id="8386d-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="8386d-139">udostępnia wartość argumentu wywołania — metoda</span><span class="sxs-lookup"><span data-stu-id="8386d-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="8386d-140">Zwraca instrukcji (lub wyrażenie w elemencie członkowskim zabudowanego wyrażenia)</span><span class="sxs-lookup"><span data-stu-id="8386d-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="8386d-141">W poniższym przykładzie pokazano wiele sposobów użycia `default` literał w wyrażeniu wartości domyślne:</span><span class="sxs-lookup"><span data-stu-id="8386d-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="8386d-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8386d-142">See also</span></span>

 <xref:System.Collections.Generic>  
 [<span data-ttu-id="8386d-143">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8386d-143">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="8386d-144">Typy ogólne (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="8386d-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)  
 [<span data-ttu-id="8386d-145">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="8386d-145">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="8386d-146">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="8386d-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="8386d-147">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="8386d-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
