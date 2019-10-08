---
title: 'Instrukcje: zwracanie zestawów wierszy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b853a6f2175009cbcbc01c14a6732b98e37e1a7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003064"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="ade62-102">Instrukcje: zwracanie zestawów wierszy</span><span class="sxs-lookup"><span data-stu-id="ade62-102">How to: Return Rowsets</span></span>
<span data-ttu-id="ade62-103">Ten przykład zwraca zestaw wierszy z bazy danych i zawiera parametr wejściowy do filtrowania wyniku.</span><span class="sxs-lookup"><span data-stu-id="ade62-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="ade62-104">Podczas wykonywania procedury składowanej, która zwraca zestaw wierszy, należy użyć klasy *wynik* , która przechowuje zwrot z procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="ade62-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="ade62-105">Aby uzyskać więcej informacji, zobacz [analizowanie LINQ to SQL kodzie źródłowym](analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="ade62-105">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ade62-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ade62-106">Example</span></span>  
 <span data-ttu-id="ade62-107">Poniższy przykład reprezentuje procedurę przechowywaną, która zwraca wiersze klientów i używa parametru wejściowego do zwrócenia tylko tych wierszy, które mają nazwę "Londyn" jako miasto klienta.</span><span class="sxs-lookup"><span data-stu-id="ade62-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="ade62-108">W przykładzie przyjęto założenie wyliczalnej klasy `CustomersByCityResult`.</span><span class="sxs-lookup"><span data-stu-id="ade62-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```sql  
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
  
## <a name="see-also"></a><span data-ttu-id="ade62-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ade62-109">See also</span></span>

- [<span data-ttu-id="ade62-110">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="ade62-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="ade62-111">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="ade62-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
