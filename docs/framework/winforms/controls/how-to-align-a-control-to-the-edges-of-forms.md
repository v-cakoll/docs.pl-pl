---
title: 'Instrukcje: Wyrównywanie formantu z krawędziami formularzy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 33a3b2e996bdab280eb7a4cd8ad7c59ccb1a1bd2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713894"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Instrukcje: Wyrównywanie formantu z krawędziami formularzy
Ułatwia kontrolki wyrównane do krawędzi formularzy, ustawiając <xref:System.Windows.Forms.Control.Dock%2A> właściwości. Ta właściwość wskazuje, której formant znajduje się w formularzu. <xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić następujące wartości:  
  
|Ustawienie|Wpływ na Twoją kontrolą|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Doków do dolnej części formularza.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Wypełnia całe pozostałe miejsce w formularzu.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Doków do lewej części formularza.|  
|<xref:System.Windows.Forms.DockStyle.None>|Czy nie Zadokuj z dowolnego miejsca i pojawia się w lokalizacji określonej przez jego <xref:System.Windows.Forms.Control.Location%2A> właściwości.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Doków prawą stronę formularza.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Doków do górnej części formularza.|  
  
 Brak obsługi w czasie projektowania dla tej funkcji w programie Visual Studio.  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a>Aby ustawić właściwość dokowania dla formantu w czasie wykonywania  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość odpowiednią wartość w kodzie.  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
