---
title: 'Instrukcje: Używanie procedur składowanych, które przyjmują parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 4f2636d3bb248adbb6b912887012b0b9c246c590
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793072"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Instrukcje: Używanie procedur składowanych, które przyjmują parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje parametry wyjściowe do parametrów referencyjnych, a dla typów wartości deklaruje parametr jako wartość null.  
  
 Aby zapoznać się z przykładem użycia parametru wejściowego w zapytaniu, które zwraca zestaw wierszy, [zobacz How to: Zwróć zestawy wierszy](how-to-return-rowsets.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przyjmuje jeden parametr wejściowy (identyfikator klienta) i zwraca parametr out (całkowita sprzedaż dla tego klienta).  
  
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
 Tę procedurę składowaną należy wywołać w następujący sposób:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](stored-procedures.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
- [Używanie typów dopuszczających wartości null](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Typy wartości dopuszczających wartości null](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
