---
title: Działania przepływu sterowania w WF
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: bcbb12210af2d0172977dca6f81355031baa043a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="control-flow-activities-in-wf"></a>Działania przepływu sterowania w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Zawiera kilka działań sterowanie przepływem działanie w przepływie pracy. Niektóre z tych działań (takie jak `Switch` i `If`) podobne do programowania środowiskach takie jak Visual C#, podczas gdy inne struktury sterujące przepływ wykonania (takich jak `Pick`) modelu nowe struktury programowania.  
  
 Należy pamiętać, że podczas działania takie jak `Parallel` i `ParallelForEach` działania zaplanować jednocześnie wiele działań podrzędnych do wykonania, ale jest używana tylko jednego wątku przepływu pracy. Każde działanie podrzędne tych działań wykonuje sekwencyjnie i nie wykonuj kolejnych działań, aż do poprzedniego działania zakończyć lub przejść bezczynności. W związku z tym te działania są najbardziej przydatne w przypadku aplikacji, w których kilka działania blokujące potencjalnie musi być wykonywany w sposób przeplotem. Jeśli żadne działania podrzędne tych działań Przejdź bezczynny, `Parallel` działania wykonuje tak jak `Sequence` działania, a `ParallelForEach` działania wykonuje tak jak `ForEach` działania. Jeśli, jednak asynchroniczne działania (takich jak działania, które pochodzą z <xref:System.Activities.AsyncCodeActivity>) lub działania obsługi komunikatów są używane, formantu zostanie przekazany dalej gałęzi, gdy działanie podrzędne oczekuje na jego komunikat do odebrania lub jego asynchroniczne zostanie ukończona.  
  
## <a name="flow-control-activities"></a>Działania przepływu sterowania  
  
|Działanie|Opis|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Wykonuje zawarte działania raz i będzie nadal występować to zrobić, gdy warunek ma `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Wykonuje instrukcję osadzony w sekwencji dla każdego elementu w kolekcji. <xref:System.Activities.Statements.ForEach%601> jest podobny do słowa kluczowego `foreach`, ale jest zaimplementowana jako działania zamiast instrukcji języka.|  
|<xref:System.Activities.Statements.If>|Wykonuje zawarte działania, jeśli wynikiem warunku jest `true`i może zostać wykonany działań zawartych w <xref:System.Activities.Statements.If.Else%2A> właściwości, jeśli wynikiem warunku jest `false`.|  
|<xref:System.Activities.Statements.Parallel>|Wykonuje zawarte działania równoległe.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Osadzona instrukcja jest wykonywana równolegle dla każdego elementu w kolekcji.|  
|<xref:System.Activities.Statements.Pick>|Udostępnia modelowanie przepływu sterowania opartego na zdarzeniach.|  
|<xref:System.Activities.Statements.PickBranch>|Reprezentuje potencjalne ścieżki wykonywania w <xref:System.Activities.Statements.Pick> działania.|  
|<xref:System.Activities.Statements.Sequence>|Wykonuje zawarte działania w sekwencji.|  
|<xref:System.Activities.Statements.Switch%601>|Wybiera wybór jednego z wielu działań do wykonania, na podstawie wartości podanego wyrażenia.|  
|<xref:System.Activities.Statements.While>|Wykonuje zawarte działania, gdy warunek ma `true`.|
