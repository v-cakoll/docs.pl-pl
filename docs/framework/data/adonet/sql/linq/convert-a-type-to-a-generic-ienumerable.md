---
title: Konwertowanie typu do ogólnego interfejsu IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d1f4c1c4a561c893b5846e6ae0b08b2d78c3589d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509600"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="b9216-102">Konwertowanie typu do ogólnego interfejsu IEnumerable</span><span class="sxs-lookup"><span data-stu-id="b9216-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="b9216-103">Użyj <xref:System.Linq.Enumerable.AsEnumerable%2A> być zwracany argument wpisanych w formie ogólnego `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="b9216-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9216-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9216-104">Example</span></span>  
 <span data-ttu-id="b9216-105">W tym przykładzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (przy użyciu domyślnego ogólnego `Query`) spróbuje przekonwertować kwerendy do bazy danych SQL, a następnie uruchomić go na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b9216-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="b9216-106">Ale `where` klauzuli odwołuje się do metody zdefiniowanej przez użytkownika po stronie klienta (`isValidProduct`), której nie można skonwertować do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="b9216-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="b9216-107">To rozwiązanie jest określenie ogólnego klienta <xref:System.Collections.Generic.IEnumerable%601> implementacji `where` do zastąpienia ogólnego <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="b9216-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="b9216-108">Można to zrobić, wywołując <xref:System.Linq.Enumerable.AsEnumerable%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="b9216-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="b9216-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9216-109">See also</span></span>
- [<span data-ttu-id="b9216-110">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="b9216-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
