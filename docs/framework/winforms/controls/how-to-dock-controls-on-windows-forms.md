---
title: 'Instrukcje: dokowanie kontrolek w Formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58b61af306385a245bedf16e370e6830c370a622
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987488"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Instrukcje: Zadokuj kontrolki na Windows Forms

Możesz zadokować kontrolki do krawędzi formularza lub popełniać kontener formantu (formularz lub kontrolka kontenera). Na przykład Eksplorator Windows dockuje swój <xref:System.Windows.Forms.TreeView> formant po lewej stronie okna i jego <xref:System.Windows.Forms.ListView> kontrolkę po prawej stronie okna. <xref:System.Windows.Forms.Control.Dock%2A> Użyj właściwości dla wszystkich widocznych kontrolek Windows Forms, aby zdefiniować tryb dokowania.

> [!NOTE]
> Kontrolki są zadokowane w odwrotnej kolejności z.

<xref:System.Windows.Forms.Control.Dock%2A> Właściwość współdziała zwłaściwością<xref:System.Windows.Forms.Control.AutoSize%2A> . Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).

## <a name="to-dock-a-control"></a>Aby zadokować formant

1. W programie Visual Studio Wybierz kontrolkę, która ma zostać zadokowany.

2. W oknie **Właściwości** kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.

   Wyświetlany jest Edytor, który pokazuje serię pól reprezentujących krawędzie i orodek formularza.

3. Kliknij przycisk, który reprezentuje krawędź formularza, w której chcesz zadokować formant. Aby wypełnić zawartość formularza kontrolki lub kontrolki kontenera, kliknij pole środkowe. Kliknij pozycję **(brak)** , aby wyłączyć dokowanie.

   Rozmiar formantu jest automatycznie zmieniany w celu dopasowania do granic zadokowanej krawędzi.

   > [!NOTE]
   > Dziedziczone kontrolki muszą `Protected` mieć możliwość zadokowania. Aby zmienić poziom dostępu kontrolki, ustaw jej właściwość **modyfikującą** w oknie **Właściwości** .

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w kontrolce FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: Kontrolki kotwicowe na Windows Forms](how-to-anchor-controls-on-windows-forms.md)
