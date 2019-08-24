---
title: 'Instrukcje: wyrównywanie kontrolki z krawędziami formularzy'
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
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015948"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Instrukcje: wyrównywanie kontrolki z krawędziami formularzy

Formant można dostosować do krawędzi formularza przez ustawienie <xref:System.Windows.Forms.Control.Dock%2A> właściwości. Ta właściwość określa, gdzie znajduje się kontrolka w formularzu. <xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić na następujące wartości:

|Ustawienie|Wpływ na kontrolkę|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Dokowanie w dolnej części formularza.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Wypełnia wszystkie pozostałe miejsca w formularzu.|
|<xref:System.Windows.Forms.DockStyle.Left>|Dokowanie po lewej stronie formularza.|
|<xref:System.Windows.Forms.DockStyle.None>|Nie jest zadokowane w dowolnym miejscu i pojawia się w lokalizacji określonej przez <xref:System.Windows.Forms.Control.Location%2A> jej właściwość.|
|<xref:System.Windows.Forms.DockStyle.Right>|Dokowanie po prawej stronie formularza.|
|<xref:System.Windows.Forms.DockStyle.Top>|Dockuje w górnej części formularza.|

Dla tej funkcji w programie Visual Studio jest obsługiwana obsługa czasu projektowania.

## <a name="set-the-dock-property-for-your-control-at-run-time"></a>Ustaw właściwość Dock dla kontrolki w czasie wykonywania

<xref:System.Windows.Forms.Control.Dock%2A> Ustaw właściwość na odpowiednią wartość w kodzie.

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
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w kontrolce FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
