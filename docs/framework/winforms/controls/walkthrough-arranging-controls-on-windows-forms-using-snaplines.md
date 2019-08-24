---
title: 'Przewodnik: rozmieszczanie kontrolek w formularzach systemu Windows za pomocą linii przyciągania'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 83f0365ffb7335cb67c729c5a113e550c119191a
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986998"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Przewodnik: Rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania

Precyzyjne rozmieszczenie kontrolek w formularzu jest wysokim priorytetem dla wielu aplikacji. Projektant formularzy systemu Windows zapewnia wiele narzędzi do układu. Jedną z najważniejszych <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkcji jest funkcja.

Linii wyrównania pokazują precyzyjną lokalizację kontrolek z innymi kontrolkami. Przedstawiono w nich również zalecane odległości między kontrolkami, jak określono w [wytycznych dotyczących interfejsu użytkownika systemu Windows](/windows/win32/uxguide/guidelines).

Linii wyrównania ułatwiają wyrównywanie kontrolek w celu wyraźnego, profesjonalnego wyglądu i zachowania (wyglądu i działania).

## <a name="create-the-project"></a>Utwórz projekt

1. W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie "SnaplineExample".

2. Wybierz formularz w projektancie formularzy.

## <a name="space-and-align-controls"></a>Kontrolki Space i align

Linii wyrównania umożliwiają dokładne i intuicyjne dostosowanie formantów w formularzu. Są one wyświetlane podczas przesuwania zaznaczonej kontrolki lub kontrolek blisko położenia, które byłyby wyrównane do innej kontrolki lub zestawu kontrolek. Wybór zostanie przyciągnięty do sugerowanej pozycji podczas przenoszenia jej poza inne kontrolki.

### <a name="to-arrange-controls-using-snaplines"></a>Aby rozmieścić kontrolki za pomocą linii wyrównania

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button>

2. <xref:System.Windows.Forms.Button> Przenieś formant do prawego dolnego rogu formularza. Zwróć uwagę na to, że linii wyrównania <xref:System.Windows.Forms.Button> pojawia się jako kontrolka zbliża się do dolnego i prawego obramowania formularza. Te linii wyrównania wyświetlają zalecaną odległość między obramowaniem kontrolki a formularzem.

3. <xref:System.Windows.Forms.Button> Przenieś kontrolkę wokół krawędzi formularza i zanotuj, gdzie pojawia się linii wyrównania. Po zakończeniu Przenieś <xref:System.Windows.Forms.Button> formant blisko środka formularza.

4. Przeciągnij inny <xref:System.Windows.Forms.Button> formant z **przybornika** do formularza.

5. Przenieś drugą <xref:System.Windows.Forms.Button> kontrolkę do momentu, aż będzie niemal poziom w pierwszej kolejności. Zwróć uwagę na snapline, który pojawia się w linii bazowej tekstu obu przycisków i Zauważ, że przenoszona kontrolka jest przyciągnięta do pozycji, która jest dokładnie na poziomie z inną kontrolką.

6. Przenieś drugi <xref:System.Windows.Forms.Button> formant do momentu, aż zostanie umieszczony bezpośrednio powyżej pierwszego. Zwróć uwagę na to, że linii wyrównania pojawia się wzdłuż lewej i prawej krawędzi obu przycisków i Zauważ, że przenoszona kontrolka jest przyciągnięta do położenia, które jest dokładnie wyrównane z inną kontrolką.

7. Wybierz jedną z <xref:System.Windows.Forms.Button> kontrolek i przenieś ją blisko siebie, aż do momentu niemal dotknięcia. Zwróć uwagę na snapline, który pojawia się między nimi. Ta odległość jest zalecaną odległością między obramowaniem kontrolek. Należy również zauważyć, że przenoszony formant przyciągnie do tego położenia.

8. Przeciągnij dwie <xref:System.Windows.Forms.Panel> kontrolki z **przybornika** do formularza.

9. Przenieś jeden z <xref:System.Windows.Forms.Panel> kontrolek do momentu, aż będzie niemal poziom w pierwszej kolejności. Zwróć uwagę na to, że linii wyrównania pojawia się wzdłuż górnej i dolnej krawędzi obu kontrolek, i Zauważ, że przenoszona kontrolka jest przyciągnięta do pozycji, która jest dokładnie na poziomie z inną kontrolką.

## <a name="align-to-form-and-container-margins"></a>Wyrównaj do postaci i marginesów kontenera

Linii wyrównania ułatwiają wyrównywanie kontrolek do marginesów i w spójny sposób.

1. Zaznacz jedną z <xref:System.Windows.Forms.Button> formantów i przenieś ją blisko prawej krawędzi formularza do momentu pojawienia się snapline. Odległość snapline od prawej krawędzi to suma <xref:System.Windows.Forms.Control.Margin%2A> właściwości kontrolki i wartości <xref:System.Windows.Forms.Control.Padding%2A> właściwości formularza.

   > [!NOTE]
   > Jeśli <xref:System.Windows.Forms.Control.Padding%2A> właściwość formularza jest ustawiona na 0, 0, 0, 0, Projektant formularzy systemu Windows daje formę <xref:System.Windows.Forms.Control.Padding%2A> cieniowanie wartości 9, 9, 9, 9. Aby zastąpić to zachowanie, przypisz wartość inną niż 0, 0, 0, 0.

2. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> właściwości kontrolki, rozszerzając <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.All%2A> wpis w oknie **Właściwości** i ustawiając właściwość na 0. Aby uzyskać szczegółowe informacje [, zobacz Przewodnik: Określanie układu formantów Windows Forms z uzupełnieniem, marginesami i właściwością](windows-forms-controls-padding-autosize.md)AutoSize.

3. <xref:System.Windows.Forms.Button> Przesuń formant blisko prawej krawędzi formularza do momentu pojawienia się snapline. Ta odległość jest teraz określona przez wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości formularza.

4. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.GroupBox>

5. Zmień wartość <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Control.Padding%2A> właściwości kontrolki, rozszerzając <xref:System.Windows.Forms.Control.Padding%2A> wpis w oknie **Właściwości** i ustawiając właściwość na wartość <xref:System.Windows.Forms.Padding.All%2A> 10.

6. Przeciągnij kontrolkę z <xref:System.Windows.Forms.GroupBox> przybornika do kontrolki. <xref:System.Windows.Forms.Button>

7. Przesuń formant blisko prawej krawędzi <xref:System.Windows.Forms.GroupBox> kontrolki do momentu pojawienia się snapline. <xref:System.Windows.Forms.Button> Przenieś kontrolkę <xref:System.Windows.Forms.GroupBox> wewnątrz kontrolki i zanotuj, gdzie pojawia się linii wyrównania. <xref:System.Windows.Forms.Button>

## <a name="align-to-grouped-controls"></a>Wyrównaj do kontrolek zgrupowanych

Możesz użyć linii wyrównania, aby wyrównać zgrupowane kontrolki, a także <xref:System.Windows.Forms.GroupBox> kontrolki w kontrolce.

1. Wybierz dwie kontrolki w formularzu. Przenieś zaznaczenie dookoła i zanotuj linii wyrównania, które pojawiają się między wyborem a innymi kontrolkami.

2. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.GroupBox>

3. Przeciągnij kontrolkę z <xref:System.Windows.Forms.GroupBox> przybornika do kontrolki. <xref:System.Windows.Forms.Button>

4. Zaznacz jedną z <xref:System.Windows.Forms.Button> formantów i przenieś ją <xref:System.Windows.Forms.GroupBox> wokół formantu. Zwróć uwagę na linii wyrównania, który pojawia się na krawędziach <xref:System.Windows.Forms.GroupBox> formantu. Należy również zwrócić uwagę na linii wyrównania, które są wyświetlane na <xref:System.Windows.Forms.Button> krawędziach kontrolki, która <xref:System.Windows.Forms.GroupBox> jest zawarta w kontrolce. Formanty, które są elementami podrzędnymi formantu kontenera, obsługują również linii wyrównania.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Użyj linii wyrównania, aby umieścić formant przez wykreślenie jego rozmiaru

1. W **przyborniku**kliknij <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągaj go na formularz.

2. Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Zwróć uwagę, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> dołączoną ikoną kontrolki. Należy również zwrócić uwagę na linii wyrównania, który pojawia się, aby <xref:System.Windows.Forms.Button> zasugerować wyrównane pozycje dla kontrolki.

3. Kliknij i przytrzymaj przycisk myszy.

4. Przeciągnij wskaźnik myszy wokół formularza. Należy zauważyć, że konspekt jest rysowany, wskazując położenie i rozmiar kontrolki.

5. Przeciągnij wskaźnik do momentu wyrównania z inną kontrolką w formularzu. Należy zauważyć, że snapline pojawia się w celu wskazania wyrównania.

6. Zwolnij przycisk myszy. Kontrolka jest tworzona na pozycji i rozmiarze wskazywanym przez konspekt.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Użyj linii wyrównania podczas przeciągania kontrolki z przybornika

1. Przeciągnij kontrolkę z przybornika na formularz, ale nie Zwolnij przycisku myszy. <xref:System.Windows.Forms.Button>

2. Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Należy zauważyć, że wskaźnik zmieni się, aby wskazać położenie, w <xref:System.Windows.Forms.Button> którym zostanie utworzona nowa kontrolka.

3. Przeciągnij wskaźnik myszy wokół formularza. Zwróć uwagę na linii wyrównania, który pojawia się, aby zasugerować wyrównane pozycje dla <xref:System.Windows.Forms.Button> kontrolki. Znajdź pozycję, która jest wyrównana do innych kontrolek.

4. Zwolnij przycisk myszy. Kontrolka jest tworzona na pozycji wskazywanej przez linii wyrównania.

## <a name="resize-a-control-using-snaplines"></a>Zmiana rozmiaru kontrolki przy użyciu linii wyrównania

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button>

2. Zmień rozmiar <xref:System.Windows.Forms.Button> kontrolki, pobierając jeden z narożnych uchwytów rozmiaru i przeciągając. Aby uzyskać szczegółowe informacje [, zobacz How to: Zmień rozmiar kontrolek](how-to-resize-controls-on-windows-forms.md)na Windows Forms.

3. Przeciągnij uchwyt zmiany rozmiarów do momentu, <xref:System.Windows.Forms.Button> gdy jeden z obramowania kontrolki zostanie wyrównany z inną kontrolką. Zauważ, że snapline pojawia się. Należy również zauważyć, że uchwyt zmiany rozmiarów jest przyciągany do pozycji wskazywanej przez snapline.

4. Zmień rozmiar <xref:System.Windows.Forms.Button> kontrolki w różnych kierunkach i Wyrównaj uchwyt zmiany rozmiaru do różnych kontrolek. Zwróć uwagę, jak linii wyrównania pojawia się w różnych orientacjach, aby wskazać wyrównanie.

## <a name="align-a-label-to-a-controls-text"></a>Wyrównywanie etykiety do tekstu kontrolki

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TextBox> Gdy porzucasz <xref:System.Windows.Forms.TextBox> formant na formularzu, kliknij symbol inteligentny i wybierz opcję **Ustaw tekst na TextBox1** . Aby uzyskać szczegółowe informacje [, zobacz Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach](performing-common-tasks-using-smart-tags-on-wf-controls.md)Windows Forms.

2. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Label>

3. Zmień wartość <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości kontrolki na `true`. Należy zauważyć, że obramowania kontrolki są dostosowywane w celu dopasowania do wyświetlanego tekstu.

4. Przenieś formant z lewej strony <xref:System.Windows.Forms.TextBox> kontrolki, tak aby był wyrównany do dolnej krawędzi <xref:System.Windows.Forms.TextBox> formantu. <xref:System.Windows.Forms.Label> Zwróć uwagę na snapline, który pojawia się wzdłuż dolnych krawędzi dwóch kontrolek.

5. Przesuwaj <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.TextBox> formant nieco w górę, dopóki tekst i tekst są wyrównane. <xref:System.Windows.Forms.Label> Zanotuj zanotowane inaczej style snapline, wskazujące, kiedy pola tekstowe obu formantów są wyrównane.

## <a name="use-snaplines-with-keyboard-navigation"></a>Korzystanie z linii wyrównania z nawigacją z klawiatury

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button> Umieść ją w lewym górnym rogu formularza.

2. Naciśnij klawisz **Ctrl**+**Strzałka w dół**. Należy zauważyć, że formant przenosi w dół formularza do pierwszego dostępnego położenia wyrównania poziomego.

3. Naciśnij klawisz **Ctrl**+**Strzałka w dół** , aż formant osiągnie dolny koniec formularza. Zanotuj położenia, które są zajęte podczas przenoszenia formularza.

4. Naciśnij klawisz **Ctrl**+**Strzałka w prawo**. Należy zauważyć, że kontrolka przechodzi między formularzem a pierwszą dostępną pozycją wyrównania w pionie.

5. Naciśnij klawisz **Ctrl**+**Strzałka w prawo** , dopóki kontrolka osiągnie bok formularza. Należy pamiętać o miejscach, w których są one zajęte w obrębie formularza.

6. Przenieś kontrolkę wokół formularza z kombinacją klawiszy strzałek. Zanotuj pozycje zajmowane przez kontrolkę i linii wyrównania do nich.

7. Naciśnij klawisz **SHIFT**+ ,<xref:System.Windows.Forms.Button> aby zmienić rozmiar kontrolki o wielokrotność jednego piksela.

8. Naciśnij klawisze **Ctrl**+**SHIFT**+**klawisze strzałek** , aby <xref:System.Windows.Forms.Button> zmienić rozmiar kontrolki w przyrostach snapline.

## <a name="selectively-disable-snaplines"></a>Selektywne wyłączanie linii wyrównania

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel>

2. Kliknij dwukrotnie ikonę kontrolkiwprzyborniku<xref:System.Windows.Forms.Button> . Należy zauważyć, że w <xref:System.Windows.Forms.TableLayoutPanel> pierwszej komórce kontrolki pojawia się nowa Kontrolka przycisku.

3. Dwukrotnie kliknij <xref:System.Windows.Forms.Button> ikonę kontrolki w przyborniku dwukrotnie. Spowoduje to pozostawienie pustej komórki <xref:System.Windows.Forms.TableLayoutPanel> w kontrolce.

4. Przeciągnij kontrolkę z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> pustej komórki kontrolki. <xref:System.Windows.Forms.Button> Należy zauważyć, że nie są wyświetlane żadne linii wyrównania.

5. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z kontrolki <xref:System.Windows.Forms.TableLayoutPanel> i przenieś ją wokół formantu. <xref:System.Windows.Forms.Button> Należy zauważyć, że linii wyrównania pojawia się ponownie.

## <a name="disable-snaplines"></a>Wyłącz linii wyrównania

Naciśnij klawisz **Alt** i podczas przenoszenia kontrolki wokół formularza.

Nie są wyświetlane żadne linii wyrównania i formant nie jest przyciągany do żadnych potencjalnych pozycji wyrównania.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Aby wyłączyć linii wyrównania w środowisku projektowym

1. W menu **Narzędzia** Otwórz okno dialogowe **Opcje** . Wybierz **Projektant formularzy systemu Windows**.

2. Wybierz węzeł **Ogólne** . W sekcji **tryb układu** Zmień wybór z **linii wyrównania** na **SnapToGrid**.

3. Wybierz **przycisk OK** , aby zastosować ustawienie.

4. Wybierz kontrolkę w formularzu i przenieś ją wokół innych kontrolek. Należy zauważyć, że linii wyrównania nie są wyświetlane.

## <a name="next-steps"></a>Następne kroki

Linii wyrównania oferują intuicyjny sposób wyrównywania kontrolek w formularzu. Sugestie dotyczące większej eksploracji obejmują:

- Spróbuj zagnieżdżać <xref:System.Windows.Forms.GroupBox> formant w innej <xref:System.Windows.Forms.GroupBox> kontrolce. Umieść formant w formancie podrzędnym <xref:System.Windows.Forms.GroupBox> , a drugi w kontrolce nadrzędnej <xref:System.Windows.Forms.GroupBox>. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> Przenieś kontrolki, aby zobaczyć, jak przecinają się granice kontenera linii wyrównania.

- Utwórz kolumnę <xref:System.Windows.Forms.TextBox> formantów i odpowiadającą jej <xref:System.Windows.Forms.Label> kolumnę kontrolek. Ustaw wartość <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości Controls na `true`. Użyj linii wyrównania, aby przenieść <xref:System.Windows.Forms.Label> kontrolki tak, aby ich wyświetlany tekst był wyrównany do tekstu <xref:System.Windows.Forms.TextBox> w kontrolkach.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Określanie układu formantów Windows Forms z dopełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md)
