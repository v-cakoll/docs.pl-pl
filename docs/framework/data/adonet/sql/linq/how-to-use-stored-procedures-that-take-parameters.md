---
title: 'Instrukcje: Używanie procedur składowanych, które przyjmują parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 8dd463c895efcddfe288fe1dc8571981872d9d80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181769"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Instrukcje: Używanie procedur składowanych, które przyjmują parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje parametry wyjściowe można odwoływać się do parametrów, a dla typów wartości deklaruje parametr jako dopuszczającego wartość null.  
  
 Na przykład sposobu używania parametru wejściowego w zapytaniu, które zwraca zestawu wierszy zobacz [jak: Zwracane zestawy wierszy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przyjmuje jeden parametr wejściowy (identyfikator klienta) i zwraca wartość parametru wyjściowego (łączna sprzedaż dla tego klienta).  
  
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
 Możesz wywołać tę procedurę składowaną w następujący sposób:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Używanie typów dopuszczających wartości null](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Typy wartości dopuszczających wartości null](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
