---
title: New operator - C# odwołania
ms.custom: seodec18
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: ce3d39c42dc35ca3038fc38edd9327e9b96fb20f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633416"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="be296-102">New — operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="be296-102">new operator (C# Reference)</span></span>

<span data-ttu-id="be296-103">Używane do tworzenia obiektów i wywoływać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="be296-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="be296-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="be296-104">For example:</span></span>

```csharp
Class1 obj  = new Class1();
```

<span data-ttu-id="be296-105">Służy również do tworzenia wystąpień typów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="be296-105">It is also used to create instances of anonymous types:</span></span>

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

<span data-ttu-id="be296-106">`new` Operator jest również używany do wywoływania konstruktora bez parametrów dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="be296-106">The `new` operator is also used to invoke the parameterless constructor for value types.</span></span> <span data-ttu-id="be296-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="be296-107">For example:</span></span>

```csharp
int i = new int();
```

<span data-ttu-id="be296-108">W poprzednich instrukcji `i` jest inicjowany do `0`, która jest wartością domyślną dla typu `int`.</span><span class="sxs-lookup"><span data-stu-id="be296-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="be296-109">Wykonywanie instrukcji ma taki sam skutek jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="be296-109">The statement has the same effect as the following:</span></span>

```csharp
int i = 0;
```

<span data-ttu-id="be296-110">Aby uzyskać pełną listę wartości domyślnych, zobacz [tabela wartości domyślnych](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="be296-110">For a complete list of default values, see [Default Values Table](default-values-table.md).</span></span>

<span data-ttu-id="be296-111">Pamiętaj, że ma ona błędem jest deklaracja konstruktora bez parametrów dla [struktury](struct.md) ponieważ każdego typu wartości niejawnie ma publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="be296-111">Remember that it is an error to declare a parameterless constructor for a [struct](struct.md) because every value type implicitly has a public parameterless constructor.</span></span> <span data-ttu-id="be296-112">Istnieje możliwość zadeklarować konstruktory sparametryzowane w typie struct, można ustawić wartości początkowej, ale tylko jest to konieczne, jeśli wymagane są wartości innej niż domyślna.</span><span class="sxs-lookup"><span data-stu-id="be296-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>

<span data-ttu-id="be296-113">Typ odwołania obiektów, takich jak klasy i obiekty typu wartości, takie jak struktury są niszczone, automatycznie, ale obiekty typu wartości jest niszczony, kiedy ich zawierającego kontekstu jest niszczony, natomiast obiekty typu odwołania są niszczone, wyrzucanie elementów Moduł zbierający na nieokreślony czas, po usunięciu ostatniego odwołania do nich.</span><span class="sxs-lookup"><span data-stu-id="be296-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="be296-114">W przypadku typów, które zawierają zasoby, takie jak dojścia do plików lub połączeń sieciowych pożądane jest mogą wykorzystać deterministyczne cleanup, aby upewnić się, jak najszybciej zwolnienie zasobów, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="be296-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="be296-115">Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="be296-115">For more information, see [using Statement](using-statement.md).</span></span>

<span data-ttu-id="be296-116">Operator `new` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="be296-116">The `new` operator cannot be overloaded.</span></span>

<span data-ttu-id="be296-117">Jeśli `new` operator nie może przydzielić pamięci, zgłosi wyjątek, <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="be296-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="be296-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="be296-118">Example</span></span>

<span data-ttu-id="be296-119">W poniższym przykładzie `struct` obiektu i obiekt klasy są tworzone i inicjowane za pomocą `new` operatora, a następnie przypisać wartości.</span><span class="sxs-lookup"><span data-stu-id="be296-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="be296-120">Wartość domyślna i przypisane wartości są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="be296-120">The default and the assigned values are displayed.</span></span>

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

<span data-ttu-id="be296-121">Zwróć uwagę, w tym przykładzie jest wartością domyślną ciągu `null`.</span><span class="sxs-lookup"><span data-stu-id="be296-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="be296-122">W związku z tym nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="be296-122">Therefore, it is not displayed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="be296-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="be296-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="be296-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be296-124">See also</span></span>

- [<span data-ttu-id="be296-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="be296-125">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="be296-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="be296-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be296-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="be296-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="be296-128">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="be296-128">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="be296-129">new</span><span class="sxs-lookup"><span data-stu-id="be296-129">new</span></span>](new.md)
- [<span data-ttu-id="be296-130">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="be296-130">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
