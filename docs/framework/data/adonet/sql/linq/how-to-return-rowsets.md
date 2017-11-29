---
title: "Porady: zwracać zestawy wierszy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 24211e82633e41256a8c801000c4d3e17d9d8612
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-rowsets"></a>Porady: zwracać zestawy wierszy
W tym przykładzie zwraca zestawu wierszy z bazy danych i zawiera parametru wejściowego przefiltrować wynik.  
  
 Podczas wykonywania procedury składowanej, która zwraca zestawu wierszy, użyj *wynik* klasy, która przechowuje zwraca z procedury składowanej. Aby uzyskać więcej informacji, zobacz [analizowanie LINQ do SQL kodu źródłowego](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia procedury przechowywanej, która zwraca wiersze klientów i użyto parametru wejściowego, aby zwrócić tylko tych wierszy wykazu "Londynie" jako miasto klienta. W przykładzie założono wyliczalny `CustomersByCityResult` klasy.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
