---
title: 'Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 342583cdbf6a1501f1bc70c6a9be5d7009c390eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940255"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="24d57-102">Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="24d57-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="24d57-103"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Użyj metody, aby określić, które dane związane z głównym miejscem docelowym powinny być pobierane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="24d57-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="24d57-104">Jeśli na przykład wiesz, że potrzebujesz informacji o zamówieniach klientów, możesz użyć <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> programu, aby upewnić się, że informacje o zamówieniach są pobierane w tym samym czasie co informacje o kliencie.</span><span class="sxs-lookup"><span data-stu-id="24d57-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="24d57-105">To podejście powoduje tylko jedną podróż do bazy danych dla obu zestawów informacji.</span><span class="sxs-lookup"><span data-stu-id="24d57-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24d57-106">Dane związane z głównym celem zapytania można pobrać, pobierając jeden z wielu produktów, takich jak pobieranie zamówień w przypadku docelowych klientów.</span><span class="sxs-lookup"><span data-stu-id="24d57-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="24d57-107">Ale takie podejście często ma wady.</span><span class="sxs-lookup"><span data-stu-id="24d57-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="24d57-108">Na przykład wyniki są tylko projekcjami, a nie jednostkami, które mogą być zmieniane i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]utrwalane przez program.</span><span class="sxs-lookup"><span data-stu-id="24d57-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="24d57-109">Możesz też pobrać wiele niepotrzebnych danych.</span><span class="sxs-lookup"><span data-stu-id="24d57-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24d57-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="24d57-110">Example</span></span>  
 <span data-ttu-id="24d57-111">W poniższym przykładzie wszystkie `Orders` dla `Customers` wszystkich osób, które znajdują się w Londynie, są pobierane po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="24d57-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="24d57-112">W efekcie dostęp do `Orders` właściwości `Customer` na obiekcie nie wyzwala nowej kwerendy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="24d57-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="24d57-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24d57-113">See also</span></span>

- [<span data-ttu-id="24d57-114">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="24d57-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
