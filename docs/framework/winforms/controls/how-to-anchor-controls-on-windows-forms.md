---
title: 'Instrukcje: kotwiczenie kontrolek na formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: b48761bda2baad4f7d1e6db9b41d73d6d54bc081
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211271"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Instrukcje: kotwiczenie kontrolek na formularzach systemu Windows

Projektując formularz, który użytkownik może zmienić rozmiar w czasie wykonywania, kontrolek w formularzu należy zmienić rozmiar i zmienić położenie prawidłowo. Aby zmienić rozmiar kontrolki dynamicznej z formularza, można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolek formularzy Windows Forms. <xref:System.Windows.Forms.Control.Anchor%2A> Właściwość definiuje pozycji zakotwiczenia dla formantu. Gdy formant jest zakotwiczona do formularza i rozmiarów formularza, formant zachowuje odległość między formantem i pozycji zakotwiczenia. Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formant, który jest zakotwiczona lewy, prawy i dolną krawędzią formularza, jak rozmiarów formularza <xref:System.Windows.Forms.TextBox> kontrolować zmiany rozmiaru w poziomie, tak, aby utrzymuje tej samej odległości od lewej i prawej strony formularza. Ponadto kontrolka umieszcza się w pionie tak, aby jego lokalizacja jest zawsze tej samej odległości od dolnej krawędzi formularza. Jeśli formant nie jest zakotwiczona rozmiarów formularza, położenie formantu względem krawędzi formularza jest zmieniany.

<xref:System.Windows.Forms.Control.Anchor%2A> Właściwość wchodzi w interakcję z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości. Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Zakotwicz formant w formularzu

1. W programie Visual Studio wybierz formant, który chcesz, aby móc zakotwiczyć.

    > [!NOTE]
    > Wiele kontrolek można zakotwiczyć jednocześnie, naciskając klawisz CTRL, klikając każdy formant, aby go zaznaczyć, a następnie postępuj zgodnie z pozostałą część tej procedury.

2. W **właściwości** okna, kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.

     Zostanie wyświetlony Edytor, pokazujący krzyżyk.

3. Aby ustawić elementu zakotwiczenia, kliknij lewym górnym rogu, po prawej stronie i dolną sekcję między środowiskami.

     Kontrolki jest zakotwiczona u góry i pozostanie domyślnie.

4. Aby wyczyścić boku formant, który został zakotwiczone, kliknij ten arm między środowiskami.

5. Aby zamknąć <xref:System.Windows.Forms.Control.Anchor%2A> Edytor właściwości, kliknij przycisk <xref:System.Windows.Forms.Control.Anchor%2A> ponownie nazwę właściwości.

Gdy formularz jest wyświetlana w czasie wykonywania, pozostaje osiągniesz idealną pozycję w tej samej odległości od krawędzi formularza zmienia rozmiar kontrolki. Odległość od zakotwiczonej krawędzi zawsze pozostaje taki sam jak odległości określonej, gdy kontrolka jest umieszczany w Windows Forms Designer.

> [!NOTE]
> Niektóre kontrolki, takie jak <xref:System.Windows.Forms.ComboBox> sterowania, ma ograniczenia do ich wysokość. Zakotwiczanie formantu do dołu formularza lub kontener nie może wymusić kontroli przekroczenie limitu wysokości.

Musi być dziedziczone formantów `Protected` mogli jest zakotwiczona. Aby zmienić poziom dostępu formantu, ustaw jego `Modifiers` właściwość **właściwości** okna.

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: Dokowanie formantów na formularzach Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Układania Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)
