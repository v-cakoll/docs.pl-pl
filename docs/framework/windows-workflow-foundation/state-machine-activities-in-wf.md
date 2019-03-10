---
title: Działań automatu stanów w WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: eee507f873cde3aabce09c9b3fdb1620cd79fdab
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710319"
---
# <a name="state-machine-activities-in-wf"></a>Działań automatu stanów w WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zawiera kilka działań dostarczane przez system i projektanci działań do tworzenia przepływów pracy automatu stanów.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Wykonuje zawarte działania przy użyciu modelu maszyny znanego stanu.|  
|<xref:System.Activities.Statements.State>|Reprezentuje stan w automacie stanów.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Reprezentuje kończący stan w automacie stanów. <xref:System.Activities.Core.Presentation.FinalState> Projektant działań jest że w przypadku używane tworzy <xref:System.Activities.Statements.State> we wstępnie skonfigurowanym jako powodujący przerwanie stanu. Aby uzyskać więcej informacji, zobacz [FinalState, Projektant działań](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Reprezentuje przejście między dwoma stanami. Istnieje nie **przybornika** element do <xref:System.Activities.Statements.Transition>; przejścia są tworzone w Projektancie przepływu pracy, przeciągając i upuszczając linię między dwoma stanami lub upuszczając stanu na trójkąty, które są wyświetlane, kiedy jeden stan jest aktywowany zamiast innego . Aby uzyskać więcej informacji, zobacz [Transaction, Projektant działań](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
