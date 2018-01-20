---
title: "Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd8bc5e227bd68fc3c5c59d80549322ca742bcf9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Wskazówki: rozmieszczanie formantów w formularzach systemu Windows za pomocą linii przyciągania
Rozmieszczenie kontrolek w formularzu jest wysoki priorytet dla wielu aplikacji. Projektant formularzy systemu Windows udostępnia wiele narzędzi układu, w tym celu. Jednym z najważniejszych jest <xref:System.Windows.Forms.Design.Behavior.SnapLine> funkcji.  
  
 Linie przyciągania Pokaż dokładnie, gdzie wyrównywanie formantów z innych kontrolek. One również zawierają zalecane odległości marginesy między formantami, zgodnie z wytycznymi interfejsu użytkownika systemu Windows. Aby uzyskać więcej informacji, zobacz [projektu interfejsu użytkownika i rozwoju](http://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Linie przyciągania ułatwiają wyrównywanie formantów, aby uzyskać wysoką, professional wygląd i zachowanie (wygląd i działanie).  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu formularzy systemu Windows  
  
-   Odstępy i wyrównywanie formantów za pomocą linii przyciągania  
  
-   Wyrównywanie do formularza i marginesów kontenera  
  
-   Wyrównywanie formantów grupowanych  
  
-   Można umieścić formantu przy użyciu konspektu jego rozmiar za pomocą linii przyciągania  
  
-   Za pomocą linii przyciągania podczas przeciągania formant z przybornika  
  
-   Zmiana rozmiaru formantów za pomocą linii przyciągania  
  
-   Wyrównanie etykiety w celu tekstu formantu  
  
-   Za pomocą linii przyciągania z nawigacji klawiatury  
  
-   Linie przyciągania i panele układu  
  
-   Wyłączanie linie przyciągania  
  
 Gdy skończysz, konieczne będzie zrozumienia układu roli za pomocą funkcji linie przyciągania.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie "SnaplineExample". Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Wybierz formularza w narzędziu Projektant dla formularzy.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Odstępy i wyrównywanie formantów za pomocą linii przyciągania  
 Linie przyciągania zapewnić dokładne i intuicyjne sposób wyrównywanie formantów w formularzu. One wyświetlane, gdy chcesz przenieść wybrany formant lub kontrolki obok pozycji, która będzie wyrównany z innego formantu lub zbiór kontrolek. Wybór spowoduje "przyciąganie" sugerowane miejsce podczas przenoszenia go poza inne formanty.  
  
#### <a name="to-arrange-controls-using-snaplines"></a>Aby zorganizować formantów za pomocą linii przyciągania  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu.  
  
2.  Przenieś <xref:System.Windows.Forms.Button> formantu prawym dolnym rogu formularza. Uwaga linie przyciągania, który pojawia się jako <xref:System.Windows.Forms.Button> kontroli zbliża się do dolnej i prawej obramowania formularza. Te linie przyciągania wyświetlić zalecaną odległość między obramowania formantu i formularza.  
  
3.  Przenieś <xref:System.Windows.Forms.Button> kontroli wokół obramowania formularza i Uwaga, w którym są wyświetlane linie przyciągania. Po zakończeniu przenoszenia <xref:System.Windows.Forms.Button> sterowania na środku formularza.  
  
4.  Przeciągnij kolejny <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu.  
  
5.  Przenieś drugi <xref:System.Windows.Forms.Button> kontrolowanie momentu niemal poziomu z pierwszego. Zanotuj snapline —, wyświetlany w linii bazowej tekstu obu przycisków i należy pamiętać, że formant, który przenosisz przyciąganie pozycji, która jest dokładnie poziomu za pomocą formantu innych.  
  
6.  Przenieś drugi <xref:System.Windows.Forms.Button> kontrolować, dopóki nie znajduje się bezpośrednio nad pierwszy. Należy pamiętać, linie przyciągania, są wyświetlane wzdłuż lewej i prawej krawędzi przyciski, którą należy zauważyć, że kontrolka możesz przenoszenie przyciąganie do pozycji, która jest dokładnie wyrównana z innych formantu.  
  
7.  Wybierz jedną z <xref:System.Windows.Forms.Button> steruje i przenieść blisko innych, dopóki nie są one prawie dotknięcie. Uwaga snapline —, który pojawia się między nimi. To jest to zalecane odległość między obramowania formantów. Należy również zauważyć, że formant, który przenosisz przyciąganie do tej pozycji.  
  
8.  Przeciągnij dwa <xref:System.Windows.Forms.Panel> formantów **przybornika** na formularzu.  
  
9. Przenieść jeden z <xref:System.Windows.Forms.Panel> kontrolki, dopóki nie zostanie niemal poziomu z pierwszym. Należy pamiętać, linie przyciągania, są wyświetlane wzdłuż górnej i dolnej krawędzi oba formanty, którą należy pamiętać, że formant, który przenosisz przyciąganie pozycji, która jest dokładnie poziomu za pomocą formantu innych.  
  
## <a name="aligning-to-form-and-container-margins"></a>Wyrównywanie do formularza i marginesów kontenera  
 Linie przyciągania ułatwiają wyrównywanie formantów do formularza i kontener marginesu w sposób ciągły.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Aby wyrównać formantów do formularza i kontener marginesów  
  
1.  Wybierz jedną z <xref:System.Windows.Forms.Button> steruje i przenieść blisko prawej krawędzi formularza, aż pojawi się snapline —. Snapline — odległość od prawej krawędzi jest sumą formantu <xref:System.Windows.Forms.Control.Margin%2A> właściwości i formularza <xref:System.Windows.Forms.Control.Padding%2A> wartości właściwości.  
  
> [!NOTE]
>  Jeśli formularza <xref:System.Windows.Forms.Control.Padding%2A> właściwość jest ustawiona na 0,0,0,0, Projektant formularzy systemu Windows zapewnia formularza zasłonięty <xref:System.Windows.Forms.Control.Padding%2A> wartość 9,9,9,9. Aby zmienić to zachowanie, należy przypisać wartość inną niż 0,0,0,0.  
  
1.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Margin%2A> właściwości rozwijając <xref:System.Windows.Forms.Control.Margin%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości na 0. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie limit formantów formularzy systemu Windows z dopełnienie, marginesami oraz właściwościami AutoSize właściwość](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Przenieś <xref:System.Windows.Forms.Button> kontroli blisko prawej krawędzi formularza, dopóki nie zostanie wyświetlony snapline —. Odległość znajduje się teraz według wartości w postaci <xref:System.Windows.Forms.Control.Padding%2A> właściwości.  
  
3.  Przeciągnij <xref:System.Windows.Forms.GroupBox> kontrolować z **przybornika** na formularzu.  
  
4.  Zmień wartość <xref:System.Windows.Forms.GroupBox> formantu <xref:System.Windows.Forms.Control.Padding%2A> właściwości rozwijając <xref:System.Windows.Forms.Control.Padding%2A> wpis w **właściwości** okno i ustawienie <xref:System.Windows.Forms.Padding.All%2A> właściwości do 10.  
  
5.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.GroupBox> formantu.  
  
6.  Przenieś <xref:System.Windows.Forms.Button> kontroli blisko prawej krawędzi <xref:System.Windows.Forms.GroupBox> kontrolować aż pojawi się snapline —. Przenieś <xref:System.Windows.Forms.Button> kontroli w ramach <xref:System.Windows.Forms.GroupBox> kontroli i Uwaga, w którym są wyświetlane linie przyciągania.  
  
## <a name="aligning-to-grouped-controls"></a>Wyrównywanie formantów grupowanych  
 Linie przyciągania umożliwia wyrównywanie formantów grupowanych również jako steruje w obrębie <xref:System.Windows.Forms.GroupBox> formantu.  
  
#### <a name="to-align-to-grouped-controls"></a>Aby wyrównać grupowanych formantów  
  
1.  Wybierz dwa formantów w formularzu. Poruszanie się zaznaczenie i zanotuj linie przyciągania, który pojawia się między wybór i innych kontrolek.  
  
2.  Przeciągnij <xref:System.Windows.Forms.GroupBox> kontrolować z **przybornika** na formularzu.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do <xref:System.Windows.Forms.GroupBox> formantu.  
  
4.  Wybierz jedną z <xref:System.Windows.Forms.Button> steruje i przenosić <xref:System.Windows.Forms.GroupBox> formantu. Uwaga linie przyciągania, który pojawia się na krawędzi <xref:System.Windows.Forms.GroupBox> formantu. Należy również zauważyć, linie przyciągania, który pojawia się na krawędzi <xref:System.Windows.Forms.Button> formant, który jest zawarty w <xref:System.Windows.Forms.GroupBox> formantu. Formanty, które są elementami podrzędnymi formantu kontenera obsługują także linie przyciągania.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Można umieścić formantu przy użyciu konspektu jego rozmiar za pomocą linii przyciągania  
 Wyrównuje linie przyciągania pomocy określa, kiedy należy najpierw umieścić je w formularzu.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Na potrzeby Umieść formant przez tworzenie konspektu rozmiaru linie przyciągania  
  
1.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.Button> ikona formantu. Nie przeciągnij go na formularzu.  
  
2.  Przesuń wskaźnik myszy nad powierzchni projektowej formularza. Należy pamiętać, że kursor zmienia się na krzyżyk z <xref:System.Windows.Forms.Button> ikona kontroli dołączony. Należy również zauważyć, linie przyciągania, wyświetlanych sugerowanie wyrównany pozycji <xref:System.Windows.Forms.Button> formantu.  
  
3.  Kliknij i przytrzymaj przycisk myszy.  
  
4.  Przeciągnij wskaźnik myszy wokół formularza. Należy pamiętać, że konspektu jest pobierana, wskazującą położenie i rozmiar formantu.  
  
5.  Przeciągnij wskaźnik czasu z formantem w formularzu. Należy pamiętać, że snapline — zostanie wyświetlony wskazujący wyrównania.  
  
6.  Zwolnij przycisk myszy. Formant nie zostanie utworzony na położenie i rozmiar wskazywanym przez konturu.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Za pomocą linii przyciągania podczas przeciągania formant z przybornika  
 Linie przyciągania ułatwiają wyrównywanie steruje podczas przeciągania z **przybornika** na formularzu.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Aby użyć linie przyciągania podczas przeciągania formant z przybornika  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu, ale nie zwolnij przycisk myszy.  
  
2.  Przesuń wskaźnik myszy nad powierzchni projektowej formularza. Kursor zmienia się na wskazać pozycję, w której nowe <xref:System.Windows.Forms.Button> formantu zostanie utworzony.  
  
3.  Przeciągnij wskaźnik myszy wokół formularza. Należy pamiętać, linie przyciągania, wyświetlanych sugerowanie wyrównany pozycji <xref:System.Windows.Forms.Button> formantu. Znajdź pozycji, która jest wyrównywana z innych kontrolek.  
  
4.  Zwolnij przycisk myszy. Kontrolka jest tworzony w pozycji linie przyciągania.  
  
## <a name="resizing-controls-using-snaplines"></a>Zmiana rozmiaru formantów za pomocą linii przyciągania  
 Linie przyciągania ułatwiają wyrównywanie formantów podczas zmiany ich rozmiaru.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Aby zmienić rozmiar formantu za pomocą linii przyciągania  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu.  
  
2.  Zmień rozmiar <xref:System.Windows.Forms.Button> kontroli przez narożnika uchwytów i przeciągając dane. Aby uzyskać więcej informacji, zobacz [porady: zmiana rozmiaru formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Przeciągnij uchwyt zmiany rozmiaru, dopóki jedna z <xref:System.Windows.Forms.Button> obramowania formantu jest wyrównywana z formantem. Należy pamiętać, że snapline — zostanie wyświetlona. Należy również zauważyć, że uchwyt zmiany rozmiaru przyciąganie do pozycji snapline —.  
  
4.  Zmień rozmiar <xref:System.Windows.Forms.Button> kontroli w różnych kierunkach i wyrównywanie uchwyt zmiany rozmiaru, aby inne formanty. Należy zwrócić uwagę, jak linie przyciągania pojawiać się w różnych położeniach wskazująca wyrównania.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Wyrównanie etykiety w celu tekstu formantu  
 Niektóre formanty oferują snapline — wyrównywania inne formanty do wyświetlanego tekstu.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Aby wyrównać etykietę do tekstu formantu  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> kontrolować z **przybornika** na formularzu. Po upuszczeniu <xref:System.Windows.Forms.TextBox> sterowania do formularza, kliknij symbol tagów inteligentnych i wybierz **ustawioną tekst Poletekstowe1** opcji. Aby uzyskać więcej informacji, zobacz [wskazówki: wykonywanie typowych zadań za pomocą tagów inteligentnych formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Przeciągnij <xref:System.Windows.Forms.Label> kontrolować z **przybornika** na formularzu.  
  
3.  Zmień wartość <xref:System.Windows.Forms.Label> formantu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`. Należy pamiętać, że obramowania formantu są dostosowane do wyświetlania tekstu.  
  
4.  Przenieś <xref:System.Windows.Forms.Label> kontrolki do lewej strony <xref:System.Windows.Forms.TextBox> kontrolować, więc jest wyrównane do dolnej krawędzi <xref:System.Windows.Forms.TextBox> formantu. Należy zwrócić uwagę snapline —, wyświetlany wzdłuż dolnej krawędzi dwóch formantów.  
  
5.  Przenieś <xref:System.Windows.Forms.Label> kontroli nieco górę, aż do <xref:System.Windows.Forms.Label> tekstu i <xref:System.Windows.Forms.TextBox> wyrównania tekstu. Należy pamiętać, inaczej styl snapline —, zostanie wyświetlone, wskazujący, gdy pola tekstowe obu formantów są wyrównane.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Za pomocą linii przyciągania z nawigacji klawiatury  
 Wyrównuje linie przyciągania pomocy określa, kiedy są rozmieszczanie je za pomocą klawiszy strzałek.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Aby używać linie przyciągania z nawigacji klawiatury  
  
1.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularzu. Umieść go w lewym górnym rogu formularza.  
  
2.  Naciśnij klawisze CTRL + Strzałka w dół. Należy pamiętać, że kontrolka przechodzi w dół formularza do pierwszą pozycję dostępne wyrównanie w poziomie.  
  
3.  Naciśnij klawisze CTRL + Strzałka w dół, dopóki nie osiągnie formantu dolnej części formularza. Należy pamiętać, pozycje, które przypada przesyłane w dół formularza.  
  
4.  Naciśnij klawisze CTRL + Strzałka w prawo. Należy pamiętać, że kontrolka porusza się na formularzu na pierwszą pozycję dostępne wyrównanie w pionie.  
  
5.  Naciśnij klawisz CTRL + Strzałka w prawo, dopóki nie osiągnie formantu stronach formularza. Należy zwrócić uwagę położenie obiektu podczas ruchu na formularzu.  
  
6.  Przenieś formant wokół formularza z kombinacji klawiszy strzałek. Należy pamiętać, pozycje, które zajmuje formantu i linie przyciągania, który je dołączyć.  
  
7.  Naciśnij klawisze SHIFT + dowolna strzałka, aby zmienić rozmiar <xref:System.Windows.Forms.Button> kontroli co jeden piksel.  
  
8.  Naciśnij klawisze CTRL + SHIFT + dowolna strzałka, aby zmienić rozmiar <xref:System.Windows.Forms.Button> kontroli w przyrostach snapline —.  
  
## <a name="snaplines-and-layout-panels"></a>Linie przyciągania i panele układu  
 Linie przyciągania są wyłączone w ramach panele układu.  
  
#### <a name="to-selectively-disable-snaplines"></a>Aby wyłączyć linie przyciągania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
2.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontroli w **przybornika**. Należy pamiętać, że nową kontrolkę przycisku zostanie wyświetlone w <xref:System.Windows.Forms.TableLayoutPanel> pierwszej komórki formantu.  
  
3.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> ikonę kontroli w **przybornika** dwa razy więcej. Spowoduje to pozostawienie co pustej komórki w <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
4.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do pustej komórki z <xref:System.Windows.Forms.TableLayoutPanel> formantu. Należy pamiętać, że są wyświetlane nie linie przyciągania.  
  
5.  Przeciągnij <xref:System.Windows.Forms.Button> kontroli z <xref:System.Windows.Forms.TableLayoutPanel> kontroli i przenosić <xref:System.Windows.Forms.TableLayoutPanel> formantu. Należy pamiętać, że linie przyciągania pojawiają się ponownie.  
  
## <a name="disabling-snaplines"></a>Wyłączanie linie przyciągania  
 Linie przyciągania jest domyślnie włączona. Linie przyciągania można wyłączyć selektywnie lub można je wyłączyć w środowisku projektowym.  
  
#### <a name="to-selectively-disable-snaplines"></a>Aby wyłączyć linie przyciągania  
  
-   Naciśnij klawisz ALT i podczas przenoszenia formantu wokół formularza.  
  
     Warto zauważyć, że są wyświetlane nie linie przyciągania formantu nie przyciąganie do wszelkich potencjalnych wyrównanie pozycji.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Aby wyłączyć linie przyciągania w środowisku projektowania programu  
  
1.  Z **narzędzia** menu, otwórz **opcje** okno dialogowe. Otwórz okno dialogowe Projektant formularzy systemu Windows. Aby uzyskać więcej informacji, zobacz [ogólne, Projektant formularzy systemu Windows, opcje — Okno dialogowe](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).  
  
2.  Wybierz **ogólne** węzła. W **tryb układu** sekcji, wybór z **linie przyciągania** do **SnapToGrid**.  
  
3.  Kliknij przycisk OK, aby zastosować ustawienia.  
  
4.  Wybierz kontrolkę w formularzu i przenosić inne formanty. Należy pamiętać, że nie są wyświetlane linie przyciągania.  
  
## <a name="next-steps"></a>Następne kroki  
 Linie przyciągania oferuje intuicyjny środków wyrównywanie formantów w formularzu. Sugestie dotyczące więcej eksploracji obejmują:  
  
-   Spróbuj zagnieżdżenia <xref:System.Windows.Forms.GroupBox> kontroli w innym <xref:System.Windows.Forms.GroupBox> formantu. Miejsce <xref:System.Windows.Forms.Button> formantu podrzędnego <xref:System.Windows.Forms.GroupBox> kontroli, a druga nadrzędnym <xref:System.Windows.Forms.GroupBox> formantu. Przenieś <xref:System.Windows.Forms.Button> formanty około, aby zobaczyć, jak linie przyciągania między granicami kontenera.  
  
-   Utwórz kolumnę z <xref:System.Windows.Forms.TextBox> kontrolek i odpowiednią kolumnę <xref:System.Windows.Forms.Label> kontrolki. Ustaw wartość <xref:System.Windows.Forms.Label> formantów <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`. Linie przyciągania umożliwia przenoszenie <xref:System.Windows.Forms.Label> kontrolki, ich wyświetlanego tekstu jest wyrównana z tekstem w <xref:System.Windows.Forms.TextBox> kontrolki.  
  
 Informacje dotyczące projektowania interfejsu użytkownika systemu Windows, zobacz podręcznik *środowisko użytkownika systemu Windows firmy Microsoft, oficjalnego wskazówki dla deweloperów interfejsu użytkownika i projektantów* Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
