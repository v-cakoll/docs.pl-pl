---
title: Wykonanie podzapytania w operacji grupowania
description: Jak wykonanie podzapytania w operacji grupowania.
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: f638b8a679a15891d04e02f1597d6bf7934a9e74
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
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
