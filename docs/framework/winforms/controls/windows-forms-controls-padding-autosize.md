---
title: 'Wskazówki: tworzenie formantów formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76c880c208355b01d0fbaf46cf58091ad147846b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460599"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Przewodnik: Określanie układu formantów z dopełnieniem, marginesami i właściwością AutoSize

Precyzyjne rozmieszczenie kontrolek w formularzu jest wysokim priorytetem dla wielu aplikacji. **Projektant formularzy systemu Windows** w programie Visual Studio oferuje wiele narzędzi do układu. Trzy najważniejsze są właściwościami <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>i <xref:System.Windows.Forms.Control.AutoSize%2A>, które znajdują się na wszystkich Windows Formsch kontrolek.

Właściwość <xref:System.Windows.Forms.Control.Margin%2A> definiuje odstęp wokół formantu, który utrzymuje inne kontrolki o określonej odległości od obramowań kontrolek.

Właściwość <xref:System.Windows.Forms.Control.Padding%2A> definiuje miejsce wewnątrz kontrolki, która utrzymuje zawartość kontrolki (na przykład wartość właściwości <xref:System.Windows.Forms.Control.Text%2A>) określoną odległość od obramowań kontrolek.

Na poniższej ilustracji przedstawiono <xref:System.Windows.Forms.Control.Padding%2A> i <xref:System.Windows.Forms.Control.Margin%2A> właściwości formantu.

![Uzupełnienie i margines dla kontrolek Windows Forms](./media/vs-winformpadmargin.gif)

Właściwość <xref:System.Windows.Forms.Control.AutoSize%2A> instruuje formant, aby automatycznie zmieniał rozmiar do jego zawartości. Zmiana rozmiaru nie zmieni się na wartość mniejszą niż oryginalna Właściwość <xref:System.Windows.Forms.Control.Size%2A> i będzie uwzględniać wartość właściwości <xref:System.Windows.Forms.Control.Padding%2A>.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

1. W programie Visual Studio Utwórz projekt **aplikacji systemu Windows** o nazwie `LayoutExample`.

2. Wybierz formularz w **Projektant formularzy systemu Windows**.

## <a name="set-margins-for-controls"></a>Ustaw marginesy dla kontrolek

Możesz ustawić domyślną odległość między kontrolkami przy użyciu właściwości <xref:System.Windows.Forms.Control.Margin%2A>. Gdy przesuwasz formant wystarczająco blisko do innej kontrolki, zobaczysz snapline, który pokazuje marginesy dla dwóch kontrolek. Przenoszony formant zostanie również przyciągnięty do odległości zdefiniowanej przez marginesy.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Rozmieszczanie kontrolek w formularzu przy użyciu właściwości Margin

1. Przeciągnij dwie <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do formularza.

2. Wybierz jedną z formantów <xref:System.Windows.Forms.Button> i przenieś ją w dół, aż do momentu niemal dotknięcia.

   Obserwuj snapline występujące między nimi. Ta odległość jest sumą dwóch wartości <xref:System.Windows.Forms.Control.Margin%2A> kontrolek. Kontrolka, którą przenosisz, zostanie przyciągnięta do tej odległości. Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

3. Zmień właściwość <xref:System.Windows.Forms.Control.Margin%2A> jednego z formantów, rozszerzając wpis <xref:System.Windows.Forms.Control.Margin%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.All%2A> na **20**.

4. Wybierz jedną z formantów <xref:System.Windows.Forms.Button> i przenieś ją blisko siebie.

   Snapline definiujący sumę wartości marginesu jest dłuższy i że formant jest przyciągany do większej odległości od innej kontrolki.

5. Zmień właściwość <xref:System.Windows.Forms.Control.Margin%2A> wybranego formantu, rozszerzając wpis <xref:System.Windows.Forms.Control.Margin%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.Top%2A> na **5**.

6. Przenieś wybraną kontrolkę poniżej innej kontrolki i sprawdź, czy snapline jest krótszy. Przenieś wybraną kontrolkę z lewej strony innej kontrolki i sprawdź, czy snapline zachowuje wartość zaobserwowanej w kroku 4.

7. Można ustawić każdą z aspektów <xref:System.Windows.Forms.Control.Margin%2A> właściwości, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, do różnych wartości lub ustawić dla nich wszystkie wartości z właściwością <xref:System.Windows.Forms.Padding.All%2A>.

## <a name="set-padding-for-controls"></a>Ustaw uzupełnienie dla kontrolek

Aby osiągnąć dokładny układ wymagany dla aplikacji, formanty często zawierają kontrolki podrzędne. Gdy chcesz określić bliskość obramowania kontrolki podrzędnej do obramowania kontrolki nadrzędnej, użyj właściwości <xref:System.Windows.Forms.Control.Padding%2A> kontrolki nadrzędnej w połączeniu z właściwością <xref:System.Windows.Forms.Control.Margin%2A> formantu podrzędnego. Właściwość <xref:System.Windows.Forms.Control.Padding%2A> jest również używana do kontrolowania bliskości zawartości kontrolki (na przykład właściwości <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button>) do jej obramowań.

### <a name="arrange-controls-on-your-form-using-padding"></a>Rozmieszczanie kontrolek w formularzu przy użyciu dopełnienia

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz.

2. Zmień wartość właściwości <xref:System.Windows.Forms.Control.AutoSize%2A> kontrolki <xref:System.Windows.Forms.Button> na **wartość true**.

3. Zmień właściwość <xref:System.Windows.Forms.Control.Padding%2A>, rozszerzając wpis <xref:System.Windows.Forms.Control.Padding%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.All%2A> na **5**.

   Kontrolka rozwija się, aby zapewnić miejsce na nowe uzupełnienie.

4. Przeciągnij kontrolkę <xref:System.Windows.Forms.GroupBox> z **przybornika** na formularz. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.GroupBox>. Umieść kontrolkę <xref:System.Windows.Forms.Button>, tak aby była opróżniana z prawego dolnego rogu kontrolki <xref:System.Windows.Forms.GroupBox>.

   Obserwuj linii wyrównania, który pojawia się jako formant <xref:System.Windows.Forms.Button>, zbliża się do dolnego i prawego obramowania kontrolki <xref:System.Windows.Forms.GroupBox>. Te linii wyrównania odpowiadają właściwości <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Button>.

5. Zmień właściwość <xref:System.Windows.Forms.Control.Padding%2A> kontrolki <xref:System.Windows.Forms.GroupBox>, rozszerzając wpis <xref:System.Windows.Forms.Control.Padding%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.All%2A> na **20**.

6. Wybierz kontrolkę <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.GroupBox> i przenieś ją do środka <xref:System.Windows.Forms.GroupBox>.

   Linii wyrównania pojawia się na większej odległości od obramowań kontrolki <xref:System.Windows.Forms.GroupBox>. Ta odległość jest sumą właściwości <xref:System.Windows.Forms.Control.Margin%2A> kontrolki <xref:System.Windows.Forms.Button> i właściwości <xref:System.Windows.Forms.Control.Padding%2A> kontrolki <xref:System.Windows.Forms.GroupBox>.

## <a name="size-controls-automatically"></a>Automatyczne sterowanie rozmiarem

W niektórych aplikacjach rozmiar kontrolki nie będzie taki sam w czasie wykonywania, jak w czasie projektowania. Tekst kontrolki <xref:System.Windows.Forms.Button>, na przykład, może zostać pobrany z bazy danych, a jej długość nie jest znana z góry.

Gdy właściwość <xref:System.Windows.Forms.Control.AutoSize%2A> jest ustawiona na `true`, formant zmieni swój rozmiar na jego zawartość. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Rozmieszczanie kontrolek w formularzu przy użyciu właściwości AutoSize

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz.

2. Zmień wartość właściwości <xref:System.Windows.Forms.Control.AutoSize%2A> kontrolki <xref:System.Windows.Forms.Button> na **wartość true**.

3. Zmień właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button> na **ten przycisk ma długi ciąg dla właściwości text**.

   Po zatwierdzeniu zmiany rozmiar kontrolki <xref:System.Windows.Forms.Button> zmienia się w celu dopasowania do nowego tekstu.

4. Przeciągnij inną kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz.

5. Zmień właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button> na "**ten przycisk ma długi ciąg dla swojej właściwości text".**

   Gdy zatwierdzisz zmianę, formant <xref:System.Windows.Forms.Button> nie zmieni rozmiaru, a tekst zostanie obcięty przez prawą krawędź formantu.

6. Zmień właściwość <xref:System.Windows.Forms.Control.Padding%2A>, rozszerzając wpis <xref:System.Windows.Forms.Control.Padding%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.All%2A> na **5**.

   Tekst w części wewnętrznej kontrolki jest obcinany na wszystkich czterech stronach.

7. Zmień właściwość <xref:System.Windows.Forms.Control.AutoSize%2A> kontrolki <xref:System.Windows.Forms.Button> na **wartość true**.

   Kontrolka <xref:System.Windows.Forms.Button> zmienia rozmiar siebie tak, aby obejmowała cały ciąg. Ponadto dopełnienie zostało dodane wokół tekstu, co sprawia, że formant <xref:System.Windows.Forms.Button> rozszerza się we wszystkich czterech kierunkach.

8. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz. Umieść ją w prawym dolnym rogu formularza.

9. Zmień wartość właściwości <xref:System.Windows.Forms.Control.AutoSize%2A> kontrolki <xref:System.Windows.Forms.Button> na **wartość true**.

10. Ustaw właściwość <xref:System.Windows.Forms.Control.Anchor%2A> kontrolki <xref:System.Windows.Forms.Button> na <xref:System.Windows.Forms.AnchorStyles.Right><xref:System.Windows.Forms.AnchorStyles.Bottom>.

11. Zmień właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button> na "**ten przycisk ma długi ciąg dla swojej właściwości text".**

   Po zatwierdzeniu zmiany zmieni rozmiar kontrolki <xref:System.Windows.Forms.Button> na lewą stronę. Ogólnie rzecz biorąc, automatyczne określanie rozmiaru powoduje zwiększenie rozmiaru kontrolki w kierunku przeciwnym do ustawienia właściwości <xref:System.Windows.Forms.Control.Anchor%2A>.

## <a name="autosize-and-autosizemode-properties"></a>Właściwości AutoSize i AutoSizeMode

 Niektóre formanty obsługują Właściwość `AutoSizeMode`, co daje dokładniejszą kontrolę nad zachowaniem automatycznej zmiany rozmiarów formantu.

### <a name="use-the-autosizemode-property"></a>Użyj właściwości AutoSizeMode

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Panel> z **przybornika** na formularz.

2. Ustaw wartość właściwości <xref:System.Windows.Forms.Control.AutoSize%2A> kontrolki <xref:System.Windows.Forms.Panel> na **wartość true**.

3. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.Panel>.

4. Umieść formant <xref:System.Windows.Forms.Button> w prawym dolnym rogu kontrolki <xref:System.Windows.Forms.Panel>.

5. Wybierz kontrolkę <xref:System.Windows.Forms.Panel> i Pochwyć prawy dolny uchwyt zmiany rozmiarów. Zmień rozmiar kontrolki <xref:System.Windows.Forms.Panel> na większą i mniejszą.

   > [!NOTE]
   > Można swobodnie zmieniać rozmiar kontrolki <xref:System.Windows.Forms.Panel>, ale nie można jej zmienić na mniejszej niż pozycja prawego dolnego rogu kontrolki <xref:System.Windows.Forms.Button>. To zachowanie jest określone przez wartość domyślną właściwości `AutoSizeMode`, która jest <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.

6. Ustaw wartość właściwości `AutoSizeMode` kontrolki <xref:System.Windows.Forms.Panel> na <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.

   <xref:System.Windows.Forms.Panel> kontrolować rozmiary formantu <xref:System.Windows.Forms.Button>. Nie można zmienić rozmiaru kontrolki <xref:System.Windows.Forms.Panel>.

7. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> w kierunku lewego górnego rogu kontrolki <xref:System.Windows.Forms.Panel>.

   Kontrolka <xref:System.Windows.Forms.Panel> zmienia rozmiar na nową pozycję kontrolki <xref:System.Windows.Forms.Button>.

## <a name="next-steps"></a>Następne kroki

Istnieje wiele innych funkcji układu służących do porządkowania formantów w aplikacjach Windows Forms. Oto kilka kombinacji, które możesz wypróbować:

- Utwórz formularz przy użyciu kontrolki <xref:System.Windows.Forms.TableLayoutPanel>. Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Spróbuj zmienić wartości właściwości <xref:System.Windows.Forms.Control.Padding%2A> kontrolki <xref:System.Windows.Forms.TableLayoutPanel>, a także Właściwość <xref:System.Windows.Forms.Control.Margin%2A> w jej kontrolkach podrzędnych.

- Wypróbuj ten sam eksperyment przy użyciu kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>. Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

- Eksperymentuj z dokowaniem formantów podrzędnych w kontrolce <xref:System.Windows.Forms.Panel>. Właściwość <xref:System.Windows.Forms.Control.Padding%2A> jest bardziej ogólnym scenariuszem właściwości <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> i można ją zaspokoić, umieszczając formant podrzędny w kontrolce <xref:System.Windows.Forms.Panel> i ustawiając właściwość <xref:System.Windows.Forms.Control.Dock%2A> formantu podrzędnego na <xref:System.Windows.Forms.DockStyle.Fill>. Ustaw właściwość <xref:System.Windows.Forms.Control.Padding%2A> kontrolki <xref:System.Windows.Forms.Panel> na różne wartości i zanotuj efekt.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize, właściwość — omówienie](autosize-property-overview.md)
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
