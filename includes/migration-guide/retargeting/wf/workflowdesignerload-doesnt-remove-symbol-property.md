---
ms.openlocfilehash: 97a92c6bce80b93e9a8bdd863bf881631eaffb27
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804634"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load nie powoduje usunięcia właściwości symboli

|   |   |
|---|---|
|Szczegóły|Podczas określania wartości docelowej programu .NET Framework 4.5 w Projektancie przepływu pracy i ładowanie ponownie hostowanej 3,5 przepływu pracy przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> zgłaszany podczas zapisywania przepływu pracy.|
|Sugestia|Ta usterka wyłącznie w sytuacji, gdy przeznaczone dla .NET Framework 4.5 w Projektancie przepływu pracy, dzięki czemu możesz pracować nad całym, ustawiając <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> do wersji 4.0 Framework.Alternatively .NET, można uniknąć problemu, przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodę, aby załadować przepływu pracy, zamiast <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Scope|Duży|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

