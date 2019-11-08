---
title: Obsługa wartości zerowych w wyrażeniach zapytań ( C#LINQ in)
description: Dowiedz się, jak obsłużyć wartości null w C#wyrażeniach zapytań LINQ w.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736855"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="9fe4e-103">Obsługa wartości null w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="9fe4e-103">Handle null values in query expressions</span></span>

<span data-ttu-id="9fe4e-104">Ten przykład pokazuje, jak obsługiwać możliwe wartości null w kolekcjach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="9fe4e-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="9fe4e-105">Kolekcja obiektów, taka jak <xref:System.Collections.Generic.IEnumerable%601>, może zawierać elementy, których wartość jest [równa null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="9fe4e-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="9fe4e-106">Jeśli kolekcja źródłowa ma wartość null lub zawiera element, którego wartość jest równa null, a zapytanie nie obsługuje wartości null, podczas wykonywania zapytania zostanie zgłoszone <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="9fe4e-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="9fe4e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9fe4e-107">Example</span></span>

<span data-ttu-id="9fe4e-108">Można odpowiednio zakodować, aby uniknąć wyjątku odwołania o wartości null, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9fe4e-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="9fe4e-109">W poprzednim przykładzie klauzula `where` filtruje wszystkie elementy null w sekwencji kategorii.</span><span class="sxs-lookup"><span data-stu-id="9fe4e-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="9fe4e-110">Ta technika jest niezależna od sprawdzania wartości null w klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="9fe4e-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="9fe4e-111">Wyrażenie warunkowe mające wartość null w tym przykładzie działa, ponieważ `Products.CategoryID` jest typu `int?`, który jest skrótem dla `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="9fe4e-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="9fe4e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9fe4e-112">Example</span></span>

<span data-ttu-id="9fe4e-113">W klauzuli join, jeśli tylko jeden z kluczy porównania jest typem wartości null, można rzutować inne do typu dopuszczającego wartość null w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="9fe4e-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="9fe4e-114">W poniższym przykładzie Załóżmy, że `EmployeeID` jest kolumną zawierającą wartości typu `int?`:</span><span class="sxs-lookup"><span data-stu-id="9fe4e-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="9fe4e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fe4e-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="9fe4e-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9fe4e-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="9fe4e-117">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="9fe4e-117">Nullable value types</span></span>](../language-reference/builtin-types/nullable-value-types.md)
