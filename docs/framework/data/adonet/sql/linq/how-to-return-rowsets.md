---
title: 'Porady: zwracać zestawy wierszy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: a2666b752d936e10d377113d5bf18111393df3ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="7adcd-102">Porady: zwracać zestawy wierszy</span><span class="sxs-lookup"><span data-stu-id="7adcd-102">How to: Return Rowsets</span></span>
<span data-ttu-id="7adcd-103">W tym przykładzie zwraca zestawu wierszy z bazy danych i zawiera parametru wejściowego przefiltrować wynik.</span><span class="sxs-lookup"><span data-stu-id="7adcd-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="7adcd-104">Podczas wykonywania procedury składowanej, która zwraca zestawu wierszy, użyj *wynik* klasy, która przechowuje zwraca z procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="7adcd-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="7adcd-105">Aby uzyskać więcej informacji, zobacz [analizowanie LINQ do SQL kodu źródłowego](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="7adcd-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7adcd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7adcd-106">Example</span></span>  
 <span data-ttu-id="7adcd-107">Poniższy przykład przedstawia procedury przechowywanej, która zwraca wiersze klientów i użyto parametru wejściowego, aby zwrócić tylko tych wierszy wykazu "Londynie" jako miasto klienta.</span><span class="sxs-lookup"><span data-stu-id="7adcd-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="7adcd-108">W przykładzie założono wyliczalny `CustomersByCityResult` klasy.</span><span class="sxs-lookup"><span data-stu-id="7adcd-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7adcd-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7adcd-109">See Also</span></span>  
 [<span data-ttu-id="7adcd-110">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="7adcd-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [<span data-ttu-id="7adcd-111">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="7adcd-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
