---
title: 'Porady: kotwiczenie formantów na formularzach systemu Windows'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15f12cb0d389344351c4ddf97ee9db37882de460
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459682"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Instrukcje: kontrolki kotwicowe na Windows Forms

Jeśli projektujesz formularz, którego użytkownik może zmienić rozmiar w czasie wykonywania, kontrolki w formularzu powinny zmieniać rozmiar i zmienić położenie odpowiednio. Aby dynamicznie zmieniać rozmiar kontrolek przy użyciu formularza, można użyć właściwości <xref:System.Windows.Forms.Control.Anchor%2A> Windows Forms kontrolek. Właściwość <xref:System.Windows.Forms.Control.Anchor%2A> definiuje położenie zakotwiczenia dla kontrolki. Gdy kontrolka jest zakotwiczona do formularza i zmieniany jest rozmiar formularza, formant utrzymuje odległość między kontrolką a położeniami zakotwiczenia. Na przykład jeśli masz formant <xref:System.Windows.Forms.TextBox>, który jest zakotwiczony w lewej, prawej i dolnej części formularza, w miarę zmieniania rozmiaru formularza <xref:System.Windows.Forms.TextBox> kontrolka zmienia rozmiar w poziomie tak, aby zachować taką samą odległość od prawej i lewej strony formularza. Ponadto kontrolka sama rozmieszczenie w pionie, tak aby jej lokalizacja była zawsze taka sama jak odległość od dolnej krawędzi formularza. Jeśli kontrolka nie jest zakotwiczona i rozmiar formularza zostanie zmieniony, pozycja kontrolki względem krawędzi formularza zostanie zmieniona.

Właściwość <xref:System.Windows.Forms.Control.Anchor%2A> współdziała z właściwością <xref:System.Windows.Forms.Control.AutoSize%2A>. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Zakotwiczenie kontrolki w formularzu

1. W programie Visual Studio Wybierz kontrolkę, którą chcesz zakotwiczyć.

    > [!NOTE]
    > Możesz zakotwiczyć wiele kontrolek jednocześnie, naciskając klawisz CTRL, klikając poszczególne kontrolki, aby je zaznaczyć, a następnie postępując zgodnie z resztą tej procedury.

2. W oknie **Właściwości** kliknij strzałkę po prawej stronie właściwości <xref:System.Windows.Forms.Control.Anchor%2A>.

     Wyświetlany jest Edytor, który pokazuje krzyżyk.

3. Aby ustawić kotwicę, kliknij górną, lewą, prawą lub dolną sekcję krzyżyka.

     Kontrolki są domyślnie zakotwiczone na górze i w lewo.

4. Aby wyczyścić stronę kontrolki, która została zakotwiczenie, kliknij tę ramię krzyżowo.

5. Aby zamknąć Edytor właściwości <xref:System.Windows.Forms.Control.Anchor%2A>, kliknij ponownie nazwę właściwości <xref:System.Windows.Forms.Control.Anchor%2A>.

Gdy formularz zostanie wyświetlony w czasie wykonywania, zmienia rozmiar kontrolki tak, aby pozostawał w tej samej odległości od krawędzi formularza. Odległość od zakotwiczonej krawędzi zawsze pozostaje taka sama jak odległość zdefiniowana, gdy kontrolka jest umieszczona w Projektant formularzy systemu Windows.

> [!NOTE]
> Niektóre kontrolki, takie jak kontrolka <xref:System.Windows.Forms.ComboBox>, mają limit wysokości. Zakotwiczenie kontrolki do dołu jej formularza lub kontenera nie może wymusić przekroczenia limitu wysokości formantu.

Kontrolki dziedziczone muszą być `Protected`, aby mogły być zakotwiczone. Aby zmienić poziom dostępu kontrolki, ustaw jej Właściwość `Modifiers` w oknie **Właściwości** .

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Instrukcje: dokowanie kontrolek na formularzach Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)
