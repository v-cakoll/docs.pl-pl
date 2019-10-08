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
# <a name="how-to-return-rowsets"></a>Instrukcje: zwracanie zestawów wierszy
Ten przykład zwraca zestaw wierszy z bazy danych i zawiera parametr wejściowy do filtrowania wyniku.  
  
 Podczas wykonywania procedury składowanej, która zwraca zestaw wierszy, należy użyć klasy *wynik* , która przechowuje zwrot z procedury składowanej. Aby uzyskać więcej informacji, zobacz [analizowanie LINQ to SQL kodzie źródłowym](analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład reprezentuje procedurę przechowywaną, która zwraca wiersze klientów i używa parametru wejściowego do zwrócenia tylko tych wierszy, które mają nazwę "Londyn" jako miasto klienta. W przykładzie przyjęto założenie wyliczalnej klasy `CustomersByCityResult`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](stored-procedures.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
