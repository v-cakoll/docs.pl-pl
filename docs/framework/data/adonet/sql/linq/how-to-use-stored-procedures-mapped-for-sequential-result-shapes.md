---
title: 'Instrukcje: Używanie procedur składowanych zmapowanych do sekwencyjnych kształtów wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 296870029d2329640466b3a540e9057738173aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495659"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Instrukcje: Używanie procedur składowanych zmapowanych do sekwencyjnych kształtów wyników
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
