---
title: "new — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="988c3-102">new — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="988c3-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="988c3-103">Używany do tworzenia obiektów i wywołania konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="988c3-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="988c3-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="988c3-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="988c3-105">Służy również do tworzenia wystąpień typów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="988c3-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="988c3-106">`new` Operator również służy do wywoływania domyślnego konstruktora dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="988c3-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="988c3-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="988c3-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="988c3-108">W powyższych instrukcji `i` jest ustawiana na `0`, która jest wartością domyślną dla typu `int`.</span><span class="sxs-lookup"><span data-stu-id="988c3-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="988c3-109">Instrukcja ma ten sam efekt w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="988c3-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="988c3-110">Aby uzyskać pełną listę wartości domyślne, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="988c3-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="988c3-111">Należy jednak pamiętać błędu, aby zadeklarować konstruktora domyślnego dla [struktury](../../../csharp/language-reference/keywords/struct.md) ponieważ każdy typ wartości niejawnie ma publicznego konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="988c3-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="988c3-112">Można zadeklarować konstruktory sparametryzowane w typie struktury można ustawić wartości początkowej, ale tylko jest to konieczne, jeśli są wymagane wartości innej niż domyślna.</span><span class="sxs-lookup"><span data-stu-id="988c3-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="988c3-113">Typ wartości obiektów, takich jak struktury są tworzone na stosie, gdy typ referencyjny obiektów, takich jak klasy są tworzone na stosie.</span><span class="sxs-lookup"><span data-stu-id="988c3-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="988c3-114">Obu typów obiektów zostaną zniszczone automatycznie, ale obiekty na podstawie typów wartości zostaną zniszczone, gdy przejdą poza zakresem, obiektów w oparciu o typy referencyjne zostaną zniszczone na czas nieokreślony, po usunięciu ostatniego odwołania do nich.</span><span class="sxs-lookup"><span data-stu-id="988c3-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="988c3-115">Typy odwołań używające stałej zasoby, takie jak duże ilości pamięci, dojścia do plików lub połączeń sieciowych czasami jest pożądane fragmentów finalizacja deterministyczna, aby upewnić się, że obiekt zostanie zniszczony tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="988c3-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="988c3-116">Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="988c3-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="988c3-117">`new` Operator nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="988c3-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="988c3-118">Jeśli `new` operator nie może przydzielić pamięci, zgłasza wyjątek, <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="988c3-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="988c3-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="988c3-119">Example</span></span>  
 <span data-ttu-id="988c3-120">W poniższym przykładzie `struct` utworzenia i zainicjowana przy użyciu obiektu i obiekt klasy `new` operatora, a następnie przypisać wartości.</span><span class="sxs-lookup"><span data-stu-id="988c3-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="988c3-121">Wartość domyślna i przypisane wartości są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="988c3-121">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="988c3-122">W przykładzie, który jest domyślna wartość ciągu `null`.</span><span class="sxs-lookup"><span data-stu-id="988c3-122">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="988c3-123">W związku z tym nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="988c3-123">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="988c3-124">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="988c3-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="988c3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="988c3-125">See Also</span></span>  
 [<span data-ttu-id="988c3-126">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="988c3-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="988c3-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="988c3-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="988c3-128">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="988c3-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="988c3-129">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="988c3-129">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="988c3-130">Nowy</span><span class="sxs-lookup"><span data-stu-id="988c3-130">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="988c3-131">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="988c3-131">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
