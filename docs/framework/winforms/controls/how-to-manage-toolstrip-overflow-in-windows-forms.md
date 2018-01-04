---
title: "Porady: zarządzanie przepełnieniem elementu ToolStrip w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 619c4832626693a56280c70af3ade5dbb9e9d4de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Porady: zarządzanie przepełnieniem elementu ToolStrip w formularzach systemu Windows
Gdy wszystkie elementy na <xref:System.Windows.Forms.ToolStrip> formantu nie mieszczą się w przydzielonym miejscu, można włączyć funkcji przepełnienie na <xref:System.Windows.Forms.ToolStrip> i określają zachowanie przepełnienie określonych <xref:System.Windows.Forms.ToolStripItem>s.  
  
 Po dodaniu <xref:System.Windows.Forms.ToolStripItem>, które wymagają więcej miejsca niż przydzielony <xref:System.Windows.Forms.ToolStrip> danego formularza bieżący rozmiar, <xref:System.Windows.Forms.ToolStripOverflowButton> automatycznie pojawia się na <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ToolStripOverflowButton> Pojawia się, i włączone przepełnienie elementy są przenoszone do menu przeciążenia listy rozwijanej. Dzięki temu można dostosować i ustalić ich priorytety jak Twoje <xref:System.Windows.Forms.ToolStrip> elementów poprawnie dostosować do różnych rozmiarów. Można także zmienić wygląd elementów, gdy należą one do przeciążenia przy użyciu <xref:System.Windows.Forms.ToolStripItem.Placement%2A> i <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> właściwości i <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzeń. Jeśli w czasie projektowania lub czas wykonywania powiększyć więcej formularza <xref:System.Windows.Forms.ToolStripItem>s mogą być wyświetlane w głównym <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripOverflowButton> nawet może zniknąć dopóki zmniejszyć rozmiar formularza.  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a>Aby włączyć przepełnienie w formancie ToolStrip  
  
-   Upewnij się, że <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> nie ustawiono właściwości `false` dla <xref:System.Windows.Forms.ToolStrip>. Wartość domyślna to `True`.  
  
     Podczas <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> jest `True` (ustawienie domyślne), <xref:System.Windows.Forms.ToolStripItem> są wysyłane do menu rozwijanego przepełnienie podczas zawartość <xref:System.Windows.Forms.ToolStripItem> przekracza szerokość poziomego <xref:System.Windows.Forms.ToolStrip> lub wysokości pionowym <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Aby określić zachowanie Przepełnienie elementu ToolStripItem określonych  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> właściwość <xref:System.Windows.Forms.ToolStripItem> na żądaną wartość. Możliwości są `Always`, `Never`, i `AsNeeded`. Defaultis `AsNeeded`.  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip — podsumowanie informacji o technologii](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
