---
title: "Porady: wyrównywanie formantu z krawędziami formularzy w czasie projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86134902a6645d2c9bf7bcef2cf93bf543d8c9bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Porady: wyrównywanie formantu z krawędziami formularzy w czasie projektowania
Umożliwia wyrównanie z krawędzią formularzy przez ustawienie formantu <xref:System.Windows.Forms.Control.Dock%2A>. Ta właściwość określa, gdzie formantu znajduje się w formularzu. <xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić następujące wartości:  
  
|Ustawienie|Wpływ na formantu|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Doków do dolnej części formularza.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Kopiuje wszystkie pozostałe miejsce w formularzu.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Doków po lewej stronie formularza.|  
|<xref:System.Windows.Forms.DockStyle.None>|Czy nie dokowania z dowolnego miejsca i pojawia się w lokalizacji określonej przez jego <xref:System.Windows.Forms.Control.Location%2A>.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Doków z prawej strony formularza.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Doków do górnej części formularza.|  
  
 Te wartości można również ustawić w kodzie. Aby uzyskać więcej informacji, zobacz [porady: wyrównywanie formantu z krawędziami formularzy](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a>Aby ustawić właściwości Dock dla formantu w czasie projektowania  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz formantu.  
  
2.  W **właściwości** , kliknij listę rozwijaną pola obok <xref:System.Windows.Forms.Control.Dock%2A> właściwości.  
  
     Graficzny interfejs reprezentujący sześciu możliwe <xref:System.Windows.Forms.Control.Dock%2A> wyświetlane ustawienia.  
  
3.  Wybierz odpowiednie ustawienie.  
  
4.  Formant będzie teraz dock w sposób określony przez ustawienie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [Porady: wyrównywanie formantu z krawędziami formularzy](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Porady: kotwiczenie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Opracowywanie formularzy systemu Windows formantów w czasie projektowania](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
