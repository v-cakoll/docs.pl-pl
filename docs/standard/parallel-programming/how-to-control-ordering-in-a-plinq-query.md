---
title: 'Porady: sterowanie szeregowaniem w zapytaniu PLINQ'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3aef90c1a1160905662f93a83d6536f6d804b179
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Porady: sterowanie szeregowaniem w zapytaniu PLINQ
Poniższe przykłady pokazują, jak sterowanie szeregowaniem w zapytaniu PLINQ przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> — metoda rozszerzenia.  
  
> [!WARNING]
>  Te przykłady głównie służą jedynie do zademonstrowania użycia i może lub może nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytań.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zachowuje kolejność sekwencji źródłowej. Czasami jest to konieczne. na przykład niektóre operatorów zapytań wymagają sekwencji źródłowej uporządkowanych aby wygenerować poprawnych wyników.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono niektóre zapytania operatory, których sekwencji źródłowej prawdopodobnie oczekiwano może zostać określona. Operatory te będą działać na nieuporządkowaną sekwencji, ale może powodować generowanie nieoczekiwane wyniki.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zachowania kolejności pierwszej części zapytania, a następnie usuń, kolejność w celu zwiększenia wydajności w klauzuli join, a następnie ponowne zastosowanie porządkowanie sekwencji wynik końcowy.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.ParallelEnumerable>  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
