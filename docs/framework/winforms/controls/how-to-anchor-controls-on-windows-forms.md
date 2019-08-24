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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94fa6fe90e5583a3bfecf376af59d53f6d8528af
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987492"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Instrukcje: Kontrolki kotwicowe na Windows Forms

Jeśli projektujesz formularz, którego użytkownik może zmienić rozmiar w czasie wykonywania, kontrolki w formularzu powinny zmieniać rozmiar i zmienić położenie odpowiednio. Aby dynamicznie zmieniać rozmiar kontrolek przy użyciu formularza, można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantów Windows Forms. <xref:System.Windows.Forms.Control.Anchor%2A> Właściwość definiuje pozycję kotwicy dla kontrolki. Gdy kontrolka jest zakotwiczona do formularza i zmieniany jest rozmiar formularza, formant utrzymuje odległość między kontrolką a położeniami zakotwiczenia. Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formant, który jest zakotwiczony do lewej, prawej i dolnej krawędzi formularza, w miarę zmieniania rozmiaru <xref:System.Windows.Forms.TextBox> formularza kontrolka zmienia rozmiar w poziomie tak, aby zachować taką samą odległość od prawej i lewej strony formularza. Ponadto kontrolka sama rozmieszczenie w pionie, tak aby jej lokalizacja była zawsze taka sama jak odległość od dolnej krawędzi formularza. Jeśli kontrolka nie jest zakotwiczona i rozmiar formularza zostanie zmieniony, pozycja kontrolki względem krawędzi formularza zostanie zmieniona.

<xref:System.Windows.Forms.Control.Anchor%2A> Właściwość współdziała zwłaściwością<xref:System.Windows.Forms.Control.AutoSize%2A> . Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Zakotwiczenie kontrolki w formularzu

1. W programie Visual Studio Wybierz kontrolkę, którą chcesz zakotwiczyć.

    > [!NOTE]
    > Możesz zakotwiczyć wiele kontrolek jednocześnie, naciskając klawisz CTRL, klikając poszczególne kontrolki, aby je zaznaczyć, a następnie postępując zgodnie z resztą tej procedury.

2. W oknie **Właściwości** kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.

     Wyświetlany jest Edytor, który pokazuje krzyżyk.

3. Aby ustawić kotwicę, kliknij górną, lewą, prawą lub dolną sekcję krzyżyka.

     Kontrolki są domyślnie zakotwiczone na górze i w lewo.

4. Aby wyczyścić stronę kontrolki, która została zakotwiczenie, kliknij tę ramię krzyżowo.

5. Aby zamknąć <xref:System.Windows.Forms.Control.Anchor%2A> Edytor właściwości, <xref:System.Windows.Forms.Control.Anchor%2A> kliknij ponownie nazwę właściwości.

Gdy formularz zostanie wyświetlony w czasie wykonywania, zmienia rozmiar kontrolki tak, aby pozostawał w tej samej odległości od krawędzi formularza. Odległość od zakotwiczonej krawędzi zawsze pozostaje taka sama jak odległość zdefiniowana, gdy kontrolka jest umieszczona w Projektant formularzy systemu Windows.

> [!NOTE]
> Niektóre kontrolki, takie jak <xref:System.Windows.Forms.ComboBox> kontrolka, mają limit wysokości. Zakotwiczenie kontrolki do dołu jej formularza lub kontenera nie może wymusić przekroczenia limitu wysokości formantu.

Dziedziczone kontrolki muszą `Protected` mieć możliwość zakotwiczenia. Aby zmienić poziom dostępu kontrolki, ustaw jej `Modifiers` właściwość w oknie **Właściwości** .

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: Zadokuj kontrolki na Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Określanie układu formantów Windows Forms z dopełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md)
