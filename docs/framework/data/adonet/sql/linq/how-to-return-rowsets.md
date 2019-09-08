---
title: 'Instrukcje: Zwracane zestawy wierszy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 5ec188e0345140297062d0a10dfbbc4a294bbb7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781607"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="18c37-102">Instrukcje: Zwracane zestawy wierszy</span><span class="sxs-lookup"><span data-stu-id="18c37-102">How to: Return Rowsets</span></span>
<span data-ttu-id="18c37-103">Ten przykład zwraca zestaw wierszy z bazy danych i zawiera parametr wejściowy do filtrowania wyniku.</span><span class="sxs-lookup"><span data-stu-id="18c37-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="18c37-104">Podczas wykonywania procedury składowanej, która zwraca zestaw wierszy, należy użyć klasy *wynik* , która przechowuje zwrot z procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="18c37-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="18c37-105">Aby uzyskać więcej informacji, zobacz [analizowanie LINQ to SQL kodzie źródłowym](analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="18c37-105">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18c37-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="18c37-106">Example</span></span>  
 <span data-ttu-id="18c37-107">Poniższy przykład reprezentuje procedurę przechowywaną, która zwraca wiersze klientów i używa parametru wejściowego do zwrócenia tylko tych wierszy, które mają nazwę "Londyn" jako miasto klienta.</span><span class="sxs-lookup"><span data-stu-id="18c37-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="18c37-108">W przykładzie przyjęto założenie klasy wyliczalnej `CustomersByCityResult` .</span><span class="sxs-lookup"><span data-stu-id="18c37-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="18c37-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18c37-109">See also</span></span>

- [<span data-ttu-id="18c37-110">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="18c37-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="18c37-111">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="18c37-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
