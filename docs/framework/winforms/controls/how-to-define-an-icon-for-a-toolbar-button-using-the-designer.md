---
title: "Porady: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85be18b2cbb4e0fe729c335016fa8e7348f7be13
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Porady: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 <xref:System.Windows.Forms.ToolBar>przyciski będą mogli wyświetlać ikony w nich ułatwiający identyfikację przez użytkowników. Jest to osiągane przez dodanie obrazów do <xref:System.Windows.Forms.ImageList> składnika i kojarzenie go z <xref:System.Windows.Forms.ToolBar> formantu.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ToolBar> kontroli i <xref:System.Windows.Forms.ImageList> składnika. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Aby ustawić ikony dla przycisku paska narzędzi w czasie projektowania  
  
1.  Dodawanie obrazów do <xref:System.Windows.Forms.ImageList> składnika. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie obrazów ImageList przy użyciu projektanta](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Wybierz <xref:System.Windows.Forms.ToolBar> kontrolkę w formularzu.  
  
3.  W **właściwości** ustaw <xref:System.Windows.Forms.ToolBar> formantu <xref:System.Windows.Forms.ToolBar.ImageList%2A> właściwości <xref:System.Windows.Forms.ImageList> składnika.  
  
4.  Kliknij przycisk <xref:System.Windows.Forms.ToolBar> formantu <xref:System.Windows.Forms.ToolBar.Buttons%2A> właściwość, aby go zaznaczyć, a następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **Edytora kolekcji ToolBarButton**.  
  
5.  Użyj **Dodaj** przycisk, aby dodać przyciski <xref:System.Windows.Forms.ToolBar> formantu.  
  
6.  W **właściwości** okna, która jest wyświetlana w okienku po prawej stronie **edytora kolekcji ToolBarButton**ustaw <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> właściwości przycisku paska narzędzi do jednej z wartości na liście, które jest przenoszony z obrazów dodane do <xref:System.Windows.Forms.ImageList> składnika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolBar>  
 [Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar, kontrolka](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [ImageList, składnik](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
