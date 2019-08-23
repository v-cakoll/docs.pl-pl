---
title: Proceduralne przepływy pracy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: d1edd73b2276d0a3918b61c8da2d04769d09e7c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956118"
---
# <a name="procedural-workflows"></a><span data-ttu-id="7a4a4-102">Proceduralne przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="7a4a4-102">Procedural Workflows</span></span>
<span data-ttu-id="7a4a4-103">Proceduralne przepływy pracy używają metod sterowania przepływem podobnych do tych, które znajdują się w językach proceduralnych.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="7a4a4-104">Te konstrukcje obejmują `While` i `If`.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="7a4a4-105">Te przepływy pracy mogą być swobodnie składane przy użyciu innych działań <xref:System.Activities.Statements.Flowchart> sterowania <xref:System.Activities.Statements.Sequence>przepływem, takich jak i.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="7a4a4-106">Sterowanie przepływem wykonywania</span><span class="sxs-lookup"><span data-stu-id="7a4a4-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="7a4a4-107">Biblioteka działań przepływu pracy ma działania dotyczące modelowania większości metod kontroli przepływu używanych w językach proceduralnych.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="7a4a4-108">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7a4a4-108">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="7a4a4-109">Aby korzystać z działań sterowania przepływem, przeciągnij i upuść je z przybornika **działań** do działania złożonego wewnątrz okna projektanta.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a4a4-110">W przypadku używania funkcji hostingu systemu Windows Server AppFabric do hostowania przepływów pracy w kolektywie serwerów, program AppFabric przeniesie wystąpienia między różnymi serwerami programu AppFabric.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-110">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="7a4a4-111">Wymaga to, aby zasoby mogły być współużytkowane między wszystkimi węzłami.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="7a4a4-112">Żadna z domyślnych działań w ramach przepływu pracy netto 4 nie zawiera żadnych operacji, które uzyskują dostęp do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="7a4a4-113">Ponieważ program AppFabric nie oferuje żadnego mechanizmu, aby oznaczyć przepływ pracy jako nieruchomy, Deweloper nie może tworzyć działań niestandardowych, które kończą się niepowodzeniem podczas przenoszenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7a4a4-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a4a4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a4a4-114">See also</span></span>

- [<span data-ttu-id="7a4a4-115">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="7a4a4-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
