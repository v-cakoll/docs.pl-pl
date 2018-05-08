---
title: 'Porady: dokowanie formantów na formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [AutoSize, właściwość — omówienie](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
