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
# <a name="how-to-return-rowsets"></a>Instrukcje: Zwracane zestawy wierszy
Ten przykład zwraca zestaw wierszy z bazy danych i zawiera parametr wejściowy do filtrowania wyniku.  
  
 Podczas wykonywania procedury składowanej, która zwraca zestaw wierszy, należy użyć klasy *wynik* , która przechowuje zwrot z procedury składowanej. Aby uzyskać więcej informacji, zobacz [analizowanie LINQ to SQL kodzie źródłowym](analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład reprezentuje procedurę przechowywaną, która zwraca wiersze klientów i używa parametru wejściowego do zwrócenia tylko tych wierszy, które mają nazwę "Londyn" jako miasto klienta. W przykładzie przyjęto założenie klasy wyliczalnej `CustomersByCityResult` .  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](stored-procedures.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
