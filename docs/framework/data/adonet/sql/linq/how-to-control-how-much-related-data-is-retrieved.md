---
title: 'Porady: kontrolowanie, ile powiązane dane są pobierane'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 202e33f3130e8db7269af2b4669690cf5c6468cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="01ff3-102">Porady: kontrolowanie, ile powiązane dane są pobierane</span><span class="sxs-lookup"><span data-stu-id="01ff3-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="01ff3-103">Użyj <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metodę, aby określić, które dane powiązane z urządzenie docelowe głównej powinny zostać pobrane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="01ff3-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="01ff3-104">Na przykład jeśli wiadomo, konieczne będą informacje dotyczące zamówienia klientów, można użyć <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> aby upewnić się, że informacje o kolejności są pobierane w tym samym czasie jako informacje o kliencie.</span><span class="sxs-lookup"><span data-stu-id="01ff3-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="01ff3-105">Ta metoda powoduje podróży tylko jeden do bazy danych w obu zestawach danych.</span><span class="sxs-lookup"><span data-stu-id="01ff3-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01ff3-106">Można pobrać danych związanych z głównym celem kwerendy, pobierając iloczyn wektorowy jako jeden duży projekcji, takie jak pobieranie zamówienia, jeśli zostanie rozpoczęta dla klientów.</span><span class="sxs-lookup"><span data-stu-id="01ff3-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="01ff3-107">Jednak takie podejście charakteryzuje się często wady.</span><span class="sxs-lookup"><span data-stu-id="01ff3-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="01ff3-108">Na przykład, wyniki są po prostu projekcje i nie jednostek, które można zmienić i utrwalone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01ff3-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="01ff3-109">I może być pobierania duże ilości danych, która nie ma potrzeby.</span><span class="sxs-lookup"><span data-stu-id="01ff3-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ff3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="01ff3-110">Example</span></span>  
 <span data-ttu-id="01ff3-111">W poniższym przykładzie wszystkie `Orders` dla wszystkich `Customers` kto znajdują się w Londynie są pobierane, gdy zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="01ff3-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="01ff3-112">W rezultacie, kolejne dostęp do `Orders` właściwość `Customer` obiektu nie spowoduje wyzwolenia Nowa kwerenda bazy danych.</span><span class="sxs-lookup"><span data-stu-id="01ff3-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="01ff3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01ff3-113">See Also</span></span>  
 [<span data-ttu-id="01ff3-114">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="01ff3-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
