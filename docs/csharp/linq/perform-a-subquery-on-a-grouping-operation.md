---
title: Wykonanie podzapytania w operacji grupowania
description: Jak wykonanie podzapytania w operacji grupowania.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Wykonanie podzapytania w operacji grupowania

W tym temacie przedstawiono dwa różne sposoby, aby utworzyć kwerendę, porządkuje źródło danych w grupach, a następnie wykonuje podzapytania w każdej grupie pojedynczo. Podstawowa metoda w każdym przykładzie jest grupować elementy źródłowe przy użyciu *kontynuacji* o nazwie `newGroup`i generować nowy podzapytania przed `newGroup`. Tym podzapytaniu jest wykonywane na każdej grupy utworzony w wyniku zapytania zewnętrzne. Należy pamiętać, że w tym przykładzie ostateczne dane wyjściowe nie jest grupą, ale prostych sekwencji typy anonimowe.  
  
 Aby uzyskać więcej informacji na temat grupy, zobacz [klauzuli group](../language-reference/keywords/group-clause.md).  
  
 Aby uzyskać więcej informacji o kontynuacje, zobacz [do](../language-reference/keywords/into.md). W poniższym przykładzie użyto struktury danych w pamięci jako źródło danych, ale same zasady mają zastosowanie dla dowolnego rodzaju źródła danych LINQ.  
  
## <a name="example"></a>Przykład 

 > [!NOTE]
 > Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)
