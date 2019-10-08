---
title: 'Instrukcje: korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami skalarnymi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: dfe82fd50eb3eedeaff9082a4288901f72197795
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003236"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Instrukcje: korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami skalarnymi
Można zmapować metodę klienta zdefiniowaną w klasie do funkcji zdefiniowanej przez użytkownika przy użyciu atrybutu <xref:System.Data.Linq.Mapping.FunctionAttribute>. Należy zauważyć, że treść metody konstruuje wyrażenie, które przechwytuje zamiar wywołania metody i przekazuje to wyrażenie do <xref:System.Data.Linq.DataContext> do translacji i wykonywania.  
  
> [!NOTE]
> Bezpośrednie wykonanie odbywa się tylko wtedy, gdy funkcja jest wywoływana poza zapytaniem. Aby uzyskać więcej informacji, zobacz [How to: Call User-Defined Functions inline](how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod SQL przedstawia Skalarną funkcję zdefiniowaną przez użytkownika `ReverseCustName()`.  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Należy zmapować metodę klienta, na przykład następujące dla tego kodu:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje zdefiniowane przez użytkownika](user-defined-functions.md)
