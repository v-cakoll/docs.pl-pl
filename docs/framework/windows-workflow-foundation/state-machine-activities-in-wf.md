---
title: "Działania automatu stanów w WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5056557c9fee74e9a16b235220c797e1f6356ce3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="state-machine-activities-in-wf"></a>Działania automatu stanów w WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]zawiera kilka działań dostarczane przez system i projektantów działań do tworzenia przepływów pracy komputera stanu.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Wykonuje zawarte działania przy użyciu modelu maszyny znanego stanu.|  
|<xref:System.Activities.Statements.State>|Reprezentuje stan komputera stanu.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Reprezentuje zakończenia stan komputera stanu. <xref:System.Activities.Core.Presentation.FinalState>Projektant działań jest że w przypadku używane tworzy <xref:System.Activities.Statements.State> wstępnie skonfigurowane jako stan zakończenia. Aby uzyskać więcej informacji, zobacz [Projektant działań stan końcowy](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Reprezentuje przejście między dwoma stanami. Brak nie **przybornika** element do <xref:System.Activities.Statements.Transition>; przejścia na projektanta przepływów pracy są tworzone przez przeciąganie i upuszczanie linii między dwoma stanami lub poprzez upuszczenie stanu na trójkąty widocznych jednego stanu jest aktywowany przez inny . Aby uzyskać więcej informacji, zobacz [Projektant działań przejścia](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
