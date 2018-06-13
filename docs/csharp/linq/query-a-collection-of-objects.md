---
title: Kwerenda dotycząca kolekcji obiektów
description: Jak zapytanie względem kolekcji.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: c690da2ae59d2a9b34a5bd403bc54797c4e95fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282395"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="cc2c3-103">Kwerenda dotycząca kolekcji obiektów</span><span class="sxs-lookup"><span data-stu-id="cc2c3-103">Query a collection of objects</span></span>
<span data-ttu-id="cc2c3-104">W tym przykładzie przedstawiono sposób wykonania prostego zapytania listy `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="cc2c3-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="cc2c3-105">Każdy `Student` obiektu zawiera niektóre podstawowe informacje o student i listę, która reprezentuje studentów w czterech badania.</span><span class="sxs-lookup"><span data-stu-id="cc2c3-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="cc2c3-106">Ta aplikacja służy jako platforma wiele innych przykładów w tej sekcji, które korzystają z jednego `students` źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cc2c3-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc2c3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc2c3-107">Example</span></span>  
 <span data-ttu-id="cc2c3-108">Następujące zapytanie zwraca studentów, którzy otrzymali wynikiem 90 lub większa na ich pierwsze egzaminu.</span><span class="sxs-lookup"><span data-stu-id="cc2c3-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="cc2c3-109">To zapytanie jest celowo proste do eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="cc2c3-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="cc2c3-110">Na przykład spróbujesz więcej warunków w `where` klauzulę lub użyj `orderby` klauzuli sortowania wyników.</span><span class="sxs-lookup"><span data-stu-id="cc2c3-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="cc2c3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc2c3-111">See also</span></span>  
 [<span data-ttu-id="cc2c3-112">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="cc2c3-112">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="cc2c3-113">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="cc2c3-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
