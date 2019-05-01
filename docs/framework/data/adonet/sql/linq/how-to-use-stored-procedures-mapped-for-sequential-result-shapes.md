---
title: 'Instrukcje: Używanie procedur składowanych zamapowanych na sekwencyjne kształty wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: e51ebacb3f6be849f7b871f2d12db3ea7476b117
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877074"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Instrukcje: Używanie procedur składowanych zamapowanych na sekwencyjne kształty wyników
Ten rodzaj procedury składowanej można wygenerować więcej niż jeden kształt wyniku, ale wiesz, w jakiej kolejności wyniki są zwracane. Natomiast tego scenariusza ze scenariuszem, których nie znasz sekwencji zwraca. Aby uzyskać więcej informacji, zobacz [jak: Używanie procedur składowanych zmapowanych do wielu kształtów wyników](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Przykład  
 Oto języka T-SQL procedury przechowywanej, która zwraca sekwencyjnie wielu kształtów wyników:  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Przykład  
 Aby wykonać tę procedurę składowaną należy użyć kodu podobnego do następującego.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
