---
title: 'Instrukcje: dokowanie kontrolek w Formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: dc514fd8b9b7a17bf07a878e42729db4187d2b82
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963628"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Instrukcje: dokowanie kontrolek w Formularzach systemu Windows
Możesz zadokować kontrolki do krawędzi formularza lub popełniać kontener formantu (formularz lub kontrolka kontenera). Na przykład Eksplorator Windows dockuje swój <xref:System.Windows.Forms.TreeView> formant po lewej stronie okna i jego <xref:System.Windows.Forms.ListView> kontrolkę po prawej stronie okna. <xref:System.Windows.Forms.Control.Dock%2A> Użyj właściwości dla wszystkich widocznych kontrolek Windows Forms, aby zdefiniować tryb dokowania.  
  
> [!NOTE]
> Kontrolki są zadokowane w odwrotnej kolejności z.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Właściwość współdziała zwłaściwością<xref:System.Windows.Forms.Control.AutoSize%2A> . Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Aby zadokować formant  
  
1. Wybierz kontrolkę, która ma zostać zadokowany.  
  
2. W okno właściwości kliknij strzałkę znajdującą się po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.  
  
     Wyświetlany jest Edytor, który pokazuje serię pól reprezentujących krawędzie i orodek formularza.  
  
3. Kliknij przycisk, który reprezentuje krawędź formularza, w której chcesz zadokować formant. Aby wypełnić zawartość formularza kontrolki lub kontrolki kontenera, kliknij pole środkowe. Kliknij pozycję **(brak)** , aby wyłączyć dokowanie.  
  
     Rozmiar formantu jest automatycznie zmieniany w celu dopasowania do granic zadokowanej krawędzi.  
  
    > [!NOTE]
    > Dziedziczone kontrolki muszą `Protected` mieć możliwość zadokowania. Aby zmienić poziom dostępu kontrolki, ustaw jej właściwość **modyfikującą** w okno właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w kontrolce FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: Kontrolki kotwicowe na Windows Forms](how-to-anchor-controls-on-windows-forms.md)
