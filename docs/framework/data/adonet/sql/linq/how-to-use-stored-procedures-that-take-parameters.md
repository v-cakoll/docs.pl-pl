---
title: 'Porady: Użyj procedur składowanych, które przyjmują parametrów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: d1c9337f59b8cf218b9d2ab8fe4cf21afd2da689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353514"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Porady: Użyj procedur składowanych, które przyjmują parametrów
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje parametry wyjściowe do odwołania do parametrów, a dla typów wartości deklaruje parametr jako wartości null.  
  
 Na przykład sposobu używania parametru wejściowego w zapytaniu, które zwraca zestawu wierszy zobacz [porady: zwracać zestawów wierszy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przyjmuje jeden parametr wejściowy (identyfikator klienta) i zwraca parametrem out (łączna sprzedaż dla tego klienta).  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a>Przykład  
 Tę procedurę składowaną spowodowałoby wywołanie w następujący sposób:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Używanie typów dopuszczających wartości null](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Typy wartości dopuszczających wartości null](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
