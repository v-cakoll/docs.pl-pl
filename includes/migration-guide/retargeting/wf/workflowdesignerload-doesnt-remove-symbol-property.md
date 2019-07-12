---
ms.openlocfilehash: 97a92c6bce80b93e9a8bdd863bf881631eaffb27
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804634"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="2a3c0-101">WorkflowDesigner.Load nie powoduje usunięcia właściwości symboli</span><span class="sxs-lookup"><span data-stu-id="2a3c0-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2a3c0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2a3c0-102">Details</span></span>|<span data-ttu-id="2a3c0-103">Podczas określania wartości docelowej programu .NET Framework 4.5 w Projektancie przepływu pracy i ładowanie ponownie hostowanej 3,5 przepływu pracy przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> zgłaszany podczas zapisywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2a3c0-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="2a3c0-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="2a3c0-104">Suggestion</span></span>|<span data-ttu-id="2a3c0-105">Ta usterka wyłącznie w sytuacji, gdy przeznaczone dla .NET Framework 4.5 w Projektancie przepływu pracy, dzięki czemu możesz pracować nad całym, ustawiając <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> do wersji 4.0 Framework.Alternatively .NET, można uniknąć problemu, przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodę, aby załadować przepływu pracy, zamiast <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="2a3c0-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="2a3c0-106">Scope</span><span class="sxs-lookup"><span data-stu-id="2a3c0-106">Scope</span></span>|<span data-ttu-id="2a3c0-107">Duży</span><span class="sxs-lookup"><span data-stu-id="2a3c0-107">Major</span></span>|
|<span data-ttu-id="2a3c0-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="2a3c0-108">Version</span></span>|<span data-ttu-id="2a3c0-109">4.5</span><span class="sxs-lookup"><span data-stu-id="2a3c0-109">4.5</span></span>|
|<span data-ttu-id="2a3c0-110">Typ</span><span class="sxs-lookup"><span data-stu-id="2a3c0-110">Type</span></span>|<span data-ttu-id="2a3c0-111">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="2a3c0-111">Retargeting</span></span>|
|<span data-ttu-id="2a3c0-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2a3c0-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

