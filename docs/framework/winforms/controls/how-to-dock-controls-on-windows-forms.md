---
title: Dokowanie kontrolek
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02f1c26dcb322a39c41781c83d8c820bd2fd27e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745524"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Instrukcje: dokowanie formantów na Windows Forms

Możesz zadokować kontrolki do krawędzi formularza lub popełniać kontener formantu (formularz lub kontrolka kontenera). Na przykład Eksplorator Windows dockuje jego formant <xref:System.Windows.Forms.TreeView> po lewej stronie okna i kontrolce <xref:System.Windows.Forms.ListView> po prawej stronie okna. Użyj właściwości <xref:System.Windows.Forms.Control.Dock%2A> dla wszystkich widocznych Windows Forms formantów, aby zdefiniować tryb dokowania.

> [!NOTE]
> Kontrolki są zadokowane w odwrotnej kolejności z.

Właściwość <xref:System.Windows.Forms.Control.Dock%2A> współdziała z właściwością <xref:System.Windows.Forms.Control.AutoSize%2A>. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).

## <a name="to-dock-a-control"></a>Aby zadokować formant

1. W programie Visual Studio Wybierz kontrolkę, która ma zostać zadokowany.

2. W oknie **Właściwości** kliknij strzałkę po prawej stronie właściwości <xref:System.Windows.Forms.Control.Dock%2A>.

   Wyświetlany jest Edytor, który pokazuje serię pól reprezentujących krawędzie i orodek formularza.

3. Kliknij przycisk, który reprezentuje krawędź formularza, w której chcesz zadokować formant. Aby wypełnić zawartość formularza kontrolki lub kontrolki kontenera, kliknij pole środkowe. Kliknij pozycję **(brak)** , aby wyłączyć dokowanie.

   Rozmiar formantu jest automatycznie zmieniany w celu dopasowania do granic zadokowanej krawędzi.

   > [!NOTE]
   > Dziedziczone kontrolki muszą być `Protected`, aby mogły być zadokowane. Aby zmienić poziom dostępu kontrolki, ustaw jej właściwość **modyfikującą** w oknie **Właściwości** .

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
- [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms](how-to-anchor-controls-on-windows-forms.md)
