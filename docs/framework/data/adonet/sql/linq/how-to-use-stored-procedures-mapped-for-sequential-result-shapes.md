---
title: 'Instrukcje: Używanie procedur składowanych zamapowanych na sekwencyjne kształty wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: bae10e823a274304f21292cf55947a4d4eaccc10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781456"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Instrukcje: Używanie procedur składowanych zamapowanych na sekwencyjne kształty wyników
Ten rodzaj procedury składowanej może generować więcej niż jeden kształt wynikowy, ale wiadomo, w jakiej kolejności zwracane są wyniki. Ten scenariusz należy wykonać w scenariuszu, w którym nie jest znana sekwencja zwracanych wartości. Aby uzyskać więcej informacji, zobacz [jak: Używanie procedur składowanych mapowanych na wiele](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)kształtów wyników.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się T-SQL procedury składowanej zwracającej wiele kształtów wyników sekwencyjnie:  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Przykład  
 Aby wykonać tę procedurę składowaną, należy użyć kodu podobnego do poniższego.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury składowane](stored-procedures.md)
