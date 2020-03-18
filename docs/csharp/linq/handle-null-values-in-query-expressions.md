---
title: Obsługa wartości null w wyrażeniach kwerendy (LINQ w języku C#)
description: Dowiedz się, jak obsługiwać wartości null w wyrażeniach kwerend LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73736855"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="2ac22-103">Obsługa wartości null w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="2ac22-103">Handle null values in query expressions</span></span>

<span data-ttu-id="2ac22-104">W tym przykładzie pokazano, jak obsługiwać możliwe wartości null w kolekcjach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="2ac22-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="2ac22-105">Kolekcja obiektów, takich <xref:System.Collections.Generic.IEnumerable%601> jak może zawierać elementy, których wartość jest [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="2ac22-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="2ac22-106">Jeśli kolekcja źródłowa ma wartość null lub zawiera element, którego wartość <xref:System.NullReferenceException> ma wartość null, a kwerenda nie obsługuje wartości null, podczas wykonywania kwerendy zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="2ac22-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="2ac22-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ac22-107">Example</span></span>

<span data-ttu-id="2ac22-108">Można kod defensywnie, aby uniknąć wyjątku odwołania zerowego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ac22-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="2ac22-109">W poprzednim przykładzie `where` klauzula odfiltrowuje wszystkie elementy null w sekwencji kategorii.</span><span class="sxs-lookup"><span data-stu-id="2ac22-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="2ac22-110">Ta technika jest niezależna od sprawdzania wartości null w klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="2ac22-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="2ac22-111">Wyrażenie warunkowe z null w `Products.CategoryID` tym przykładzie `int?` działa, ponieważ `Nullable<int>`jest typu, który jest skrótem dla .</span><span class="sxs-lookup"><span data-stu-id="2ac22-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="2ac22-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ac22-112">Example</span></span>

<span data-ttu-id="2ac22-113">W join klauzuli, jeśli tylko jeden z kluczy porównania jest typem wartości nullable, można rzutować drugi do typu nullable w wyrażeniu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="2ac22-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="2ac22-114">W poniższym przykładzie `EmployeeID` załóżmy, że jest `int?`to kolumna zawierająca wartości typu:</span><span class="sxs-lookup"><span data-stu-id="2ac22-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="2ac22-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ac22-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="2ac22-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2ac22-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="2ac22-117">Typy wartości z możliwością null</span><span class="sxs-lookup"><span data-stu-id="2ac22-117">Nullable value types</span></span>](../language-reference/builtin-types/nullable-value-types.md)
