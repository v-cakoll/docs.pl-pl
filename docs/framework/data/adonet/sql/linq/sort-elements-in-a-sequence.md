---
title: Sortowanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: f6f112a63dd976a1d6ae91f2fafd6678a9f40846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945087"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="2854e-102">Sortowanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="2854e-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="2854e-103">Użyj operatora <xref:System.Linq.Enumerable.OrderBy%2A> , aby posortować sekwencję według jednego lub kilku kluczy.</span><span class="sxs-lookup"><span data-stu-id="2854e-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2854e-104">Program jest przeznaczony do obsługi porządkowania według prostych typów pierwotnych, `string`takich `int`jak,, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="2854e-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="2854e-105">Nie obsługuje porządkowania złożonych klas wielowartościowych, takich jak typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="2854e-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="2854e-106">Nie obsługuje `byte` również typów danych.</span><span class="sxs-lookup"><span data-stu-id="2854e-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2854e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2854e-107">Example</span></span>  
 <span data-ttu-id="2854e-108">Poniższy przykład sortuje `Employees` według daty zatrudnienia.</span><span class="sxs-lookup"><span data-stu-id="2854e-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="2854e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2854e-109">Example</span></span>  
 <span data-ttu-id="2854e-110">Poniższy przykład używa `where` do sortowania `Orders` danych wysłanych `London` przez fracht.</span><span class="sxs-lookup"><span data-stu-id="2854e-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="2854e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2854e-111">Example</span></span>  
 <span data-ttu-id="2854e-112">Poniższy przykład sortuje `Products` według ceny jednostkowej od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="2854e-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="2854e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="2854e-113">Example</span></span>  
 <span data-ttu-id="2854e-114">Poniższy przykład używa mieszanki `OrderBy` do sortowania `Customers` według miejscowości, a następnie według nazwy kontaktu.</span><span class="sxs-lookup"><span data-stu-id="2854e-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="2854e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2854e-115">Example</span></span>  
 <span data-ttu-id="2854e-116">Poniższy przykład sortuje zamówienia od `EmployeeID 1` przez `ShipCountry`, a następnie według najwyższego do najniższego frachtu.</span><span class="sxs-lookup"><span data-stu-id="2854e-116">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="2854e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="2854e-117">Example</span></span>  
 <span data-ttu-id="2854e-118">Poniższy przykład łączy <xref:System.Linq.Enumerable.OrderBy%2A>operatory, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.GroupBy%2A> i, aby znaleźć, żemająnajwyższącenęjednostkowąwkażdejkategorii,anastępniesortujewedługidentyfikatorakategoriiGrupujwedług.`Products`</span><span class="sxs-lookup"><span data-stu-id="2854e-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="2854e-119">W przypadku uruchomienia poprzedniego zapytania względem przykładowej bazy danych Northwind wyniki będą wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="2854e-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="2854e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2854e-120">See also</span></span>

- [<span data-ttu-id="2854e-121">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="2854e-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="2854e-122">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="2854e-122">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
