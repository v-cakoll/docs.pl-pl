---
title: Działań automatu stanów w WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 5aee2a7cb078d9d62c9296f7dda9f28ff812a88a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120916"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="88189-102">Działań automatu stanów w WF</span><span class="sxs-lookup"><span data-stu-id="88189-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="88189-103">zawiera kilka działań dostarczane przez system i projektanci działań do tworzenia przepływów pracy automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="88189-103">provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="88189-104">Wykonuje zawarte działania przy użyciu modelu maszyny znanego stanu.</span><span class="sxs-lookup"><span data-stu-id="88189-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="88189-105">Reprezentuje stan w automacie stanów.</span><span class="sxs-lookup"><span data-stu-id="88189-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="88189-106">Reprezentuje kończący stan w automacie stanów.</span><span class="sxs-lookup"><span data-stu-id="88189-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="88189-107"><xref:System.Activities.Core.Presentation.FinalState> Projektant działań jest że w przypadku używane tworzy <xref:System.Activities.Statements.State> we wstępnie skonfigurowanym jako powodujący przerwanie stanu.</span><span class="sxs-lookup"><span data-stu-id="88189-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="88189-108">Aby uzyskać więcej informacji, zobacz [FinalState, Projektant działań](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="88189-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="88189-109">Reprezentuje przejście między dwoma stanami.</span><span class="sxs-lookup"><span data-stu-id="88189-109">Represents the transition between two states.</span></span> <span data-ttu-id="88189-110">Istnieje nie **przybornika** element do <xref:System.Activities.Statements.Transition>; przejścia są tworzone w Projektancie przepływu pracy, przeciągając i upuszczając linię między dwoma stanami lub upuszczając stanu na trójkąty, które są wyświetlane, kiedy jeden stan jest aktywowany zamiast innego .</span><span class="sxs-lookup"><span data-stu-id="88189-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="88189-111">Aby uzyskać więcej informacji, zobacz [Transaction, Projektant działań](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="88189-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88189-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88189-112">See also</span></span>

- [<span data-ttu-id="88189-113">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="88189-113">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
