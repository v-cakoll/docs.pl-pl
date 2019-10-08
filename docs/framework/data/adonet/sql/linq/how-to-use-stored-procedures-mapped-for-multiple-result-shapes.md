---
title: 'Instrukcje: używanie procedur składowanych mapowanych dla wielu kształtów wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 065e866ec5937c4af31c0b1563a7582cb4112eba
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003270"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Instrukcje: używanie procedur składowanych mapowanych dla wielu kształtów wyników
Gdy procedura składowana może zwracać wiele kształtów wyników, typ zwracany nie może być jednoznacznie wpisany do pojedynczego kształtu projekcji. Chociaż [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] może generować wszystkie możliwe typy projekcji, nie może on znać kolejności, w której zostaną zwrócone.  
  
 Ten scenariusz należy wykonać z procedurami składowanymi, które tworzą sekwencyjnie wiele kształtów wynikowych. Aby uzyskać więcej informacji, zobacz [How to: use procedur składowanych mapowanych na sekwencyjne kształty wynikowe](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 Atrybut <xref:System.Data.Linq.Mapping.ResultTypeAttribute> jest stosowany do procedur składowanych, które zwracają wiele typów wyników, aby określić zestaw typów, które może zwracać procedura.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu SQL kształt wynik zależy od danych wejściowych (`shape =1` lub `shape = 2`). Nie wiesz, która projekcja zostanie najpierw zwrócona.  
  
``` sql
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
> Aby uzyskać moduł wyliczający poprawnego typu, należy użyć wzorca <xref:System.Data.Linq.IMultipleResults.GetResult%2A> na podstawie wiedzy o procedurze składowanej.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](stored-procedures.md)
