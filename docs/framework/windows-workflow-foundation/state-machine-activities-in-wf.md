---
title: Działania automatu stanów w WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 78727bab0102909e9f1e479210cf4b42801aa3ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515772"
---
# <a name="state-machine-activities-in-wf"></a>Działania automatu stanów w WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zawiera kilka działań dostarczane przez system i projektantów działań do tworzenia przepływów pracy komputera stanu.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Wykonuje zawarte działania przy użyciu modelu maszyny znanego stanu.|  
|<xref:System.Activities.Statements.State>|Reprezentuje stan komputera stanu.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Reprezentuje zakończenia stan komputera stanu. <xref:System.Activities.Core.Presentation.FinalState> Projektant działań jest że w przypadku używane tworzy <xref:System.Activities.Statements.State> wstępnie skonfigurowane jako stan zakończenia. Aby uzyskać więcej informacji, zobacz [Projektant działań stan końcowy](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Reprezentuje przejście między dwoma stanami. Brak nie **przybornika** element do <xref:System.Activities.Statements.Transition>; przejścia na projektanta przepływów pracy są tworzone przez przeciąganie i upuszczanie linii między dwoma stanami lub poprzez upuszczenie stanu na trójkąty widocznych jednego stanu jest aktywowany przez inny . Aby uzyskać więcej informacji, zobacz [Projektant działań przejścia](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
