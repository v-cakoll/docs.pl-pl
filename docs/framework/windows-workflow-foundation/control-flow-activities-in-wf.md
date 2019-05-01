---
title: Działania przepływu sterowania w WF
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: bcbb12210af2d0172977dca6f81355031baa043a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945915"
---
# <a name="control-flow-activities-in-wf"></a>Działania przepływu sterowania w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Zawiera kilka działań do sterowania przepływem wykonania w przepływie pracy. Niektóre z tych działań (takie jak `Switch` i `If`) zaimplementować podobne do tych w programowanie w środowiskach, takich jak Visual struktury sterujące przepływem C#, podczas gdy inne (takie jak `Pick`) modelu nowych struktur programowania.  
  
 Należy pamiętać, że podczas działania takie jak `Parallel` i `ParallelForEach` działania jednocześnie zaplanować wiele działań podrzędnych do wykonania, tylko jednego wątku jest używana dla przepływu pracy. Każde działanie podrzędne tych działań jest wykonywana sekwencyjnie, a kolejne działania nie są wykonywane do momentu ukończenia lub przejdź bezczynności poprzednich działań. W wyniku działania te są najbardziej przydatne w przypadku aplikacji, w których kilka mogącego powodować blokowanie działania muszą być wykonywane w sposób przeplotem. Jeśli żadne działania podrzędne działania te bezczynny, `Parallel` działanie wykonuje się podobnie jak `Sequence` działania i `ParallelForEach` działanie wykonuje się podobnie jak `ForEach` działania. Jeśli jednak działaniach asynchronicznych (takich jak działania, które wynikają z <xref:System.Activities.AsyncCodeActivity>) lub działań dotyczących komunikatów są używane, kontrolka zostanie przekazany do następnej gałęzi, gdy działanie podrzędne czeka na komunikat do odebrania lub swoją pracę asynchroniczną, należy wykonać.  
  
## <a name="flow-control-activities"></a>Działania sterowania przepływem  
  
|Działanie|Opis|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Wykonuje zawarte działania raz i będzie kontynuowane to zrobić, gdy warunek ma `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Wykonuje instrukcję osadzone w sekwencji dla każdego elementu w kolekcji. <xref:System.Activities.Statements.ForEach%601> jest podobny do słowa kluczowego `foreach`, ale jest zaimplementowana jako działania, a nie instrukcji języka.|  
|<xref:System.Activities.Statements.If>|Wykonuje zawarte działania, jeśli warunek jest `true`i może wykonywać działania zawarte w <xref:System.Activities.Statements.If.Else%2A> właściwość, jeśli wynikiem warunku jest `false`.|  
|<xref:System.Activities.Statements.Parallel>|Wykonuje zawarte działania równoległe.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Osadzona instrukcja jest wykonywana równolegle dla każdego elementu w kolekcji.|  
|<xref:System.Activities.Statements.Pick>|Udostępnia modelowanie przepływu sterowania opartego na zdarzeniach.|  
|<xref:System.Activities.Statements.PickBranch>|Reprezentuje potencjalnych ścieżką wykonywania w <xref:System.Activities.Statements.Pick> działania.|  
|<xref:System.Activities.Statements.Sequence>|Wykonuje zawarte działania w sekwencji.|  
|<xref:System.Activities.Statements.Switch%601>|Wybiera wybór jednego z wielu działań do wykonania, na podstawie wartości podanego wyrażenia.|  
|<xref:System.Activities.Statements.While>|Wykonuje zawarte działania, gdy warunek ma `true`.|
