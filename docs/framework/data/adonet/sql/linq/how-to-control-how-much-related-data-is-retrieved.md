---
title: 'Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: dd59c09185eab003274614dcc30393b060e6b7c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904478"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="ec48a-102">Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="ec48a-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="ec48a-103">Użyj <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metodę, aby określić, które dane powiązane z głównym docelowej mają zostać pobrane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="ec48a-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="ec48a-104">Na przykład, jeśli wiesz, konieczne będą informacje dotyczące zamówień klientów, można użyć <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> aby upewnić się, że informacje o kolejności są pobierane w tym samym czasie jako informacje o kliencie.</span><span class="sxs-lookup"><span data-stu-id="ec48a-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="ec48a-105">To podejście powoduje tylko jeden podróży do bazy danych dla obu zestawów informacji.</span><span class="sxs-lookup"><span data-stu-id="ec48a-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec48a-106">Możesz pobrać dane związane z głównym celem zapytania, pobierając obejmujących wiele produktów jako jeden duży projekcji, takie jak pobieranie zamówień, gdy skierowane do klientów.</span><span class="sxs-lookup"><span data-stu-id="ec48a-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="ec48a-107">Jednak to podejście ma często wady.</span><span class="sxs-lookup"><span data-stu-id="ec48a-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="ec48a-108">Na przykład, wyniki są po prostu projekcje i nie jednostki, które można zmienić i utrwalone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec48a-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="ec48a-109">A może pobieranie dużej ilości danych, która nie ma potrzeby.</span><span class="sxs-lookup"><span data-stu-id="ec48a-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec48a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec48a-110">Example</span></span>  
 <span data-ttu-id="ec48a-111">W poniższym przykładzie wszystkie `Orders` dla wszystkich `Customers` kto znajdują się w Londynie są pobierane, gdy zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="ec48a-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="ec48a-112">Dzięki temu usługa następujących po sobie dostęp do `Orders` właściwość `Customer` obiektu nie wyzwalają nowej kwerendy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ec48a-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ec48a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec48a-113">See also</span></span>

- [<span data-ttu-id="ec48a-114">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="ec48a-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
