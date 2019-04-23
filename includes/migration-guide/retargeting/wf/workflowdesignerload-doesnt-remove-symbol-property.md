---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774484"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load nie powoduje usunięcia właściwości symboli

|   |   |
|---|---|
|Szczegóły|Podczas określania wartości docelowej programu .NET Framework 4.5 w Projektancie przepływu pracy i ładowanie ponownie hostowanej 3,5 przepływu pracy przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> zgłaszany podczas zapisywania przepływu pracy.|
|Sugestia|Ta usterka wyłącznie w sytuacji, gdy przeznaczone dla .NET Framework 4.5 w Projektancie przepływu pracy, dzięki czemu możesz pracować nad całym, ustawiając <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> do wersji 4.0 Framework.Alternatively .NET, można uniknąć problemu, przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodę, aby załadować przepływu pracy, zamiast <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
