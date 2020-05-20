---
title: Działania przepływu sterowania w WF
description: Ten artykuł podsumowuje działania .NET Framework 4.6.1 w celu kontrolowania przepływu wykonywania w ramach przepływu pracy.
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: 18ff982d3f215e3fd46108eb2411f3d1a5ab9745
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420074"
---
# <a name="control-flow-activities-in-wf"></a>Działania przepływu sterowania w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]Zawiera kilka działań związanych z kontrolowaniem przepływu wykonywania w ramach przepływu pracy. Niektóre z tych działań (takie jak `Switch` i `If` ) implementują struktury sterowania przepływem podobne do tych w środowiskach programowania, takich jak Visual C#, a inne (takie jak `Pick` ) modelują nowe struktury programowania.  
  
 Należy pamiętać, że podczas gdy działania, takie jak `Parallel` działania i, `ParallelForEach` Zaplanuj jednocześnie wiele działań podrzędnych, tylko jeden wątek jest używany dla przepływu pracy. Każde działanie podrzędne tych działań wykonuje sekwencyjne i kolejne działania nie są wykonywane do momentu ukończenia poprzednich działań lub przejścia w stan bezczynności. W związku z tym te działania są najbardziej przydatne w przypadku aplikacji, w których niektóre możliwe do blokowania działania muszą być wykonywane w sposób przeplotu. Jeśli żadna z działań podrzędnych tych działań nie przejdzie do trybu bezczynności, `Parallel` działanie jest wykonywane podobnie jak `Sequence` działanie, a `ParallelForEach` działanie jest wykonywane podobnie jak `ForEach` działanie. Jeśli jednak są używane działania asynchroniczne (takie jak działania pochodzące z <xref:System.Activities.AsyncCodeActivity> ) lub komunikaty dotyczące komunikatów, kontrola zostanie przekazana do następnej gałęzi, podczas gdy działanie podrzędne czeka na jego odebranie lub zakończenie pracy asynchronicznej.  
  
## <a name="flow-control-activities"></a>Działania sterowania przepływem  
  
|Działanie|Opis|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Wykonuje zawarte działania raz i w dalszym ciągu kontynuuje działanie, gdy warunek to `true` .|  
|<xref:System.Activities.Statements.ForEach%601>|Wykonuje osadzoną instrukcję w sekwencji dla każdego elementu w kolekcji. <xref:System.Activities.Statements.ForEach%601>jest podobny do słowa kluczowego `foreach` , ale jest zaimplementowany jako działanie, a nie język instrukcji.|  
|<xref:System.Activities.Statements.If>|Wykonuje zawarte działania, jeśli warunek jest `true` i może wykonywać działania zawarte we właściwości, <xref:System.Activities.Statements.If.Else%2A> Jeśli warunek ma wartość `false` .|  
|<xref:System.Activities.Statements.Parallel>|Wykonuje zawarte działania równolegle.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Wykonuje osadzoną instrukcję równolegle dla każdego elementu w kolekcji.|  
|<xref:System.Activities.Statements.Pick>|Udostępnia modelowanie przepływu sterowania opartego na zdarzeniach.|  
|<xref:System.Activities.Statements.PickBranch>|Reprezentuje potencjalną ścieżkę wykonywania w <xref:System.Activities.Statements.Pick> działaniu.|  
|<xref:System.Activities.Statements.Sequence>|Wykonuje zawarte działania w sekwencji.|  
|<xref:System.Activities.Statements.Switch%601>|Wybiera jeden wybór z wielu działań do wykonania na podstawie wartości danego wyrażenia.|  
|<xref:System.Activities.Statements.While>|Wykonuje zawarte działania, gdy spełniony jest warunek `true` .|
