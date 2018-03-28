---
title: Kwerenda dotycząca kolekcji obiektów
description: Jak zapytanie względem kolekcji.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: a62e5c6324d15376f1b42ad078eeb883b05ef14f
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="0745f-104">Kwerenda dotycząca kolekcji obiektów</span><span class="sxs-lookup"><span data-stu-id="0745f-104">Query a collection of objects</span></span>
<span data-ttu-id="0745f-105">W tym przykładzie przedstawiono sposób wykonania prostego zapytania listy `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="0745f-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="0745f-106">Każdy `Student` obiektu zawiera niektóre podstawowe informacje o student i listę, która reprezentuje studentów w czterech badania.</span><span class="sxs-lookup"><span data-stu-id="0745f-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="0745f-107">Ta aplikacja służy jako platforma wiele innych przykładów w tej sekcji, które korzystają z jednego `students` źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0745f-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0745f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0745f-108">Example</span></span>  
 <span data-ttu-id="0745f-109">Następujące zapytanie zwraca studentów, którzy otrzymali wynikiem 90 lub większa na ich pierwsze egzaminu.</span><span class="sxs-lookup"><span data-stu-id="0745f-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="0745f-110">To zapytanie jest celowo proste do eksperymentu.</span><span class="sxs-lookup"><span data-stu-id="0745f-110">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="0745f-111">Na przykład spróbujesz więcej warunków w `where` klauzulę lub użyj `orderby` klauzuli sortowania wyników.</span><span class="sxs-lookup"><span data-stu-id="0745f-111">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="0745f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0745f-112">See also</span></span>  
 [<span data-ttu-id="0745f-113">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="0745f-113">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="0745f-114">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="0745f-114">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
