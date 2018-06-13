---
title: Sortowanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 00c7a7a62890aced4c480e2653084c0b7cfe7f45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361961"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="0975b-102">Sortowanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="0975b-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="0975b-103">Użyj <xref:System.Linq.Enumerable.OrderBy%2A> operatora, aby posortować sekwencji zgodnie z co najmniej jeden klucz.</span><span class="sxs-lookup"><span data-stu-id="0975b-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0975b-104"> Służy do ustalania kolejności przez proste typy pierwotne, takie jak `string`, `int`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0975b-104"> is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="0975b-105">Nie obsługuje kolejności złożonych wielowartościowe klas, takich jak typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="0975b-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="0975b-106">Go nie obsługuje również `byte` typy danych.</span><span class="sxs-lookup"><span data-stu-id="0975b-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0975b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="0975b-107">Example</span></span>  
 <span data-ttu-id="0975b-108">Poniższy przykład sortuje `Employees` według daty zatrudnienia.</span><span class="sxs-lookup"><span data-stu-id="0975b-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="0975b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0975b-109">Example</span></span>  
 <span data-ttu-id="0975b-110">W poniższym przykładzie użyto `where` sortowania `Orders` dostarczona do `London` przez transport.</span><span class="sxs-lookup"><span data-stu-id="0975b-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="0975b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0975b-111">Example</span></span>  
 <span data-ttu-id="0975b-112">Poniższy przykład sortuje `Products` przez jednostkę ceny od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="0975b-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="0975b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0975b-113">Example</span></span>  
 <span data-ttu-id="0975b-114">W poniższym przykładzie użyto związek `OrderBy` sortowania `Customers` przez miasto, a następnie nazwisko osoby kontaktowej.</span><span class="sxs-lookup"><span data-stu-id="0975b-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="0975b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0975b-115">Example</span></span>  
 <span data-ttu-id="0975b-116">Poniższy przykład sortuje zamówień z `EmployeeID 1` przez kraj wysyłki, a następnie według kolejności malejącej transportu.</span><span class="sxs-lookup"><span data-stu-id="0975b-116">The following example sorts Orders from `EmployeeID 1` by ship-to country, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="0975b-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="0975b-117">Example</span></span>  
 <span data-ttu-id="0975b-118">Poniższy przykład łączy <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, i <xref:System.Linq.Enumerable.GroupBy%2A> operatorów można znaleźć `Products` ma najwyższy cenie jednostkowej w każdej kategorii, a następnie sortuje grupy według identyfikatora kategorii.</span><span class="sxs-lookup"><span data-stu-id="0975b-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="0975b-119">Jeśli poprzednie zapytanie wykonywane przykładowej bazy danych Northwind, wyniki będą wyglądać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0975b-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0975b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0975b-120">See Also</span></span>  
 [<span data-ttu-id="0975b-121">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="0975b-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="0975b-122">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="0975b-122">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
