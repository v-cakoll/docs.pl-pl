---
title: 'Przewodnik: rozmieszczanie kontrolek w formularzach systemu Windows za pomocą linii przyciągania'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 8ac1ba6b8121aabea3c992ca5b943f231fc19ce2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950069"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Przewodnik: rozmieszczanie kontrolek w formularzach systemu Windows za pomocą linii przyciągania
Precyzyjne rozmieszczenie kontrolek w formularzu jest wysokim priorytetem dla wielu aplikacji. Projektant formularzy systemu Windows zapewnia wiele narzędzi do układu. Jedną z najważniejszych <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkcji jest funkcja.

 Linii wyrównania pokazują precyzyjną lokalizację kontrolek z innymi kontrolkami. Przedstawiono w nich również zalecane odległości między kontrolkami, jak określono w wytycznych dotyczących interfejsu użytkownika systemu Windows. Aby uzyskać szczegółowe informacje, zobacz [Projektowanie interfejsu użytkownika i programowanie](https://go.microsoft.com/FWLink/?LinkId=83878).

 Linii wyrównania ułatwiają wyrównywanie kontrolek w celu wyraźnego, profesjonalnego wyglądu i zachowania (wyglądu i działania).

 Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu Windows Forms

- Odstępy i wyrównywanie kontrolek przy użyciu linii wyrównania

- Wyrównywanie do marginesów formularza i kontenera

- Wyrównywanie do kontrolek zgrupowanych

- Umieszczanie kontrolki za pomocą linii wyrównania

- Używanie linii wyrównania podczas przeciągania kontrolki z przybornika

- Zmienianie rozmiarów formantów przy użyciu linii wyrównania

- Wyrównywanie etykiety do tekstu kontrolki

- Używanie linii wyrównania z nawigacją z klawiatury

- Linii wyrównania i panele układów

- Wyłączanie linii wyrównania

 Po zakończeniu będzie można zrozumieć rolę układu odgrywaną przez funkcję linii wyrównania.

## <a name="creating-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Utwórz projekt aplikacji oparty na systemie Windows o nazwie "SnaplineExample" (**plik** > **Nowy** > **projekt** >  **C# Visual** lub **Visual Basic** > **klasyczny**  > Aplikacja klasyczna**Windows Forms**).

2. Wybierz formularz w projektancie formularzy.

## <a name="spacing-and-aligning-controls-using-snaplines"></a>Odstępy i wyrównywanie kontrolek przy użyciu linii wyrównania
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

## <a name="aligning-to-form-and-container-margins"></a>Wyrównywanie do marginesów formularza i kontenera
 Linii wyrównania ułatwiają wyrównywanie kontrolek do marginesów i w spójny sposób.

### <a name="to-align-controls-to-form-and-container-margins"></a>Aby wyrównać kontrolki do postaci i marginesów kontenera

1. Zaznacz jedną z <xref:System.Windows.Forms.Button> formantów i przenieś ją blisko prawej krawędzi formularza do momentu pojawienia się snapline. Odległość snapline od prawej krawędzi to suma <xref:System.Windows.Forms.Control.Margin%2A> właściwości kontrolki i wartości <xref:System.Windows.Forms.Control.Padding%2A> właściwości formularza.

> [!NOTE]
> Jeśli <xref:System.Windows.Forms.Control.Padding%2A> właściwość formularza jest ustawiona na 0, 0, 0, 0, Projektant formularzy systemu Windows daje formę <xref:System.Windows.Forms.Control.Padding%2A> cieniowanie wartości 9, 9, 9, 9. Aby zastąpić to zachowanie, przypisz wartość inną niż 0, 0, 0, 0.

1. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> właściwości kontrolki, rozszerzając <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.All%2A> wpis w oknie **Właściwości** i ustawiając właściwość na 0. Aby uzyskać szczegółowe informacje [, zobacz Przewodnik: Określanie układu formantów Windows Forms z uzupełnieniem, marginesami i właściwością](windows-forms-controls-padding-autosize.md)AutoSize.

2. <xref:System.Windows.Forms.Button> Przesuń formant blisko prawej krawędzi formularza do momentu pojawienia się snapline. Ta odległość jest teraz określona przez wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości formularza.

3. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.GroupBox>

4. Zmień wartość <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Control.Padding%2A> właściwości kontrolki, rozszerzając <xref:System.Windows.Forms.Control.Padding%2A> wpis w oknie **Właściwości** i ustawiając właściwość na wartość <xref:System.Windows.Forms.Padding.All%2A> 10.

5. Przeciągnij kontrolkę z <xref:System.Windows.Forms.GroupBox> przybornika do kontrolki. <xref:System.Windows.Forms.Button>

6. Przesuń formant blisko prawej krawędzi <xref:System.Windows.Forms.GroupBox> kontrolki do momentu pojawienia się snapline. <xref:System.Windows.Forms.Button> Przenieś kontrolkę <xref:System.Windows.Forms.GroupBox> wewnątrz kontrolki i zanotuj, gdzie pojawia się linii wyrównania. <xref:System.Windows.Forms.Button>

## <a name="aligning-to-grouped-controls"></a>Wyrównywanie do kontrolek zgrupowanych
 Możesz użyć linii wyrównania, aby wyrównać zgrupowane kontrolki, a także <xref:System.Windows.Forms.GroupBox> kontrolki w kontrolce.

### <a name="to-align-to-grouped-controls"></a>Aby wyrównać zgrupowane kontrolki

1. Wybierz dwie kontrolki w formularzu. Przenieś zaznaczenie dookoła i zanotuj linii wyrównania, które pojawiają się między wyborem a innymi kontrolkami.

2. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.GroupBox>

3. Przeciągnij kontrolkę z <xref:System.Windows.Forms.GroupBox> przybornika do kontrolki. <xref:System.Windows.Forms.Button>

4. Zaznacz jedną z <xref:System.Windows.Forms.Button> formantów i przenieś ją <xref:System.Windows.Forms.GroupBox> wokół formantu. Zwróć uwagę na linii wyrównania, który pojawia się na krawędziach <xref:System.Windows.Forms.GroupBox> formantu. Należy również zwrócić uwagę na linii wyrównania, które są wyświetlane na <xref:System.Windows.Forms.Button> krawędziach kontrolki, która <xref:System.Windows.Forms.GroupBox> jest zawarta w kontrolce. Formanty, które są elementami podrzędnymi formantu kontenera, obsługują również linii wyrównania.

## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Umieszczanie kontrolki za pomocą linii wyrównania
 Linii wyrównania ułatwia wyrównywanie formantów po ich umieszczeniu w formularzu.

### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Aby używać linii wyrównania do umieszczania kontrolki przez obramowanie jej rozmiaru

1. W **przyborniku**kliknij <xref:System.Windows.Forms.Button> ikonę kontrolki. Nie przeciągaj go na formularz.

2. Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Zwróć uwagę, że wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.Button> dołączoną ikoną kontrolki. Należy również zwrócić uwagę na linii wyrównania, który pojawia się, aby <xref:System.Windows.Forms.Button> zasugerować wyrównane pozycje dla kontrolki.

3. Kliknij i przytrzymaj przycisk myszy.

4. Przeciągnij wskaźnik myszy wokół formularza. Należy zauważyć, że konspekt jest rysowany, wskazując położenie i rozmiar kontrolki.

5. Przeciągnij wskaźnik do momentu wyrównania z inną kontrolką w formularzu. Należy zauważyć, że snapline pojawia się w celu wskazania wyrównania.

6. Zwolnij przycisk myszy. Kontrolka jest tworzona na pozycji i rozmiarze wskazywanym przez konspekt.

## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Używanie linii wyrównania podczas przeciągania kontrolki z przybornika
 Linii wyrównania ułatwiają wyrównywanie formantów podczas przeciągania ich z **przybornika** do formularza.

### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Aby użyć linii wyrównania podczas przeciągania kontrolki z przybornika

1. Przeciągnij kontrolkę z przybornika na formularz, ale nie Zwolnij przycisku myszy. <xref:System.Windows.Forms.Button>

2. Przesuń wskaźnik myszy nad powierzchnię projektową formularza. Należy zauważyć, że wskaźnik zmieni się, aby wskazać położenie, w <xref:System.Windows.Forms.Button> którym zostanie utworzona nowa kontrolka.

3. Przeciągnij wskaźnik myszy wokół formularza. Zwróć uwagę na linii wyrównania, który pojawia się, aby zasugerować wyrównane pozycje dla <xref:System.Windows.Forms.Button> kontrolki. Znajdź pozycję, która jest wyrównana do innych kontrolek.

4. Zwolnij przycisk myszy. Kontrolka jest tworzona na pozycji wskazywanej przez linii wyrównania.

## <a name="resizing-controls-using-snaplines"></a>Zmienianie rozmiarów formantów przy użyciu linii wyrównania
 Linii wyrównania ułatwia wyrównywanie kontrolek w miarę ich zmieniania.

### <a name="to-resize-a-control-using-snaplines"></a>Aby zmienić rozmiar kontrolki przy użyciu linii wyrównania

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button>

2. Zmień rozmiar <xref:System.Windows.Forms.Button> kontrolki, pobierając jeden z narożnych uchwytów rozmiaru i przeciągając. Aby uzyskać szczegółowe informacje [, zobacz How to: Zmień rozmiar kontrolek](how-to-resize-controls-on-windows-forms.md)na Windows Forms.

3. Przeciągnij uchwyt zmiany rozmiarów do momentu, <xref:System.Windows.Forms.Button> gdy jeden z obramowania kontrolki zostanie wyrównany z inną kontrolką. Zauważ, że snapline pojawia się. Należy również zauważyć, że uchwyt zmiany rozmiarów jest przyciągany do pozycji wskazywanej przez snapline.

4. Zmień rozmiar <xref:System.Windows.Forms.Button> kontrolki w różnych kierunkach i Wyrównaj uchwyt zmiany rozmiaru do różnych kontrolek. Zwróć uwagę, jak linii wyrównania pojawia się w różnych orientacjach, aby wskazać wyrównanie.

## <a name="aligning-a-label-to-a-controls-text"></a>Wyrównywanie etykiety do tekstu kontrolki
 Niektóre kontrolki oferują snapline do wyrównywania innych kontrolek do wyświetlanego tekstu.

### <a name="to-align-a-label-to-a-controls-text"></a>Aby wyrównać etykietę do tekstu kontrolki

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TextBox> Gdy porzucasz <xref:System.Windows.Forms.TextBox> formant na formularzu, kliknij symbol inteligentny i wybierz opcję **Ustaw tekst na TextBox1** . Aby uzyskać szczegółowe informacje [, zobacz Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach](performing-common-tasks-using-smart-tags-on-wf-controls.md)Windows Forms.

2. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Label>

3. Zmień wartość <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości kontrolki na `true`. Należy zauważyć, że obramowania kontrolki są dostosowywane w celu dopasowania do wyświetlanego tekstu.

4. Przenieś formant z lewej strony <xref:System.Windows.Forms.TextBox> kontrolki, tak aby był wyrównany do dolnej krawędzi <xref:System.Windows.Forms.TextBox> formantu. <xref:System.Windows.Forms.Label> Zwróć uwagę na snapline, który pojawia się wzdłuż dolnych krawędzi dwóch kontrolek.

5. Przesuwaj <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.TextBox> formant nieco w górę, dopóki tekst i tekst są wyrównane. <xref:System.Windows.Forms.Label> Zanotuj zanotowane inaczej style snapline, wskazujące, kiedy pola tekstowe obu formantów są wyrównane.

## <a name="using-snaplines-with-keyboard-navigation"></a>Używanie linii wyrównania z nawigacją z klawiatury
 Linii wyrównania ułatwiają wyrównywanie formantów podczas ich rozmieszczania przy użyciu klawiszy strzałek klawiatury.

### <a name="to-use-snaplines-with-keyboard-navigation"></a>Aby użyć linii wyrównania z nawigacją z klawiatury

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.Button> Umieść ją w lewym górnym rogu formularza.

2. Naciśnij klawisze CTRL + STRZAŁKA w dół. Należy zauważyć, że formant przenosi w dół formularza do pierwszego dostępnego położenia wyrównania poziomego.

3. Naciśnij klawisze CTRL + STRZAŁKA w dół, aż formant osiągnie dolny koniec formularza. Zanotuj położenia, które są zajęte podczas przenoszenia formularza.

4. Naciśnij klawisze CTRL + STRZAŁKA w prawo. Należy zauważyć, że kontrolka przechodzi między formularzem a pierwszą dostępną pozycją wyrównania w pionie.

5. Naciśnij klawisze CTRL + STRZAŁKA w prawo, dopóki kontrolka osiągnie bok formularza. Należy pamiętać o miejscach, w których są one zajęte w obrębie formularza.

6. Przenieś kontrolkę wokół formularza z kombinacją klawiszy strzałek. Zanotuj pozycje zajmowane przez kontrolkę i linii wyrównania do nich.

7. Naciśnij klawisze SHIFT + dowolny klawisz Strzałka, aby <xref:System.Windows.Forms.Button> zmienić rozmiar kontrolki o wielokrotność jednego piksela.

8. Naciśnij klawisze CTRL + SHIFT + dowolny klawisz Strzałka, aby <xref:System.Windows.Forms.Button> zmienić rozmiar kontrolki w przyrostach snapline.

## <a name="snaplines-and-layout-panels"></a>Linii wyrównania i panele układów
 Linii wyrównania są wyłączone w panelach układu.

### <a name="to-selectively-disable-snaplines"></a>Aby selektywnie wyłączyć linii wyrównania

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel>

2. Kliknij dwukrotnie ikonę kontrolkiwprzyborniku<xref:System.Windows.Forms.Button> . Należy zauważyć, że w <xref:System.Windows.Forms.TableLayoutPanel> pierwszej komórce kontrolki pojawia się nowa Kontrolka przycisku.

3. Dwukrotnie kliknij <xref:System.Windows.Forms.Button> ikonę kontrolki w przyborniku dwukrotnie. Spowoduje to pozostawienie pustej komórki <xref:System.Windows.Forms.TableLayoutPanel> w kontrolce.

4. Przeciągnij kontrolkę z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> pustej komórki kontrolki. <xref:System.Windows.Forms.Button> Należy zauważyć, że nie są wyświetlane żadne linii wyrównania.

5. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z kontrolki <xref:System.Windows.Forms.TableLayoutPanel> i przenieś ją wokół formantu. <xref:System.Windows.Forms.Button> Należy zauważyć, że linii wyrównania pojawia się ponownie.

## <a name="disabling-snaplines"></a>Wyłączanie linii wyrównania
 Linii wyrównania są domyślnie włączone. Linii wyrównania można wyłączyć wybiórczo lub można je wyłączyć w środowisku projektowym.

### <a name="to-selectively-disable-snaplines"></a>Aby selektywnie wyłączyć linii wyrównania

- Naciśnij klawisz ALT i podczas przenoszenia kontrolki wokół formularza.

     Należy zauważyć, że nie są wyświetlane żadne linii wyrównania i formant nie jest przyciągany do żadnych potencjalnych pozycji wyrównania.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Aby wyłączyć linii wyrównania w środowisku projektowym

1. W menu **Narzędzia** Otwórz okno dialogowe **Opcje** . Otwórz okno dialogowe Projektant formularzy systemu Windows. Aby uzyskać szczegółowe informacje, zobacz [Ogólne, Projektant formularzy systemu Windows, Opcje — okno dialogowe](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).

2. Wybierz węzeł **Ogólne** . W sekcji **tryb układu** Zmień wybór z **linii wyrównania** na **SnapToGrid**.

3. Kliknij przycisk OK, aby zastosować ustawienie.

4. Wybierz kontrolkę w formularzu i przenieś ją wokół innych kontrolek. Należy zauważyć, że linii wyrównania nie są wyświetlane.

## <a name="next-steps"></a>Następne kroki
 Linii wyrównania oferują intuicyjny sposób wyrównywania kontrolek w formularzu. Sugestie dotyczące większej eksploracji obejmują:

- Spróbuj zagnieżdżać <xref:System.Windows.Forms.GroupBox> formant w innej <xref:System.Windows.Forms.GroupBox> kontrolce. Umieść formant w formancie podrzędnym <xref:System.Windows.Forms.GroupBox> , a drugi w kontrolce nadrzędnej <xref:System.Windows.Forms.GroupBox>. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> Przenieś kontrolki, aby zobaczyć, jak przecinają się granice kontenera linii wyrównania.

- Utwórz kolumnę <xref:System.Windows.Forms.TextBox> formantów i odpowiadającą jej <xref:System.Windows.Forms.Label> kolumnę kontrolek. Ustaw wartość <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości Controls na `true`. Użyj linii wyrównania, aby przenieść <xref:System.Windows.Forms.Label> kontrolki tak, aby ich wyświetlany tekst był wyrównany do tekstu <xref:System.Windows.Forms.TextBox> w kontrolkach.

 Aby uzyskać informacje na temat projektowania interfejsu użytkownika systemu Windows, zobacz Podręcznik *użytkownika systemu Microsoft Windows, oficjalne wytyczne dla deweloperów interfejsu użytkownika i projektantów* REDMOND, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Określanie układu formantów Windows Forms z dopełnieniem, marginesami i właściwością AutoSize](windows-forms-controls-padding-autosize.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
