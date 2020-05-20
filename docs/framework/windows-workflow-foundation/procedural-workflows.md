---
title: Proceduralne przepływy pracy
description: W programie Workflow Foundation przepływy pracy proceduralnej korzystają z metod sterowania przepływem podobnych do tych, które znajdują się w językach proceduralnych.
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 97664c1352928e7d05c2ed15fc118dd21474cfc3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421439"
---
# <a name="procedural-workflows"></a><span data-ttu-id="1c607-103">Proceduralne przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="1c607-103">Procedural Workflows</span></span>
<span data-ttu-id="1c607-104">Proceduralne przepływy pracy używają metod sterowania przepływem podobnych do tych, które znajdują się w językach proceduralnych.</span><span class="sxs-lookup"><span data-stu-id="1c607-104">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="1c607-105">Te konstrukcje obejmują `While` i `If` .</span><span class="sxs-lookup"><span data-stu-id="1c607-105">These constructs include `While` and `If`.</span></span> <span data-ttu-id="1c607-106">Te przepływy pracy mogą być swobodnie składane przy użyciu innych działań sterowania przepływem, takich jak <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="1c607-106">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="1c607-107">Sterowanie przepływem wykonywania</span><span class="sxs-lookup"><span data-stu-id="1c607-107">Controlling Execution Flow</span></span>  
 <span data-ttu-id="1c607-108">Biblioteka działań przepływu pracy ma działania dotyczące modelowania większości metod kontroli przepływu używanych w językach proceduralnych.</span><span class="sxs-lookup"><span data-stu-id="1c607-108">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="1c607-109">Należą do nich:</span><span class="sxs-lookup"><span data-stu-id="1c607-109">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="1c607-110">Aby korzystać z działań sterowania przepływem, przeciągnij i upuść je z przybornika **działań** do działania złożonego wewnątrz okna projektanta.</span><span class="sxs-lookup"><span data-stu-id="1c607-110">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c607-111">W przypadku używania funkcji hostingu systemu Windows Server AppFabric do hostowania przepływów pracy w kolektywie serwerów, program AppFabric przeniesie wystąpienia między różnymi serwerami programu AppFabric.</span><span class="sxs-lookup"><span data-stu-id="1c607-111">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="1c607-112">Wymaga to, aby zasoby mogły być współużytkowane między wszystkimi węzłami.</span><span class="sxs-lookup"><span data-stu-id="1c607-112">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="1c607-113">Żadna z domyślnych działań w ramach przepływu pracy netto 4 nie zawiera żadnych operacji, które uzyskują dostęp do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1c607-113">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="1c607-114">Ponieważ program AppFabric nie oferuje żadnego mechanizmu, aby oznaczyć przepływ pracy jako nieruchomy, Deweloper nie może tworzyć działań niestandardowych, które kończą się niepowodzeniem podczas przenoszenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1c607-114">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c607-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c607-115">See also</span></span>

- [<span data-ttu-id="1c607-116">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="1c607-116">Flowchart Workflows</span></span>](flowchart-workflows.md)
