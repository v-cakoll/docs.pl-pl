---
title: "Porady: dokowanie formantów na formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4897a195dcafb8264bbab619f1a46118a829f44e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Porady: dokowanie formantów na formularzach systemu Windows
Możesz dokowanie formantów na krawędziach formularza lub je wypełnienia formantu kontenera (formularza lub kontrolki kontenera). Na przykład stacje dokujące Eksploratora Windows jego <xref:System.Windows.Forms.TreeView> kontrolki do lewej strony okna i jego <xref:System.Windows.Forms.ListView> formantu do prawej krawędzi okna. Użyj <xref:System.Windows.Forms.Control.Dock%2A> właściwości dla wszystkich widoczne formantów formularzy systemu Windows do definiowania trybu dokowania.  
  
> [!NOTE]
>  Formanty są zadokowane w odwrotnej kolejności.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Właściwości współdziała z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości. Aby uzyskać więcej informacji, zobacz [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Aby dock — formant  
  
1.  Wybierz kontrolkę, która ma być dokowania.  
  
2.  W oknie właściwości, kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.  
  
     Edytor wyświetlany jest przedstawia serię pól reprezentujący krawędzie i środek formularza.  
  
3.  Kliknij przycisk, który reprezentuje krawędzi formularz miejsce dock formantu. Aby wypełnić zawartość formantu formularza lub kontrolki kontenera, kliknij pole center. Kliknij przycisk **(Brak)** wyłączyć dokowania.  
  
     Kontrolka jest automatycznie dopasowane granice zadokowane graniczny.  
  
    > [!NOTE]
    >  Formanty dziedziczone muszą być `Protected` mógł być zadokowany. Aby zmienić poziom dostępu do formantu, ustaw jej **modyfikator** właściwości w oknie właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty formularzy systemu Windows](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Formanty przez funkcję formularzy systemu Windows](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Porady: kotwiczenie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
