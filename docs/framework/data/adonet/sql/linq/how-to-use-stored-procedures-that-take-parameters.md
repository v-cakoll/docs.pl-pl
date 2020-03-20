---
title: 'Instrukcje: Używanie procedur składowanych, które przyjmują parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 05ecc467f75fbeda785b4bac1c3b8b1ceeb173b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174332"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Instrukcje: Używanie procedur składowanych, które przyjmują parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje parametry wyjściowe do parametrów referencyjnych, a dla typów wartości deklaruje parametr jako nullable.  
  
 Na przykład, jak używać parametru wejściowego w kwerendzie zwracającej zestaw wierszy, zobacz [Jak: Zwracanie zestawów wierszy](how-to-return-rowsets.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przyjmuje jeden parametr wejściowy (identyfikator odbiorcy) i zwraca parametr out (całkowita sprzedaż dla tego odbiorcy).  
  
```sql
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
 Tę procedurę składowaną można wywołać w następujący sposób:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Procedury przechowywane](stored-procedures.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
- [Typy wartości z dopuszczalną wartości (C#)](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [Typy o wartości zerowalnej (Visual Basic)](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
