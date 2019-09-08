---
title: 'Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 2112600dfcef65b1c85445b03806ce8e9cab6a27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782055"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="9e2db-102">Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="9e2db-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="9e2db-103"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Użyj metody, aby określić, które dane związane z głównym miejscem docelowym powinny być pobierane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="9e2db-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="9e2db-104">Jeśli na przykład wiesz, że potrzebujesz informacji o zamówieniach klientów, możesz użyć <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> programu, aby upewnić się, że informacje o zamówieniach są pobierane w tym samym czasie co informacje o kliencie.</span><span class="sxs-lookup"><span data-stu-id="9e2db-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="9e2db-105">To podejście powoduje tylko jedną podróż do bazy danych dla obu zestawów informacji.</span><span class="sxs-lookup"><span data-stu-id="9e2db-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e2db-106">Dane związane z głównym celem zapytania można pobrać, pobierając jeden z wielu produktów, takich jak pobieranie zamówień w przypadku docelowych klientów.</span><span class="sxs-lookup"><span data-stu-id="9e2db-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="9e2db-107">Ale takie podejście często ma wady.</span><span class="sxs-lookup"><span data-stu-id="9e2db-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="9e2db-108">Na przykład wyniki są tylko projekcjami, a nie jednostkami, które mogą być zmieniane i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]utrwalane przez program.</span><span class="sxs-lookup"><span data-stu-id="9e2db-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="9e2db-109">Możesz też pobrać wiele niepotrzebnych danych.</span><span class="sxs-lookup"><span data-stu-id="9e2db-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e2db-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e2db-110">Example</span></span>  
 <span data-ttu-id="9e2db-111">W poniższym przykładzie wszystkie `Orders` dla `Customers` wszystkich osób, które znajdują się w Londynie, są pobierane po wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="9e2db-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="9e2db-112">W efekcie dostęp do `Orders` właściwości `Customer` na obiekcie nie wyzwala nowej kwerendy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9e2db-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9e2db-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e2db-113">See also</span></span>

- [<span data-ttu-id="9e2db-114">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="9e2db-114">Querying the Database</span></span>](querying-the-database.md)
