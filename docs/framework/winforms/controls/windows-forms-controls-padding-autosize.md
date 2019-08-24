---
title: 'Przewodnik: tworzenie kontrolek formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf0c6495b89033e75c27a1ff0cbceaff9d85f34
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987171"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Przewodnik: Określanie układu formantów z dopełnieniem, marginesami i właściwością AutoSize

Precyzyjne rozmieszczenie kontrolek w formularzu jest wysokim priorytetem dla wielu aplikacji. **Projektant formularzy systemu Windows** w programie Visual Studio oferuje wiele narzędzi do układu. Trzy z najważniejszych są <xref:System.Windows.Forms.Control.Margin%2A>właściwościami, <xref:System.Windows.Forms.Control.Padding%2A>i <xref:System.Windows.Forms.Control.AutoSize%2A> , które są obecne na wszystkich Windows Formsych kontrolkach.

<xref:System.Windows.Forms.Control.Margin%2A> Właściwość definiuje odstęp wokół formantu, który utrzymuje inne kontrolki o określonej odległości od obramowań kontrolek.

Właściwość definiuje miejsce wewnątrz kontrolki, która utrzymuje zawartość kontrolki (na przykład wartość jej <xref:System.Windows.Forms.Control.Text%2A> właściwości) określoną odległość od obramowań kontrolek. <xref:System.Windows.Forms.Control.Padding%2A>

Na poniższej ilustracji przedstawiono <xref:System.Windows.Forms.Control.Padding%2A> właściwości i <xref:System.Windows.Forms.Control.Margin%2A> kontrolki.

![Uzupełnienie i margines dla kontrolek Windows Forms](./media/vs-winformpadmargin.gif)

<xref:System.Windows.Forms.Control.AutoSize%2A> Właściwość nakazuje formantowi automatyczne dopasowanie rozmiaru do jego zawartości. Zmiana rozmiaru nie zmieni się tak, aby była mniejsza niż wartość oryginalnej <xref:System.Windows.Forms.Control.Size%2A> właściwości, i będzie uwzględniać wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

1. W programie Visual Studio Utwórz projekt **aplikacji systemu Windows** o `LayoutExample`nazwie.

2. Wybierz formularz w **Projektant formularzy systemu Windows**.

## <a name="set-margins-for-controls"></a>Ustaw marginesy dla kontrolek

Możesz ustawić domyślną odległość między kontrolkami przy użyciu <xref:System.Windows.Forms.Control.Margin%2A> właściwości. Gdy przesuwasz formant wystarczająco blisko do innej kontrolki, zobaczysz snapline, który pokazuje marginesy dla dwóch kontrolek. Przenoszony formant zostanie również przyciągnięty do odległości zdefiniowanej przez marginesy.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Rozmieszczanie kontrolek w formularzu przy użyciu właściwości Margin

1. Przeciągnij dwie <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do formularza.

2. Wybierz jedną z <xref:System.Windows.Forms.Button> kontrolek i przenieś ją blisko siebie, aż do momentu niemal dotknięcia.

   Obserwuj snapline występujące między nimi. Ta odległość jest sumą <xref:System.Windows.Forms.Control.Margin%2A> wartości dwóch kontrolek. Kontrolka, którą przenosisz, zostanie przyciągnięta do tej odległości. Aby uzyskać szczegółowe informacje [, zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)przy użyciu linii wyrównania.

3. <xref:System.Windows.Forms.Padding.All%2A> <xref:System.Windows.Forms.Control.Margin%2A>Zmień właściwość jednego z formantów, rozwijając wpis w oknie właściwości i ustawiając właściwość na 20. <xref:System.Windows.Forms.Control.Margin%2A>

4. Wybierz jedną z <xref:System.Windows.Forms.Button> formantów i przenieś ją blisko siebie.

   Snapline definiujący sumę wartości marginesu jest dłuższy i że formant jest przyciągany do większej odległości od innej kontrolki.

5. <xref:System.Windows.Forms.Padding.Top%2A> <xref:System.Windows.Forms.Control.Margin%2A>Zmień właściwość zaznaczonego formantu, rozwijając wpis w oknie właściwości i ustawiając właściwość na 5. <xref:System.Windows.Forms.Control.Margin%2A>

6. Przenieś wybraną kontrolkę poniżej innej kontrolki i sprawdź, czy snapline jest krótszy. Przenieś wybraną kontrolkę z lewej strony innej kontrolki i sprawdź, czy snapline zachowuje wartość zaobserwowanej w kroku 4.

7. Można ustawić każdą <xref:System.Windows.Forms.Control.Margin%2A> z aspektów właściwości <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Left%2A> <xref:System.Windows.Forms.Padding.Right%2A> <xref:System.Windows.Forms.Padding.Bottom%2A>,,,, do różnych <xref:System.Windows.Forms.Padding.All%2A> wartości lub można ustawić dla nich wszystkie do tej samej wartości właściwości.

## <a name="set-padding-for-controls"></a>Ustaw uzupełnienie dla kontrolek

Aby osiągnąć dokładny układ wymagany dla aplikacji, formanty często zawierają kontrolki podrzędne. Aby określić bliskość obramowania kontrolki podrzędnej do obramowania kontrolki nadrzędnej, należy użyć <xref:System.Windows.Forms.Control.Padding%2A> właściwości kontrolki nadrzędnej w połączeniu z <xref:System.Windows.Forms.Control.Margin%2A> właściwością kontrolki podrzędnej. Właściwość służy również do kontrolowania bliskości zawartości kontrolki (na przykład <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Text%2A> właściwości kontrolki) do jej obramowań. <xref:System.Windows.Forms.Control.Padding%2A>

### <a name="arrange-controls-on-your-form-using-padding"></a>Rozmieszczanie kontrolek w formularzu przy użyciu dopełnienia

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button>

2. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości kontrolki na **true**.

3. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Padding.All%2A> Zmień właściwość, rozszerzając wpis w oknie **Właściwości** i ustawiając właściwość na **5.** <xref:System.Windows.Forms.Control.Padding%2A>

   Kontrolka rozwija się, aby zapewnić miejsce na nowe uzupełnienie.

4. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.GroupBox> Przeciągnij kontrolkę z <xref:System.Windows.Forms.GroupBox> przybornika do kontrolki. <xref:System.Windows.Forms.Button> Ustaw kontrolkę tak, aby była opróżniana z prawego dolnego rogu <xref:System.Windows.Forms.GroupBox> kontrolki. <xref:System.Windows.Forms.Button>

   Obserwuj linii wyrównania, który pojawia się jako <xref:System.Windows.Forms.Button> formant zbliża się do dolnego i prawego <xref:System.Windows.Forms.GroupBox> obramowania formantu. Te linii wyrównania odpowiadają <xref:System.Windows.Forms.Control.Margin%2A> właściwości <xref:System.Windows.Forms.Button>.

5. <xref:System.Windows.Forms.GroupBox> Zmień <xref:System.Windows.Forms.Control.Padding%2A> właściwość kontrolki, rozszerzając<xref:System.Windows.Forms.Padding.All%2A> wpis w oknie właściwości i ustawiając właściwość na 20. <xref:System.Windows.Forms.Control.Padding%2A>

6. Zaznacz kontrolkę <xref:System.Windows.Forms.GroupBox> w kontrolce i przenieś ją do środka <xref:System.Windows.Forms.GroupBox>. <xref:System.Windows.Forms.Button>

   Linii wyrównania pojawia się na większej odległości od obramowania <xref:System.Windows.Forms.GroupBox> kontrolki. <xref:System.Windows.Forms.Button> Ta odległość jest sumą <xref:System.Windows.Forms.Control.Margin%2A> właściwościkontrolki<xref:System.Windows.Forms.GroupBox> i właściwościkontrolki.<xref:System.Windows.Forms.Control.Padding%2A>

## <a name="size-controls-automatically"></a>Automatyczne sterowanie rozmiarem

W niektórych aplikacjach rozmiar kontrolki nie będzie taki sam w czasie wykonywania, jak w czasie projektowania. Tekst <xref:System.Windows.Forms.Button> kontrolki, na przykład, może być pobrany z bazy danych, a jej długość nie jest znana z góry.

Gdy właściwość jest ustawiona na `true`, formant zmieni swój rozmiar do zawartości. <xref:System.Windows.Forms.Control.AutoSize%2A> Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Rozmieszczanie kontrolek w formularzu przy użyciu właściwości AutoSize

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button>

2. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości kontrolki na **true**.

3. <xref:System.Windows.Forms.Button> Zmiana właściwości<xref:System.Windows.Forms.Control.Text%2A> kontrolki na **ten przycisk ma długi ciąg dla właściwości text**.

   Po zatwierdzeniu zmiany <xref:System.Windows.Forms.Button> rozmiar formantu zmienia się w celu dopasowania do nowego tekstu.

4. Przeciągnij inny <xref:System.Windows.Forms.Button> formant z **przybornika** do formularza.

5. <xref:System.Windows.Forms.Button> Zmień Właściwość<xref:System.Windows.Forms.Control.Text%2A> kontrolki na "**ten przycisk ma długi ciąg dla swojej właściwości text".**

   Gdy zatwierdzisz zmianę, <xref:System.Windows.Forms.Button> formant nie zmieni rozmiaru, a tekst zostanie obcięty przez prawą krawędź formantu.

6. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Padding.All%2A> Zmień właściwość, rozszerzając wpis w oknie **Właściwości** i ustawiając właściwość na **5.** <xref:System.Windows.Forms.Control.Padding%2A>

   Tekst w części wewnętrznej kontrolki jest obcinany na wszystkich czterech stronach.

7. <xref:System.Windows.Forms.Button> Zmień Właściwość<xref:System.Windows.Forms.Control.AutoSize%2A> kontrolki na **true**.

   <xref:System.Windows.Forms.Button> Kontrolka zmienia rozmiar siebie tak, aby obejmowała cały ciąg. Ponadto dopełnienie zostało dodane wokół tekstu, co sprawia, <xref:System.Windows.Forms.Button> że kontrolka rozszerza się we wszystkich czterech kierunkach.

8. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button> Umieść ją w prawym dolnym rogu formularza.

9. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości kontrolki na **true**.

10. <xref:System.Windows.Forms.Button> Ustaw Właściwość<xref:System.Windows.Forms.Control.Anchor%2A> kontrolki na <xref:System.Windows.Forms.AnchorStyles.Right>,. <xref:System.Windows.Forms.AnchorStyles.Bottom>

11. <xref:System.Windows.Forms.Button> Zmień Właściwość<xref:System.Windows.Forms.Control.Text%2A> kontrolki na "**ten przycisk ma długi ciąg dla swojej właściwości text".**

   Po zatwierdzeniu zmiany rozmiar formantu zmienia <xref:System.Windows.Forms.Button> się w kierunku lewej strony. Ogólnie rzecz biorąc, automatyczne określanie rozmiaru powoduje zwiększenie rozmiaru kontrolki w kierunku przeciwnym do jego <xref:System.Windows.Forms.Control.Anchor%2A> ustawienia właściwości.

## <a name="autosize-and-autosizemode-properties"></a>Właściwości AutoSize i AutoSizeMode

 Niektóre formanty obsługują `AutoSizeMode` właściwość, która daje dokładniejszą kontrolę nad zachowaniem automatycznej zmiany rozmiarów formantu.

### <a name="use-the-autosizemode-property"></a>Użyj właściwości AutoSizeMode

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Panel>

2. Ustaw wartość <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości kontrolki na **wartość true**.

3. Przeciągnij kontrolkę z <xref:System.Windows.Forms.Panel> przybornika do kontrolki. <xref:System.Windows.Forms.Button>

4. Umieść formant <xref:System.Windows.Forms.Button> w prawym dolnym rogu <xref:System.Windows.Forms.Panel> kontrolki.

5. <xref:System.Windows.Forms.Panel> Zaznacz kontrolkę i Pochwyć prawy dolny uchwyt zmiany rozmiarów. Zmień rozmiar <xref:System.Windows.Forms.Panel> kontrolki na większy i mniejszy.

   > [!NOTE]
   > Można swobodnie zmieniać rozmiar <xref:System.Windows.Forms.Panel> kontrolki, ale nie można jej zmienić na mniejszą niż pozycja <xref:System.Windows.Forms.Button> prawego dolnego rogu kontrolki. To zachowanie jest określone przez wartość `AutoSizeMode` domyślną właściwości. <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>

6. Ustaw wartość <xref:System.Windows.Forms.Panel> `AutoSizeMode` właściwości kontrolki na <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.

   Rozmiar kontrolki, aby <xref:System.Windows.Forms.Button> objawiać formant. <xref:System.Windows.Forms.Panel> Nie można zmienić rozmiaru <xref:System.Windows.Forms.Panel> formantu.

7. Przeciągnij formant w kierunku lewego górnego rogu <xref:System.Windows.Forms.Panel> kontrolki. <xref:System.Windows.Forms.Button>

   Kontrolka zmienia rozmiar <xref:System.Windows.Forms.Button> na nową pozycję kontrolki. <xref:System.Windows.Forms.Panel>

## <a name="next-steps"></a>Następne kroki

Istnieje wiele innych funkcji układu służących do porządkowania formantów w aplikacjach Windows Forms. Oto kilka kombinacji, które możesz wypróbować:

- Utwórz formularz przy użyciu <xref:System.Windows.Forms.TableLayoutPanel> kontrolki. Aby uzyskać szczegółowe informacje [, zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)użyciu TableLayoutPanel. Spróbuj zmienić wartości <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Control.Padding%2A> właściwości kontrolki <xref:System.Windows.Forms.Control.Margin%2A> , a także właściwość w jej kontrolkach podrzędnych.

- Wypróbuj ten sam eksperyment przy użyciu <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki. Aby uzyskać szczegółowe informacje [, zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)użyciu FlowLayoutPanel.

- Eksperymentuj z dokowaniem formantów podrzędnych w <xref:System.Windows.Forms.Panel> kontrolce. Właściwość jest bardziej ogólnym warunkiem realizacji <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> właściwości i można ją zaspokoić, umieszczając kontrolkę podrzędną w <xref:System.Windows.Forms.Panel> kontrolce i ustawiając <xref:System.Windows.Forms.Control.Dock%2A> właściwość kontrolki podrzędnej na <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Panel> Ustaw Właściwość<xref:System.Windows.Forms.Control.Padding%2A> kontrolki na różne wartości i zanotuj efekt.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
