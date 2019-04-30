---
title: Kwerenda dotycząca kolekcji obiektów (LINQ w C#)
description: Dowiedz się, jak wykonać zapytanie względem kolekcji za pomocą LINQ w C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659816"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="b6236-103">Zapytanie dotyczące kolekcji obiektów</span><span class="sxs-lookup"><span data-stu-id="b6236-103">Query a collection of objects</span></span>

<span data-ttu-id="b6236-104">W tym przykładzie przedstawiono sposób wykonania prostego zapytania za pośrednictwem listy `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="b6236-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="b6236-105">Każdy `Student` obiekt zawiera niektóre podstawowe informacje o studenta i listę, która reprezentuje ocen studenta w czterech badań.</span><span class="sxs-lookup"><span data-stu-id="b6236-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="b6236-106">Ta aplikacja służy jako umożliwiająca wiele innych przykładów w tej sekcji, które używały tych samych `students` źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b6236-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6236-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6236-107">Example</span></span>

<span data-ttu-id="b6236-108">Następujące zapytanie zwraca studentów, którzy otrzymali wynik 90 lub nowszej na ich pierwsze egzamin.</span><span class="sxs-lookup"><span data-stu-id="b6236-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="b6236-109">To zapytanie jest celowo proste umożliwiające eksperymentować.</span><span class="sxs-lookup"><span data-stu-id="b6236-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="b6236-110">Na przykład, możesz spróbować więcej warunków w `where` klauzulę lub użyj `orderby` klauzulę, aby posortować wyniki.</span><span class="sxs-lookup"><span data-stu-id="b6236-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6236-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6236-111">See also</span></span>

- [<span data-ttu-id="b6236-112">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b6236-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="b6236-113">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="b6236-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
