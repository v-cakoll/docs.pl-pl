---
title: Kwerenda dotycząca kolekcji obiektów (LINQ w C#)
description: Dowiedz się, jak wykonać zapytanie względem kolekcji za pomocą LINQ w C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 7bc59e7009f9ae8d8f66c24e9519d9100404c9c4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511387"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="e478d-103">Kwerenda dotycząca kolekcji obiektów</span><span class="sxs-lookup"><span data-stu-id="e478d-103">Query a collection of objects</span></span>

<span data-ttu-id="e478d-104">W tym przykładzie przedstawiono sposób wykonania prostego zapytania za pośrednictwem listy `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="e478d-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="e478d-105">Każdy `Student` obiekt zawiera niektóre podstawowe informacje o studenta i listę, która reprezentuje ocen studenta w czterech badań.</span><span class="sxs-lookup"><span data-stu-id="e478d-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="e478d-106">Ta aplikacja służy jako umożliwiająca wiele innych przykładów w tej sekcji, które używały tych samych `students` źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e478d-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e478d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e478d-107">Example</span></span>

<span data-ttu-id="e478d-108">Następujące zapytanie zwraca studentów, którzy otrzymali wynik 90 lub nowszej na ich pierwsze egzamin.</span><span class="sxs-lookup"><span data-stu-id="e478d-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="e478d-109">To zapytanie jest celowo proste umożliwiające eksperymentować.</span><span class="sxs-lookup"><span data-stu-id="e478d-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="e478d-110">Na przykład, możesz spróbować więcej warunków w `where` klauzulę lub użyj `orderby` klauzulę, aby posortować wyniki.</span><span class="sxs-lookup"><span data-stu-id="e478d-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e478d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e478d-111">See also</span></span>

- [<span data-ttu-id="e478d-112">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e478d-112">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="e478d-113">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="e478d-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)