---
title: Konwertowanie typu na ogólny interfejs IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c92f65c22fe4b4128a171c757bb9e9c0ccbc3fee
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247731"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="7e7f2-102">Konwertowanie typu na ogólny interfejs IEnumerable</span><span class="sxs-lookup"><span data-stu-id="7e7f2-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="7e7f2-103">Użyj <xref:System.Linq.Enumerable.AsEnumerable%2A> , aby zwrócić argument, który jest typem `IEnumerable`ogólnym.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e7f2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e7f2-104">Example</span></span>  
 <span data-ttu-id="7e7f2-105">W tym przykładzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (przy użyciu domyślnego generycznego `Query`) próba konwersji zapytania na SQL i wykonania go na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="7e7f2-106">Natomiast klauzula odwołuje się do zdefiniowanej przez użytkownika metody po stronie`isValidProduct`klienta (), której nie można przekonwertować na SQL. `where`</span><span class="sxs-lookup"><span data-stu-id="7e7f2-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="7e7f2-107">Rozwiązaniem jest określenie, że <xref:System.Collections.Generic.IEnumerable%601> `where` implementacja ogólna po stronie klienta zastąpi ogólny <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="7e7f2-108">W tym celu należy wycofać <xref:System.Linq.Enumerable.AsEnumerable%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="7e7f2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e7f2-109">See also</span></span>

- [<span data-ttu-id="7e7f2-110">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="7e7f2-110">Query Examples</span></span>](query-examples.md)
