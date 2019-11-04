---
title: 'Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04bef7162662f4fbefdaa151de13468d88530914
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460637"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Przewodnik: porządkowanie formantów na Windows Forms przy użyciu linii wyrównania

Precyzyjne rozmieszczenie kontrolek w formularzu jest wysokim priorytetem dla wielu aplikacji. Projektant formularzy systemu Windows zapewnia wiele narzędzi do układu. Jedną z najważniejszych jest funkcja <xref:System.Windows.Forms.Design.Behavior.SnapLine>.

Linii wyrównania pokazują precyzyjną lokalizację kontrolek z innymi kontrolkami. Przedstawiono w nich również zalecane odległości między kontrolkami, jak określono w [wytycznych dotyczących interfejsu użytkownika systemu Windows](/windows/win32/uxguide/guidelines).

Linii wyrównania ułatwiają wyrównywanie kontrolek w celu wyraźnego, profesjonalnego wyglądu i zachowania (wyglądu i działania).

## <a name="create-the-project"></a>Utwórz projekt

1. W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie "SnaplineExample".

2. Wybierz formularz w projektancie formularzy.

## <a name="space-and-align-controls"></a>Kontrolki Space i align

Linii wyrównania umożliwiają dokładne i intuicyjne dostosowanie formantów w formularzu. Są one wyświetlane podczas przesuwania zaznaczonej kontrolki lub kontrolek blisko położenia, które byłyby wyrównane do innej kontrolki lub zestawu kontrolek. Wybór zostanie przyciągnięty do sugerowanej pozycji podczas przenoszenia jej poza inne kontrolki.

### <a name="to-arrange-controls-using-snaplines"></a>Aby rozmieścić kontrolki za pomocą linii wyrównania

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz.

2. Przenieś formant <xref:System.Windows.Forms.Button> do prawego dolnego rogu formularza. Należy zauważyć, że linii wyrównania, który pojawia się jako formant <xref:System.Windows.Forms.Button>, zbliża się do dolnego i prawego obramowania formularza. Te linii wyrównania wyświetlają zalecaną odległość między obramowaniem kontrolki a formularzem.

3. Przenieś formant <xref:System.Windows.Forms.Button> wokół obramowania formularza i zanotuj, gdzie pojawia się linii wyrównania. Po zakończeniu Przenieś formant <xref:System.Windows.Forms.Button> blisko środka formularza.

4. Przeciągnij inną kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz.

5. Przenieś drugą kontrolkę <xref:System.Windows.Forms.Button> do momentu, aż będzie niemal poziom z pierwszym. Zwróć uwagę na snapline, który pojawia się w linii bazowej tekstu obu przycisków i Zauważ, że przenoszona kontrolka jest przyciągnięta do pozycji, która jest dokładnie na poziomie z inną kontrolką.

6. Przenieś drugi formant <xref:System.Windows.Forms.Button> do momentu, aż zostanie umieszczony bezpośrednio powyżej pierwszego. Zwróć uwagę na to, że linii wyrównania pojawia się wzdłuż lewej i prawej krawędzi obu przycisków i Zauważ, że przenoszona kontrolka jest przyciągnięta do położenia, które jest dokładnie wyrównane z inną kontrolką.

7. Wybierz jedną z formantów <xref:System.Windows.Forms.Button> i przenieś ją w dół, aż do momentu niemal dotknięcia. Zwróć uwagę na snapline, który pojawia się między nimi. Ta odległość jest zalecaną odległością między obramowaniem kontrolek. Należy również zauważyć, że przenoszony formant przyciągnie do tego położenia.

8. Przeciągnij dwie <xref:System.Windows.Forms.Panel> kontrolki z **przybornika** do formularza.

9. Przenieś jedną z <xref:System.Windows.Forms.Panel> kontrolek do momentu, aż będzie niemal poziom w pierwszej kolejności. Zwróć uwagę na to, że linii wyrównania pojawia się wzdłuż górnej i dolnej krawędzi obu kontrolek, i Zauważ, że przenoszona kontrolka jest przyciągnięta do pozycji, która jest dokładnie na poziomie z inną kontrolką.

## <a name="align-to-form-and-container-margins"></a>Wyrównaj do postaci i marginesów kontenera

Linii wyrównania ułatwiają wyrównywanie kontrolek do marginesów i w spójny sposób.

1. Wybierz jedną z formantów <xref:System.Windows.Forms.Button> i przenieś ją blisko prawej krawędzi formularza do momentu pojawienia się snapline. Odległość snapline od prawej krawędzi to suma właściwości <xref:System.Windows.Forms.Control.Margin%2A> kontrolki oraz wartości właściwości <xref:System.Windows.Forms.Control.Padding%2A> formularza.

   > [!NOTE]
   > Jeśli właściwość <xref:System.Windows.Forms.Control.Padding%2A> formularza ma wartość 0, 0, 0, 0, Projektant formularzy systemu Windows nadaje postać zacieniowanej <xref:System.Windows.Forms.Control.Padding%2A> wartości 9, 9, 9, 9. Aby zastąpić to zachowanie, przypisz wartość inną niż 0, 0, 0, 0.

2. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Margin%2A> kontrolki <xref:System.Windows.Forms.Button>, rozszerzając wpis <xref:System.Windows.Forms.Control.Margin%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.All%2A> na 0. Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: układowanie formantów Windows Forms z uzupełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md).

3. Przenieś <xref:System.Windows.Forms.Button> kontrolkę blisko prawej krawędzi formularza do momentu pojawienia się snapline. Ta odległość jest teraz określona przez wartość właściwości <xref:System.Windows.Forms.Control.Padding%2A> formularza.

4. Przeciągnij kontrolkę <xref:System.Windows.Forms.GroupBox> z **przybornika** na formularz.

5. Zmień wartość właściwości <xref:System.Windows.Forms.Control.Padding%2A> kontrolki <xref:System.Windows.Forms.GroupBox>, rozszerzając wpis <xref:System.Windows.Forms.Control.Padding%2A> w oknie **Właściwości** i ustawiając właściwość <xref:System.Windows.Forms.Padding.All%2A> na 10.

6. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.GroupBox>.

7. Przenieś <xref:System.Windows.Forms.Button> kontrolkę blisko prawej krawędzi kontrolki <xref:System.Windows.Forms.GroupBox> do momentu pojawienia się snapline. Przenieś formant <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.GroupBox> i zanotuj, gdzie pojawia się linii wyrównania.

## <a name="align-to-grouped-controls"></a>Wyrównaj do kontrolek zgrupowanych

Możesz użyć linii wyrównania, aby wyrównać zgrupowane kontrolki, a także kontrolki w kontrolce <xref:System.Windows.Forms.GroupBox>.

1. Wybierz dwie kontrolki w formularzu. Przenieś zaznaczenie dookoła i zanotuj linii wyrównania, które pojawiają się między wyborem a innymi kontrolkami.

2. Przeciągnij kontrolkę <xref:System.Windows.Forms.GroupBox> z **przybornika** na formularz.

3. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do kontrolki <xref:System.Windows.Forms.GroupBox>.

4. Wybierz jedną z formantów <xref:System.Windows.Forms.Button> i przenieś ją wokół kontrolki <xref:System.Windows.Forms.GroupBox>. Zwróć uwagę na linii wyrównania, który pojawia się na krawędziach kontrolki <xref:System.Windows.Forms.GroupBox>. Należy również zwrócić uwagę na linii wyrównania, które są wyświetlane na krawędziach kontrolki <xref:System.Windows.Forms.Button>, która jest zawarta w kontrolce <xref:System.Windows.Forms.GroupBox>. Formanty, które są elementami podrzędnymi formantu kontenera, obsługują również linii wyrównania.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Użyj linii wyrównania, aby umieścić formant przez wykreślenie jego rozmiaru

1. W **przyborniku**kliknij ikonę kontrolki <xref:System.Windows.Forms.Button>. Nie przeciągaj go na formularz.

2. Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Należy zauważyć, że wskaźnik zmieni się na krzyżyk z dołączoną ikoną <xref:System.Windows.Forms.Button>. Należy również zwrócić uwagę na linii wyrównania, który pojawia się, aby zasugerować wyrównane położenia dla kontrolki <xref:System.Windows.Forms.Button>.

3. Kliknij i przytrzymaj przycisk myszy.

4. Przeciągnij wskaźnik myszy wokół formularza. Należy zauważyć, że konspekt jest rysowany, wskazując położenie i rozmiar kontrolki.

5. Przeciągnij wskaźnik do momentu wyrównania z inną kontrolką w formularzu. Należy zauważyć, że snapline pojawia się w celu wskazania wyrównania.

6. Zwolnij przycisk myszy. Kontrolka jest tworzona na pozycji i rozmiarze wskazywanym przez konspekt.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Użyj linii wyrównania podczas przeciągania kontrolki z przybornika

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz, ale nie Zwolnij przycisku myszy.

2. Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Należy zauważyć, że wskaźnik zmieni się, aby wskazać położenie, w którym zostanie utworzona nowa kontrolka <xref:System.Windows.Forms.Button>.

3. Przeciągnij wskaźnik myszy wokół formularza. Zwróć uwagę na linii wyrównania, który pojawia się, aby zasugerować wyrównane pozycje dla kontrolki <xref:System.Windows.Forms.Button>. Znajdź pozycję, która jest wyrównana do innych kontrolek.

4. Zwolnij przycisk myszy. Kontrolka jest tworzona na pozycji wskazywanej przez linii wyrównania.

## <a name="resize-a-control-using-snaplines"></a>Zmiana rozmiaru kontrolki przy użyciu linii wyrównania

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz.

2. Zmień rozmiar kontrolki <xref:System.Windows.Forms.Button>, pobierając jeden z narożnych uchwytów rozmiaru i przeciągając go. Aby uzyskać szczegółowe informacje, zobacz [How to: zmiana rozmiaru kontrolek na Windows Forms](how-to-resize-controls-on-windows-forms.md).

3. Przeciągnij uchwyt zmiany rozmiarów do momentu, gdy jeden z obramowania kontrolki <xref:System.Windows.Forms.Button> zostanie wyrównany z inną kontrolką. Zauważ, że snapline pojawia się. Należy również zauważyć, że uchwyt zmiany rozmiarów jest przyciągany do pozycji wskazywanej przez snapline.

4. Zmień rozmiar kontrolki <xref:System.Windows.Forms.Button> w różnych kierunkach i Wyrównaj uchwyt zmiany rozmiaru do różnych kontrolek. Zwróć uwagę, jak linii wyrównania pojawia się w różnych orientacjach, aby wskazać wyrównanie.

## <a name="align-a-label-to-a-controls-text"></a>Wyrównywanie etykiety do tekstu kontrolki

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.TextBox> z **przybornika** na formularz. Gdy porzucasz kontrolkę <xref:System.Windows.Forms.TextBox> na formularzu, kliknij symbol inteligentny i wybierz opcję **Ustaw tekst na TextBox1** . Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md).

2. Przeciągnij kontrolkę <xref:System.Windows.Forms.Label> z **przybornika** na formularz.

3. Zmień wartość właściwości <xref:System.Windows.Forms.Control.AutoSize%2A> kontrolki <xref:System.Windows.Forms.Label> na `true`. Należy zauważyć, że obramowania kontrolki są dostosowywane w celu dopasowania do wyświetlanego tekstu.

4. Przenieś formant <xref:System.Windows.Forms.Label> z lewej strony kontrolki <xref:System.Windows.Forms.TextBox>, tak aby był wyrównany do dolnej krawędzi kontrolki <xref:System.Windows.Forms.TextBox>. Zwróć uwagę na snapline, który pojawia się wzdłuż dolnych krawędzi dwóch kontrolek.

5. Przenieś formant <xref:System.Windows.Forms.Label> nieco w górę, dopóki tekst <xref:System.Windows.Forms.Label> i tekst <xref:System.Windows.Forms.TextBox> są wyrównane. Zanotuj zanotowane inaczej style snapline, wskazujące, kiedy pola tekstowe obu formantów są wyrównane.

## <a name="use-snaplines-with-keyboard-navigation"></a>Korzystanie z linii wyrównania z nawigacją z klawiatury

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na formularz. Umieść ją w lewym górnym rogu formularza.

2. Naciśnij klawisz **Ctrl**+**strzałkę w dół**. Należy zauważyć, że formant przenosi w dół formularza do pierwszego dostępnego położenia wyrównania poziomego.

3. Naciśnij klawisz **Ctrl**+**strzałkę w dół** , aż formant osiągnie dolną część formularza. Zanotuj położenia, które są zajęte podczas przenoszenia formularza.

4. Naciśnij klawisz **Ctrl**+**strzałkę w prawo**. Należy zauważyć, że kontrolka przechodzi między formularzem a pierwszą dostępną pozycją wyrównania w pionie.

5. Naciśnij klawisz **Ctrl**+**strzałkę w prawo** , dopóki kontrolka osiągnie bok formularza. Należy pamiętać o miejscach, w których są one zajęte w obrębie formularza.

6. Przenieś kontrolkę wokół formularza z kombinacją klawiszy strzałek. Zanotuj pozycje zajmowane przez kontrolkę i linii wyrównania do nich.

7. Naciśnij klawisz **Shift**+**klawiszy strzałek** , aby zmienić rozmiar kontrolki <xref:System.Windows.Forms.Button> o wielokrotność jednego piksela.

8. Naciśnij klawisz **Ctrl**+**SHIFT**+**klawiszy strzałek** , aby zmienić rozmiar kontrolki <xref:System.Windows.Forms.Button> w przyrostach snapline.

## <a name="selectively-disable-snaplines"></a>Selektywne wyłączanie linii wyrównania

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.

2. Kliknij dwukrotnie ikonę kontrolki <xref:System.Windows.Forms.Button> w **przyborniku**. Należy zauważyć, że w pierwszej komórce kontrolki <xref:System.Windows.Forms.TableLayoutPanel> jest wyświetlana Nowa kontrolka przycisku.

3. Kliknij dwukrotnie ikonę kontrolki <xref:System.Windows.Forms.Button> w **przyborniku** dwa razy. Spowoduje to pozostawienie pustej komórki w kontrolce <xref:System.Windows.Forms.TableLayoutPanel>.

4. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do pustej komórki kontrolki <xref:System.Windows.Forms.TableLayoutPanel>. Należy zauważyć, że nie są wyświetlane żadne linii wyrównania.

5. Przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z kontrolki <xref:System.Windows.Forms.TableLayoutPanel> i przenieś ją wokół kontrolki <xref:System.Windows.Forms.TableLayoutPanel>. Należy zauważyć, że linii wyrównania pojawia się ponownie.

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

- Spróbuj zagnieździć formant <xref:System.Windows.Forms.GroupBox> w innej kontrolce <xref:System.Windows.Forms.GroupBox>. Umieść formant <xref:System.Windows.Forms.Button> w obrębie formantu podrzędnego <xref:System.Windows.Forms.GroupBox> i drugi w kontrolce <xref:System.Windows.Forms.GroupBox> nadrzędnej. Przenieś <xref:System.Windows.Forms.Button> kontrolki, aby zobaczyć, jak przecinają się granice kontenera linii wyrównania.

- Utwórz kolumnę formantów <xref:System.Windows.Forms.TextBox> i odpowiadającą jej kolumnę formantów <xref:System.Windows.Forms.Label>. Ustaw wartość właściwości <xref:System.Windows.Forms.Control.AutoSize%2A> formantów <xref:System.Windows.Forms.Label> na `true`. Użyj linii wyrównania, aby przenieść kontrolki <xref:System.Windows.Forms.Label> tak, aby ich wyświetlany tekst był wyrównany do tekstu w kontrolkach <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](windows-forms-controls-padding-autosize.md)
