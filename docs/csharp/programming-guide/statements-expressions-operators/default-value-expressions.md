---
title: "Domyślna wartość wyrażenia (C# przewodnik programowania w języku)"
description: "Wyrażenia wartości domyślnej tworzy wartości domyślne dla dowolnego typu odwołanie lub typ wartości"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="6b422-103">Domyślna wartość wyrażenia (C# programowania przewodnik)</span><span class="sxs-lookup"><span data-stu-id="6b422-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="6b422-104">Wyrażenie wartości domyślnej powoduje wartością domyślną dla typu.</span><span class="sxs-lookup"><span data-stu-id="6b422-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="6b422-105">Wyrażenia wartości domyślne są szczególnie przydatne w ogólne klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="6b422-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="6b422-106">Jak przypisać wartości domyślnej z typem sparametryzowane jest jeden problem, który pojawia się przy użyciu typów ogólnych `T` Jeśli nie znasz następujące wcześniej:</span><span class="sxs-lookup"><span data-stu-id="6b422-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="6b422-107">Czy `T` jest typem referencyjnym lub typem wartości.</span><span class="sxs-lookup"><span data-stu-id="6b422-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="6b422-108">Jeśli `T` jest to typ wartości określa, czy jest wartość liczbowa lub struktury zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6b422-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="6b422-109">Podane zmiennej `t` sparametryzowane typu `T`, instrukcja `t = null` jest prawidłowy tylko jeśli `T` jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="6b422-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="6b422-110">Przypisanie `t = 0` działa tylko dla typów wartości liczbowe, ale nie dla struktury.</span><span class="sxs-lookup"><span data-stu-id="6b422-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="6b422-111">Rozwiązaniem jest użycie domyślne wyrażenie wartości, która zwraca `null` dla typów odwołań (typy klas i typów interfejsów) oraz zero dla typów wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="6b422-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="6b422-112">Struktury zdefiniowane przez użytkownika, zwraca struktury zainicjowany zero wzorca bitowego, która tworzy 0 lub `null` dla każdego elementu członkowskiego, w zależności od tego, czy ten element członkowski jest typem wartości lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="6b422-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="6b422-113">Dla typów wartości null `default` zwraca <xref:System.Nullable%601?displayProperty=nameWithType>, którego zainicjowano podobnie jak wszelkie struktury.</span><span class="sxs-lookup"><span data-stu-id="6b422-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=nameWithType>, which is initialized like any struct.</span></span>

<span data-ttu-id="6b422-114">`default(T)` Wyrażenie nie jest ograniczona do ogólne klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="6b422-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="6b422-115">Domyślna wartość wyrażenia może służyć z dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6b422-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="6b422-116">Dowolne z tych wyrażeń są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="6b422-116">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="6b422-117">Poniższy przykład z `GenericList<T>` klasa przedstawia sposób użycia `default(T)` operatora w klasie rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="6b422-117">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="6b422-118">Aby uzyskać więcej informacji, zobacz [ogólne omówienie](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="6b422-118">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="6b422-119">Domyślnie literału i wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="6b422-119">default literal and type inference</span></span>

<span data-ttu-id="6b422-120">Począwszy od C# 7.1, `default` literał może służyć do wyrażenia wartości domyślnej, gdy kompilator może wnioskować o typie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6b422-120">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="6b422-121">`default` Literał tworzy taką samą wartość jak odpowiednik `default(T)` gdzie `T` jest wywnioskowany typ.</span><span class="sxs-lookup"><span data-stu-id="6b422-121">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="6b422-122">Może być kodu bardziej zwięzły zmniejszając nadmiarowość z typem deklarującym więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="6b422-122">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="6b422-123">`default` Literał mogą być używane w dowolnej z następujących lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="6b422-123">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="6b422-124">Inicjator zmiennej</span><span class="sxs-lookup"><span data-stu-id="6b422-124">variable initializer</span></span>
- <span data-ttu-id="6b422-125">przypisanie zmiennej</span><span class="sxs-lookup"><span data-stu-id="6b422-125">variable assignment</span></span>
- <span data-ttu-id="6b422-126">deklarowanie wartości domyślnej dla parametru opcjonalnego</span><span class="sxs-lookup"><span data-stu-id="6b422-126">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="6b422-127">udostępnia wartość argumentu wywołania — metoda</span><span class="sxs-lookup"><span data-stu-id="6b422-127">providing the value for a method call argument</span></span>
- <span data-ttu-id="6b422-128">Zwraca instrukcji (lub wyrażenie w elemencie członkowskim zabudowanego wyrażenia)</span><span class="sxs-lookup"><span data-stu-id="6b422-128">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="6b422-129">W poniższym przykładzie pokazano wiele sposobów użycia `default` literał w wyrażeniu wartości domyślne:</span><span class="sxs-lookup"><span data-stu-id="6b422-129">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="6b422-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b422-130">See also</span></span>

 <span data-ttu-id="6b422-131"><xref:System.Collections.Generic>[Przewodnik programowania w języku C#](../index.md)</span><span class="sxs-lookup"><span data-stu-id="6b422-131"><xref:System.Collections.Generic> [C# Programming Guide](../index.md)</span></span>  
 [<span data-ttu-id="6b422-132">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="6b422-132">Generics</span></span>](../generics/index.md)  
 [<span data-ttu-id="6b422-133">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="6b422-133">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="6b422-134">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="6b422-134">Generics</span></span>](~/docs/standard/generics/index.md)  
