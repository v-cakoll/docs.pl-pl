---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804634"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load nie usuwa właściwości symbolu

|   |   |
|---|---|
|Szczegóły|Podczas kierowania na .NET Framework 4.5 w projektancie przepływu pracy i ładowania ponownie hostowanego <xref:System.Activities.Presentation.WorkflowDesigner.Load> przepływu <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> pracy 3.5 z metodą, a jest generowany podczas zapisywania przepływu pracy.|
|Sugestia|Ten błąd objawia się tylko podczas kierowania .NET Framework 4.5 w projektancie przepływu <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> pracy, dzięki czemu można obejść, ustawiając na 4.0 .NET Framework.Alternatively, problem można uniknąć przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody, aby załadować przepływ pracy, zamiast <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
