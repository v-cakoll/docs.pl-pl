---
title: 'Porady: sterowanie szeregowaniem w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa08106126212345bb594cdeabe6e7281cd7b5e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44364835"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Porady: sterowanie szeregowaniem w zapytaniu PLINQ
Te przykłady przedstawiają sposób sterowanie szeregowaniem w zapytaniu PLINQ przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> — metoda rozszerzenia.  
  
> [!WARNING]
>  Te przykłady przede wszystkim służą do zademonstrowania użycia i może być lub może nie działać szybciej niż równoważna sekwencyjnego LINQ do zapytań obiekt.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zachowuje kolejność sekwencji źródłowej. Czasami jest to konieczne. na przykład niektóre operatory zapytań wymagają sekwencji źródłowej uporządkowany w celu wygenerowania prawidłowych wyników.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano niektóre zapytania, operatory, których sekwencji źródłowej prawdopodobnie powinien zostać określona. Te operatory będą działać w sekwencji nieuporządkowaną, ale mogą one dawać nieoczekiwane wyniki.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zachować kolejności pierwszej części zapytania, a następnie usuń kolejności, co pozwoli zwiększyć wydajność klauzuli join a następnie ponownie Zastosuj kolejność sekwencji wynik końcowy.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Aby uruchomić tę metodę, wklej go do klasy PLINQDataSample w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, a następnie naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>  
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
