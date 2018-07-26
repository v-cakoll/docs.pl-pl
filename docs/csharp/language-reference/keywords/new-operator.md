---
title: new — Operator (odwołanie w C#)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243950"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="2a486-102">new — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2a486-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="2a486-103">Używane do tworzenia obiektów i wywoływać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="2a486-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="2a486-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="2a486-104">For example:</span></span>  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="2a486-105">Służy również do tworzenia wystąpień typów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="2a486-105">It is also used to create instances of anonymous types:</span></span>  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 <span data-ttu-id="2a486-106">`new` Operator jest również używany do wywoływania domyślnego konstruktora dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="2a486-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="2a486-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="2a486-107">For example:</span></span>  
  
```csharp
int i = new int();  
```  
  
 <span data-ttu-id="2a486-108">W poprzednich instrukcji `i` jest inicjowany do `0`, która jest wartością domyślną dla typu `int`.</span><span class="sxs-lookup"><span data-stu-id="2a486-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="2a486-109">Wykonywanie instrukcji ma taki sam skutek jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="2a486-109">The statement has the same effect as the following:</span></span>  
  
```csharp
int i = 0;  
```  
  
 <span data-ttu-id="2a486-110">Aby uzyskać pełną listę wartości domyślnych, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="2a486-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="2a486-111">Należy pamiętać, że jest błąd, aby zadeklarować Konstruktor domyślny dla [struktury](../../../csharp/language-reference/keywords/struct.md) ponieważ każdego typu wartości niejawnie ma publicznego konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="2a486-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="2a486-112">Istnieje możliwość zadeklarować konstruktory sparametryzowane w typie struct, można ustawić wartości początkowej, ale tylko jest to konieczne, jeśli wymagane są wartości innej niż domyślna.</span><span class="sxs-lookup"><span data-stu-id="2a486-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="2a486-113">Typ odwołania obiektów, takich jak klasy i obiekty typu wartości, takie jak struktury są niszczone, automatycznie, ale obiekty typu wartości jest niszczony, kiedy ich zawierającego kontekstu jest niszczony, natomiast obiekty typu odwołania są niszczone, wyrzucanie elementów Moduł zbierający na nieokreślony czas, po usunięciu ostatniego odwołania do nich.</span><span class="sxs-lookup"><span data-stu-id="2a486-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="2a486-114">W przypadku typów, które zawierają zasoby, takie jak dojścia do plików lub połączeń sieciowych pożądane jest mogą wykorzystać deterministyczne cleanup, aby upewnić się, jak najszybciej zwolnienie zasobów, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="2a486-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="2a486-115">Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2a486-115">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="2a486-116">Operator `new` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="2a486-116">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="2a486-117">Jeśli `new` operator nie może przydzielić pamięci, zgłosi wyjątek, <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="2a486-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a486-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a486-118">Example</span></span>  
 <span data-ttu-id="2a486-119">W poniższym przykładzie `struct` obiektu i obiekt klasy są tworzone i inicjowane za pomocą `new` operatora, a następnie przypisać wartości.</span><span class="sxs-lookup"><span data-stu-id="2a486-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="2a486-120">Wartość domyślna i przypisane wartości są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="2a486-120">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="2a486-121">Zwróć uwagę, w tym przykładzie jest wartością domyślną ciągu `null`.</span><span class="sxs-lookup"><span data-stu-id="2a486-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="2a486-122">W związku z tym nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="2a486-122">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2a486-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2a486-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2a486-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a486-124">See Also</span></span>  
 [<span data-ttu-id="2a486-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2a486-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2a486-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2a486-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2a486-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2a486-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2a486-128">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="2a486-128">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="2a486-129">new</span><span class="sxs-lookup"><span data-stu-id="2a486-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="2a486-130">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2a486-130">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
