---
title: Kwerenda kolekcji obiektów (LINQ w języku C#)
description: Dowiedz się, jak kolekcje zapytań przy użyciu LINQ w języku C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659816"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="7d9fb-103">Zapytanie dotyczące kolekcji obiektów</span><span class="sxs-lookup"><span data-stu-id="7d9fb-103">Query a collection of objects</span></span>

<span data-ttu-id="7d9fb-104">W tym przykładzie pokazano, jak wykonać `Student` prostą kwerendę za pomocą listy obiektów.</span><span class="sxs-lookup"><span data-stu-id="7d9fb-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="7d9fb-105">Każdy `Student` obiekt zawiera podstawowe informacje o uczniu i listę, która reprezentuje wyniki ucznia na czterech egzaminach.</span><span class="sxs-lookup"><span data-stu-id="7d9fb-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="7d9fb-106">Ta aplikacja służy jako ramy dla wielu innych przykładów `students` w tej sekcji, które używają tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7d9fb-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d9fb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d9fb-107">Example</span></span>

<span data-ttu-id="7d9fb-108">Następujące zapytanie zwraca uczniom, którzy otrzymali wynik 90 lub więcej na pierwszym egzaminie.</span><span class="sxs-lookup"><span data-stu-id="7d9fb-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="7d9fb-109">Ta kwerenda jest celowo proste, aby umożliwić eksperymentowanie.</span><span class="sxs-lookup"><span data-stu-id="7d9fb-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="7d9fb-110">Na przykład można spróbować więcej `where` warunków w klauzuli lub użyć `orderby` klauzuli do sortowania wyników.</span><span class="sxs-lookup"><span data-stu-id="7d9fb-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9fb-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d9fb-111">See also</span></span>

- [<span data-ttu-id="7d9fb-112">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7d9fb-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="7d9fb-113">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="7d9fb-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
