---
title: 'Instrukcje: dokowanie kontrolek w Formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 61ccad615eec81eb1aa77e6a99d48ef29ecb5be2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231529"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Instrukcje: dokowanie kontrolek w Formularzach systemu Windows
Można dokowanie formantów do krawędzi formularza lub je wypełnić kontener formantu (formularza lub kontrolki kontenera). Na przykład Windows Explorer dokowane jego <xref:System.Windows.Forms.TreeView> kontrolki do lewej części okna i jego <xref:System.Windows.Forms.ListView> kontrolki po prawej stronie okna. Użyj <xref:System.Windows.Forms.Control.Dock%2A> właściwości dla wszystkich widocznych kontrolek Windows Forms do definiowania tryb dokowania.  
  
> [!NOTE]
>  Formanty są zadokowane w odwrotnej kolejności.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Właściwość wchodzi w interakcję z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości. Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Aby zadokować kontrolki  
  
1.  Wybierz formant, który chcesz zadokować.  
  
2.  W oknie dialogowym właściwości kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.  
  
     Zostanie wyświetlony Edytor, pokazujący szereg pola reprezentujące krawędzie i środek formularza.  
  
3.  Kliknij przycisk, który reprezentuje krawędzi formularza, które chcesz zadokować formantu. Aby wypełnić zawartość formularza kontrolki lub kontrolki kontenera, kliknij pole Centrum. Kliknij przycisk **(Brak)** wyłączyć dokowania.  
  
     Kontrolka jest automatycznie dopasowane granice zadokowany krawędzi.  
  
    > [!NOTE]
    >  Musi być dziedziczone formantów `Protected` aby można było bez możliwości dokowania. Aby zmienić poziom dostępu formantu, ustaw jego **modyfikator** właściwości w oknie dialogowym właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Formanty formularzy systemu Windows](index.md)
- [Rozmieszczanie formantów na formularzach systemu Windows](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych formantów formularzy systemu Windows i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
- [Formanty formularzy systemu Windows według funkcji](windows-forms-controls-by-function.md)
- [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize — Przegląd właściwości](autosize-property-overview.md)
- [Instrukcje: kotwiczenie kontrolek na formularzach systemu Windows](how-to-anchor-controls-on-windows-forms.md)
