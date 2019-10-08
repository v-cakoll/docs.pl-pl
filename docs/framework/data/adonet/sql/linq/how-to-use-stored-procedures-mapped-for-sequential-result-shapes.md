---
title: 'Instrukcje: używanie procedur składowanych mapowanych dla sekwencyjnych kształtów wyników'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 8378a175ab2479ab9769ca08579e1c89269eaba4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003223"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Instrukcje: używanie procedur składowanych mapowanych dla sekwencyjnych kształtów wyników
Ten rodzaj procedury składowanej może generować więcej niż jeden kształt wynikowy, ale wiadomo, w jakiej kolejności zwracane są wyniki. Ten scenariusz należy wykonać w scenariuszu, w którym nie jest znana sekwencja zwracanych wartości. Aby uzyskać więcej informacji, zobacz [How to: use procedur składowanych mapowanych na wiele kształtów wynikowych](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się T-SQL procedury składowanej zwracającej wiele kształtów wyników sekwencyjnie:  
  
```sql
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
