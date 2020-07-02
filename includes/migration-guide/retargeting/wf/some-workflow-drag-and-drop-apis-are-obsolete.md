---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617289"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Niektóre interfejsy API przeciągania i upuszczania przepływu pracy są przestarzałe

#### <a name="details"></a>Szczegóły

Ten interfejs API przeciągania i upuszczania tego przepływu pracy jest przestarzały i spowoduje ostrzeżenia kompilatora, jeśli aplikacja zostanie odbudowana na 4,5.

#### <a name="suggestion"></a>Sugestia

<xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName>Zamiast tego należy użyć nowych interfejsów API, które obsługują operacje z wieloma obiektami. Alternatywnie można pominąć ostrzeżenia kompilacji lub można je uniknąć przy użyciu starszego kompilatora. Interfejsy API są nadal obsługiwane.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
