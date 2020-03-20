---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804634"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="78b9a-101">WorkflowDesigner.Load nie usuwa właściwości symbolu</span><span class="sxs-lookup"><span data-stu-id="78b9a-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="78b9a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="78b9a-102">Details</span></span>|<span data-ttu-id="78b9a-103">Podczas kierowania na .NET Framework 4.5 w projektancie przepływu pracy i ładowania ponownie hostowanego <xref:System.Activities.Presentation.WorkflowDesigner.Load> przepływu <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> pracy 3.5 z metodą, a jest generowany podczas zapisywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="78b9a-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="78b9a-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="78b9a-104">Suggestion</span></span>|<span data-ttu-id="78b9a-105">Ten błąd objawia się tylko podczas kierowania .NET Framework 4.5 w projektancie przepływu <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> pracy, dzięki czemu można obejść, ustawiając na 4.0 .NET Framework.Alternatively, problem można uniknąć przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody, aby załadować przepływ pracy, zamiast <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="78b9a-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="78b9a-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="78b9a-106">Scope</span></span>|<span data-ttu-id="78b9a-107">Duży</span><span class="sxs-lookup"><span data-stu-id="78b9a-107">Major</span></span>|
|<span data-ttu-id="78b9a-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="78b9a-108">Version</span></span>|<span data-ttu-id="78b9a-109">4.5</span><span class="sxs-lookup"><span data-stu-id="78b9a-109">4.5</span></span>|
|<span data-ttu-id="78b9a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="78b9a-110">Type</span></span>|<span data-ttu-id="78b9a-111">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="78b9a-111">Retargeting</span></span>|
|<span data-ttu-id="78b9a-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="78b9a-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
