---
title: 'Instrukcje: Zwracane zestawy wierszy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 599ad6f722251003ab56547ce050cbd0e8da831d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168717"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="ee309-102">Instrukcje: Zwracane zestawy wierszy</span><span class="sxs-lookup"><span data-stu-id="ee309-102">How to: Return Rowsets</span></span>
<span data-ttu-id="ee309-103">W tym przykładzie zwraca zestawu wierszy z bazy danych i zawiera parametr wejściowy do filtrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="ee309-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="ee309-104">Podczas wykonywania procedury składowanej, która zwraca zestawu wierszy, możesz użyć *wynik* klasy, która przechowuje zwraca z procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="ee309-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="ee309-105">Aby uzyskać więcej informacji, zobacz [analizowanie LINQ to SQL kod źródłowy](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="ee309-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee309-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee309-106">Example</span></span>  
 <span data-ttu-id="ee309-107">Poniższy przykład przedstawia procedury przechowywanej, która zwraca wiersze klientów i używa parametru wejściowego, aby zwrócić tylko wiersze z tej listy "Londyn", jak miasto klienta.</span><span class="sxs-lookup"><span data-stu-id="ee309-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="ee309-108">W przykładzie założono wyliczalny `CustomersByCityResult` klasy.</span><span class="sxs-lookup"><span data-stu-id="ee309-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee309-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee309-109">See also</span></span>

- [<span data-ttu-id="ee309-110">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="ee309-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [<span data-ttu-id="ee309-111">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="ee309-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
