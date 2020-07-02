---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616088"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner. load nie usuwa właściwości symbolu

#### <a name="details"></a>Szczegóły

W przypadku określania .NET Framework 4,5 w Projektancie przepływu pracy i załadowania przepływu pracy, który został ponownie 3,5 hostowany z użyciem <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody, <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> jest zgłaszany podczas zapisywania przepływu pracy.

#### <a name="suggestion"></a>Sugestia

Ten błąd występuje tylko w przypadku, gdy element docelowy .NET Framework 4,5 w Projektancie przepływu pracy, więc można go obejść przez ustawienie `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` do .NET Framework 4,0. Alternatywnie można uniknąć problemu przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody ładowania przepływu pracy, a nie <xref:System.Activities.Presentation.WorkflowDesigner.Load> .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
