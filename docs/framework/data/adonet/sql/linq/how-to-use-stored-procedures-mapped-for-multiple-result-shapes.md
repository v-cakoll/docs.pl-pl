---
title: 'Instrukcje: Używanie procedur składowanych zamapowanych na wiele kształtów wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: d32faf026789923ca4343271c9fd1b6bbdb068df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793094"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Instrukcje: Używanie procedur składowanych zamapowanych na wiele kształtów wyników
Gdy procedura składowana może zwracać wiele kształtów wyników, typ zwracany nie może być jednoznacznie wpisany do pojedynczego kształtu projekcji. Chociaż [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program może generować wszystkie możliwe typy projekcji, nie może znać kolejności, w której zostaną zwrócone.  
  
 Ten scenariusz należy wykonać z procedurami składowanymi, które tworzą sekwencyjnie wiele kształtów wynikowych. Aby uzyskać więcej informacji, zobacz [jak: Użyj procedur składowanych mapowanych na sekwencyjne kształty](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)wynikowe.  
  
 Ten <xref:System.Data.Linq.Mapping.ResultTypeAttribute> atrybut jest stosowany do procedur składowanych, które zwracają wiele typów wyników, aby określić zestaw typów, które może zwracać procedura.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu SQL kształt wynik zależy od danych wejściowych (`shape =1` lub `shape = 2`). Nie wiesz, która projekcja zostanie najpierw zwrócona.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Przykład  
 Aby wykonać tę procedurę składowaną, należy użyć kodu podobnego do poniższego.  
  
> [!NOTE]
> Aby uzyskać moduł wyliczający poprawnego typu, należy użyć <xref:System.Data.Linq.IMultipleResults.GetResult%2A> wzorca w zależności od wiedzy procedury składowanej.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](stored-procedures.md)
