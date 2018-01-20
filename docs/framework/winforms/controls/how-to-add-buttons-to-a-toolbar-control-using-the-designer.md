---
title: "Porady: dodawanie przycisków do formantu ToolBar przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5339d946f771b7ba187813dd67860aaa63a21eb3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Porady: dodawanie przycisków do formantu ToolBar przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 Integralną częścią <xref:System.Windows.Forms.ToolBar> formant jest przycisków, Dodaj do niej. Te mogą służyć do zapewnienia łatwy dostęp do poleceń menu lub alternatywnie mogą być umieszczane w innym miejscu interfejsu użytkownika aplikacji do udostępnienia poleceń, aby użytkownicy nie są dostępne w strukturze menu.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ToolBar> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-buttons-at-design-time"></a>Aby dodać przyciski w czasie projektowania  
  
1.  Wybierz <xref:System.Windows.Forms.ToolBar> formantu.  
  
2.  W **właściwości** okna, kliknij przycisk <xref:System.Windows.Forms.ToolBar.Buttons%2A> właściwości, aby go zaznaczyć, a następnie kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) przycisk, aby otworzyć **edytora kolekcji ToolBarButton**.  
  
3.  Użyj **Dodaj** i **Usuń** przyciski dodawania i usuwania przycisków z <xref:System.Windows.Forms.ToolBar> formantu.  
  
4.  Skonfiguruj właściwości poszczególnych przycisków w **właściwości** oknie, w którym zostanie wyświetlony w okienku po prawej stronie edytora. W poniższej tabeli przedstawiono niektóre ważne właściwości wziąć pod uwagę.  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Ustawia menu, który będzie wyświetlany na przycisku paska narzędzi z listy rozwijanej. Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> musi mieć ustawioną właściwość <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Ta właściwość ma wystąpienie <xref:System.Windows.Forms.ContextMenu> klasy jako odwołanie.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Określa, czy częściowo spoczywa Przełącz styl przycisku paska narzędzi. Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> musi mieć ustawioną właściwość <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Określa, czy Przełącz styl przycisku paska narzędzi jest obecnie w stanie włożony. Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> musi mieć ustawioną właściwość <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> lub <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Ustawia styl przycisku paska narzędzi. Musi być jedną z wartości w <xref:System.Windows.Forms.ToolBarButtonStyle> wyliczenia.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Ciąg tekstowy wyświetlany przez przycisk.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Tekst wyświetlany jako etykietka narzędzia dla przycisku.|  
  
5.  Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć panele określony.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolBar>  
 [Instrukcje: określanie ikony dla przycisku kontrolki ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [ToolBar, kontrolka](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
