---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616088"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="62590-101">WorkflowDesigner. load nie usuwa właściwości symbolu</span><span class="sxs-lookup"><span data-stu-id="62590-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

#### <a name="details"></a><span data-ttu-id="62590-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="62590-102">Details</span></span>

<span data-ttu-id="62590-103">W przypadku określania .NET Framework 4,5 w Projektancie przepływu pracy i załadowania przepływu pracy, który został ponownie 3,5 hostowany z użyciem <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody, <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> jest zgłaszany podczas zapisywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="62590-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> is thrown while saving the workflow.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="62590-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="62590-104">Suggestion</span></span>

<span data-ttu-id="62590-105">Ten błąd występuje tylko w przypadku, gdy element docelowy .NET Framework 4,5 w Projektancie przepływu pracy, więc można go obejść przez ustawienie `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` do .NET Framework 4,0. Alternatywnie można uniknąć problemu przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody ładowania przepływu pracy, a nie <xref:System.Activities.Presentation.WorkflowDesigner.Load> .</span><span class="sxs-lookup"><span data-stu-id="62590-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>

| <span data-ttu-id="62590-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="62590-106">Name</span></span>    | <span data-ttu-id="62590-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="62590-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="62590-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="62590-108">Scope</span></span>   | <span data-ttu-id="62590-109">Duży</span><span class="sxs-lookup"><span data-stu-id="62590-109">Major</span></span>       |
| <span data-ttu-id="62590-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="62590-110">Version</span></span> | <span data-ttu-id="62590-111">4.5</span><span class="sxs-lookup"><span data-stu-id="62590-111">4.5</span></span>         |
| <span data-ttu-id="62590-112">Typ</span><span class="sxs-lookup"><span data-stu-id="62590-112">Type</span></span>    | <span data-ttu-id="62590-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="62590-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="62590-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="62590-114">Affected APIs</span></span>

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
