---
title: Obsługa wartości zerowych w wyrażeniach zapytań (LINQ w C#)
description: Dowiedz się, jak Obsługa wartości zerowych w wyrażeniach zapytań LINQ w C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 14609aee2bbd1fbb487589bb41683a1f3cad1362
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857570"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="60a29-103">Obsługa wartości zerowych w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="60a29-103">Handle null values in query expressions</span></span>

<span data-ttu-id="60a29-104">Ten przykład przedstawia sposób obsługi możliwych wartości null w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="60a29-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="60a29-105">Kolekcja obiektów, takich jak <xref:System.Collections.Generic.IEnumerable%601> może zawierać elementy, których wartość jest [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="60a29-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="60a29-106">Jeśli kolekcja źródłowa jest pusta lub zawiera element, którego wartość jest równa null, a zapytanie nie obsługuje wartości null, <xref:System.NullReferenceException> zostanie zgłoszony podczas wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="60a29-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="60a29-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="60a29-107">Example</span></span>

<span data-ttu-id="60a29-108">Możesz tworzyć kod pamiętać o uniknąć wyjątek pustej referencji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="60a29-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="60a29-109">W poprzednim przykładzie `where` klauzuli odfiltrowuje wszystkie elementy o wartości null w sekwencji kategorii.</span><span class="sxs-lookup"><span data-stu-id="60a29-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="60a29-110">Ta technika jest niezależny od sprawdzanie wartości null w klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="60a29-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="60a29-111">Wyrażenie warunkowe z wartością null, w tym przykładzie działa, ponieważ `Products.CategoryID` typu `int?` co jest skrótem `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="60a29-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="60a29-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="60a29-112">Example</span></span>

<span data-ttu-id="60a29-113">W klauzuli join jeśli tylko jeden z kluczy porównania jest typem wartościowym, można rzutować z drugiej strony do typu dopuszczającego wartość null w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="60a29-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="60a29-114">W poniższym przykładzie przyjęto założenie, że `EmployeeID` to kolumna, która zawiera wartości typu `int?`:</span><span class="sxs-lookup"><span data-stu-id="60a29-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="60a29-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60a29-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="60a29-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="60a29-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="60a29-117">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="60a29-117">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
