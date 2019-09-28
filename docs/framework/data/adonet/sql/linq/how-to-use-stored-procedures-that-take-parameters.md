---
title: 'Instrukcje: Używanie procedur składowanych, które przyjmują parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: c2b657f704d072b987578be5520a58d007ecac37
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353022"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Instrukcje: Używanie procedur składowanych, które przyjmują parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje parametry wyjściowe do parametrów referencyjnych, a dla typów wartości deklaruje parametr jako Nullable.  
  
 Aby zapoznać się z przykładem użycia parametru wejściowego w zapytaniu, które zwraca zestaw wierszy, zobacz [How: Zwracaj zestawy wierszy @ no__t-0.  
  
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
- [Używanie typów wartości null](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Typy wartości dopuszczających wartości null](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
