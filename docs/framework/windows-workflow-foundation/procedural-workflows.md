---
title: Proceduralne przepływy pracy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 2ef23f61e67e0b4c08f12322bac429762205ef8d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622852"
---
# <a name="procedural-workflows"></a><span data-ttu-id="fc915-102">Proceduralne przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="fc915-102">Procedural Workflows</span></span>
<span data-ttu-id="fc915-103">Proceduralne przepływy pracy za pomocą metod sterowanie przepływem podobne do tych w procedurach językach.</span><span class="sxs-lookup"><span data-stu-id="fc915-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="fc915-104">Te konstrukcje obejmują `While` i `If`.</span><span class="sxs-lookup"><span data-stu-id="fc915-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="fc915-105">Te przepływy pracy mogą być swobodnie składane, przy użyciu innych działań sterowania przepływem, takich jak <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="fc915-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="fc915-106">Sterowanie przepływem wykonania</span><span class="sxs-lookup"><span data-stu-id="fc915-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="fc915-107">Biblioteka działań przepływu pracy ma działania dla większości metod sterowanie przepływem używanych w procedurach językach modelowania.</span><span class="sxs-lookup"><span data-stu-id="fc915-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="fc915-108">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="fc915-108">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="fc915-109">Aby użyć działania sterowania przepływem, przeciągnij i upuść je z **działania** przybornika do działania złożonego wewnątrz okna projektanta.</span><span class="sxs-lookup"><span data-stu-id="fc915-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc915-110">Jeśli przy użyciu [!INCLUDE[dublin](../../../includes/dublin-md.md)] hosta przepływów pracy, w ramach farmy sieci Web AppFabric przeniesie wystąpień między różnymi serwerami AppFabric.</span><span class="sxs-lookup"><span data-stu-id="fc915-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="fc915-111">Wymaga to, że zasoby mogą być współużytkowane przez wszystkie węzły.</span><span class="sxs-lookup"><span data-stu-id="fc915-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="fc915-112">Brak domyślnych działań przepływu pracy NET 4 zawierać dowolne operacje wymagające dostępu do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fc915-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="fc915-113">Ponieważ AppFabric nie oferuje żadnych mechanizm zaznaczania przepływów pracy jako nieruchome, deweloper nie należy utworzyć niestandardowe działania, które się nie powieść, gdy przepływ pracy zostanie przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="fc915-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc915-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc915-114">See also</span></span>

- [<span data-ttu-id="fc915-115">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="fc915-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
