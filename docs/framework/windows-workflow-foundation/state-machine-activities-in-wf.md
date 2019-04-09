---
title: Działań automatu stanów w WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 5aee2a7cb078d9d62c9296f7dda9f28ff812a88a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120916"
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
