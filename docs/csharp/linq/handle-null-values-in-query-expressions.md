---
title: Obsługa wartości null w wyrażeniach kwerendy (LINQ w języku C#)
description: Dowiedz się, jak obsługiwać wartości null w wyrażeniach zapytania LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 3da490b72bd518df7be8c14b34655af8c6f84929
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249308"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="a676b-103">Obsługa wartości null w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="a676b-103">Handle null values in query expressions</span></span>

<span data-ttu-id="a676b-104">W tym przykładzie pokazano, jak obsługiwać możliwe wartości null w kolekcjach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="a676b-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="a676b-105">Kolekcja obiektów, taka <xref:System.Collections.Generic.IEnumerable%601> jak może zawierać elementy, których wartość jest [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="a676b-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="a676b-106">Jeśli kolekcja źródło ma wartość null lub zawiera element, którego wartość jest <xref:System.NullReferenceException> null, a kwerenda nie obsługuje wartości null, zostanie ono odrzucone podczas wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="a676b-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="a676b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a676b-107">Example</span></span>

<span data-ttu-id="a676b-108">Można kodować defensywnie, aby uniknąć wyjątku odwołania null, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a676b-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="a676b-109">W poprzednim przykładzie `where` klauzula odfiltruje wszystkie elementy null w sekwencji kategorii.</span><span class="sxs-lookup"><span data-stu-id="a676b-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="a676b-110">Ta technika jest niezależna od sprawdzania wartości null w klauzuli sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="a676b-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="a676b-111">Wyrażenie warunkowe z null w `Products.CategoryID` tym przykładzie działa, ponieważ jest typu, `int?` który jest skrótem dla `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="a676b-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="a676b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a676b-112">Example</span></span>

<span data-ttu-id="a676b-113">W klauzuli sprzężenia, jeśli tylko jeden z kluczy porównania jest typem wartości możliwej do wartości null, można rzutować drugą do typu wartości możliwej do wartości null w wyrażeniu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="a676b-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable value type in the query expression.</span></span> <span data-ttu-id="a676b-114">W poniższym przykładzie `EmployeeID` załóżmy, że `int?`jest to kolumna zawierająca wartości typu:</span><span class="sxs-lookup"><span data-stu-id="a676b-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="a676b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a676b-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="a676b-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="a676b-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="a676b-117">Typy wartości możliwe do wartości null</span><span class="sxs-lookup"><span data-stu-id="a676b-117">Nullable value types</span></span>](../language-reference/builtin-types/nullable-value-types.md)
