---
title: Tworzenie kontrolki korzystającej z funkcji czasu projektowania programu Visual Studio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7166b4203c54ab31f1d929c85cf1e6481ff120f8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744077"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>Przewodnik: Tworzenie kontrolki korzystającej z funkcji czasu projektowania

Środowisko czasu projektowania dla kontrolki niestandardowej można rozszerzyć przez tworzenie skojarzonego projektanta niestandardowego.

W tym artykule przedstawiono sposób tworzenia niestandardowego projektanta dla kontrolki niestandardowej. Zaimplementowano typ `MarqueeControl` i skojarzoną klasę projektanta o nazwie `MarqueeControlRootDesigner`.

Typ `MarqueeControl` implementuje widok podobny do neonu, animowany sygnalizator i migający tekst.

Projektant tej kontrolki współdziała z środowiskiem projektowym w celu zapewnienia niestandardowego środowiska czasu projektowania. Za pomocą projektanta niestandardowego można utworzyć niestandardową implementację `MarqueeControl` z animowanymi sygnalizatorami i migającym tekstem w wielu kombinacjach. Możesz użyć asemblera kontrolki na formularzu podobnym do innego formantu Windows Forms.

Po zakończeniu pracy z tym przewodnikiem kontrolka niestandardowa będzie wyglądać następująco:

![Aplikacja wyświetlająca Neon z tekstem i przyciskami uruchamiania i zatrzymywania.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Aby zapoznać się z pełną listą kodu, zobacz [How to: Create a Windows Forms Control, który korzysta z funkcji czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Pierwszym krokiem jest utworzenie projektu aplikacji. Ten projekt będzie używany do kompilowania aplikacji, która hostuje kontrolkę niestandardową.

W programie Visual Studio Utwórz nowy projekt aplikacji Windows Forms, a następnie nadaj mu nazwę **MarqueeControlTest**.

## <a name="create-the-control-library-project"></a>Tworzenie projektu biblioteki formantów

1. Dodaj projekt biblioteki formantów Windows Forms do rozwiązania. Nazwij projekt **MarqueeControlLibrary**.

2. Korzystając z **Eksplorator rozwiązań**, usuń domyślną kontrolkę projektu, usuwając plik źródłowy o nazwie "UserControl1.cs" lub "UserControl1. vb", w zależności od wybranego języka.

3. Dodaj nowy element <xref:System.Windows.Forms.UserControl> do projektu `MarqueeControlLibrary`. Nadaj nowemu plikowi źródłowej nazwę bazową **MarqueeControl**.

4. Korzystając z **Eksplorator rozwiązań**, Utwórz nowy folder w `MarqueeControlLibrary` projekcie.

5. Kliknij prawym przyciskiem myszy folder **projekt** i Dodaj nową klasę. Nadaj mu nazwę **MarqueeControlRootDesigner**.

6. Musisz użyć typów z zestawu System. Design, więc Dodaj to odwołanie do projektu `MarqueeControlLibrary`.

## <a name="reference-the-custom-control-project"></a>Odwołuje się do projektu kontrolki niestandardowej

Aby przetestować kontrolkę niestandardową, użyjesz projektu `MarqueeControlTest`. Projekt testowy zostanie powiadomiony o kontrolce niestandardowej po dodaniu odwołania do projektu do zestawu `MarqueeControlLibrary`.

W projekcie `MarqueeControlTest` Dodaj odwołanie do projektu do zestawu `MarqueeControlLibrary`. Upewnij się, że korzystasz z karty **projekty** w oknie dialogowym **Dodaj odwołanie** zamiast odwoływać się bezpośrednio do zestawu `MarqueeControlLibrary`.

## <a name="define-a-custom-control-and-its-custom-designer"></a>Zdefiniuj kontrolkę niestandardową i jej projektanta niestandardowego

Kontrolka niestandardowa będzie pochodną klasy <xref:System.Windows.Forms.UserControl>. Dzięki temu formant może zawierać inne kontrolki i zapewnia kontrolę w dużej objęcie funkcją domyślną.

Kontrolka niestandardowa będzie dysponować skojarzonym projektantem niestandardowym. Pozwala to na utworzenie unikatowego środowiska projektowego dopasowanego specjalnie do kontrolki niestandardowej.

Formant można skojarzyć z jego projektantem za pomocą klasy <xref:System.ComponentModel.DesignerAttribute>. Ponieważ opracowujesz całe zachowanie w czasie projektowania niestandardowej kontrolki, Projektant niestandardowy Zaimplementuj interfejs <xref:System.ComponentModel.Design.IRootDesigner>.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Aby zdefiniować kontrolkę niestandardową i jej projektanta niestandardowego

1. Otwórz plik źródłowy `MarqueeControl` w **edytorze kodu**. W górnej części pliku Zaimportuj następujące przestrzenie nazw:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. Dodaj <xref:System.ComponentModel.DesignerAttribute> do deklaracji klasy `MarqueeControl`. Powoduje to skojarzenie kontrolki niestandardowej z jej projektantem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Otwórz plik źródłowy `MarqueeControlRootDesigner` w **edytorze kodu**. W górnej części pliku Zaimportuj następujące przestrzenie nazw:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Zmień deklarację `MarqueeControlRootDesigner` na dziedziczenie z klasy <xref:System.Windows.Forms.Design.DocumentDesigner>. Zastosuj <xref:System.ComponentModel.ToolboxItemFilterAttribute>, aby określić interakcję projektanta z **przybornikiem**.

   > [!NOTE]
   > Definicja klasy `MarqueeControlRootDesigner` została ujęta w przestrzeń nazw o nazwie MarqueeControlLibrary. Design. Ta deklaracja umieszcza projektanta w specjalnej przestrzeni nazw zarezerwowanej dla typów związanych z projektem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. Zdefiniuj konstruktora dla klasy `MarqueeControlRootDesigner`. Wstaw instrukcję <xref:System.Diagnostics.Trace.WriteLine%2A> w treści konstruktora. Będzie to przydatne podczas debugowania.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>Tworzenie wystąpienia kontrolki niestandardowej

1. Dodaj nowy element <xref:System.Windows.Forms.UserControl> do projektu `MarqueeControlTest`. Nadaj nowemu plikowi źródłowej nazwę bazową **DemoMarqueeControl**.

2. Otwórz plik `DemoMarqueeControl` w **edytorze kodu**. W górnej części pliku zaimportuj `MarqueeControlLibrary` przestrzeń nazw:

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. Zmień deklarację `DemoMarqueeControl` na dziedziczenie z klasy `MarqueeControl`.

4. Skompiluj projekt.

5. Otwórz formularz Form1 w Projektant formularzy systemu Windows.

6. Znajdź kartę **składniki MarqueeControlTest** w **przyborniku** i otwórz ją. Przeciągnij `DemoMarqueeControl` z **przybornika** do formularza.

7. Skompiluj projekt.

## <a name="set-up-the-project-for-design-time-debugging"></a>Konfigurowanie projektu na potrzeby debugowania w czasie projektowania

Podczas opracowywania niestandardowego środowiska czasu projektowania konieczne będzie Debugowanie formantów i składników. Istnieje prosty sposób skonfigurowania projektu w taki sposób, aby zezwalał na Debugowanie w czasie projektowania. Aby uzyskać więcej informacji, zobacz [Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

1. Kliknij prawym przyciskiem myszy projekt `MarqueeControlLibrary` i wybierz polecenie **Właściwości**.

2. W oknie dialogowym **MarqueeControlLibrary strony właściwości** wybierz stronę **debugowanie** .

3. W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny**. Będziesz debugować osobne wystąpienie programu Visual Studio, więc kliknij przycisk wielokropka (![przycisk wielokropka (...) na okno Właściwości przycisku programu Visual Studio](./media/visual-studio-ellipsis-button.png)), aby wyszukać środowisko IDE programu Visual Studio. Nazwa pliku wykonywalnego to devenv. exe, a jeśli została zainstalowana w lokalizacji domyślnej, jego ścieżka to *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*.

4. Wybierz **przycisk OK** , aby zamknąć okno dialogowe.

5. Kliknij prawym przyciskiem myszy projekt MarqueeControlLibrary i wybierz pozycję **Ustaw jako projekt startowy** , aby włączyć tę konfigurację debugowania.

## <a name="checkpoint"></a>Punkt kontrolny

Teraz można przystąpić do debugowania zachowania niestandardowej kontrolki czasu projektowania. Po ustaleniu, że środowisko debugowania jest prawidłowo skonfigurowane, należy przetestować skojarzenie między kontrolką niestandardową a projektantem niestandardowym.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Aby przetestować środowisko debugowania i skojarzenie projektanta

1. Otwórz plik źródłowy MarqueeControlRootDesigner w **edytorze kodu** i umieść punkt przerwania w instrukcji <xref:System.Diagnostics.Trace.WriteLine%2A>.

2. Naciśnij klawisz **F5** , aby rozpocząć sesję debugowania.

   Zostanie utworzone nowe wystąpienie programu Visual Studio.

3. W nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie MarqueeControlTest. Możesz łatwo znaleźć rozwiązanie, wybierając pozycję **ostatnie projekty** z menu **plik** . Plik rozwiązania MarqueeControlTest. sln zostanie wyświetlony jako ostatnio używany plik.

4. Otwórz `DemoMarqueeControl` w projektancie.

   Wystąpienie debugowania programu Visual Studio uzyskuje fokus i wykonywanie jest zatrzymywane w punkcie przerwania. Naciśnij klawisz **F5** , aby kontynuować sesję debugowania.

W tym momencie wszystko jest używane do tworzenia i debugowania formantu niestandardowego oraz skojarzonego z nim projektanta niestandardowego. Pozostała część tego artykułu koncentruje się na szczegółach implementacji funkcji formantu i projektanta.

## <a name="implement-the-custom-control"></a>Implementowanie kontrolki niestandardowej

`MarqueeControl` to <xref:System.Windows.Forms.UserControl> z małą ilością dostosowywać. Przedstawia dwie metody: `Start`, która uruchamia animację neonu i `Stop`, która powoduje zatrzymanie animacji. Ponieważ `MarqueeControl` zawiera kontrolki podrzędne implementujące interfejs `IMarqueeWidget`, `Start` i `Stop` wyliczają poszczególne kontrolki podrzędne i wywołują odpowiednio metody `StartMarquee` i `StopMarquee`, na każdym formancie podrzędnym, który implementuje `IMarqueeWidget`.

Wygląd `MarqueeBorder` i kontrolek `MarqueeText` zależy od układu, dlatego `MarqueeControl` przesłania metodę <xref:System.Windows.Forms.Control.OnLayout%2A> i wywołuje <xref:System.Windows.Forms.Control.PerformLayout%2A> w kontrolkach podrzędnych tego typu.

Jest to zakres dostosowań `MarqueeControl`. Funkcje czasu wykonywania są implementowane przez `MarqueeBorder` i `MarqueeText` kontrolki, a funkcje czasu projektowania są implementowane przez klasy `MarqueeBorderDesigner` i `MarqueeControlRootDesigner`.

### <a name="to-implement-your-custom-control"></a>Aby zaimplementować kontrolkę niestandardową

1. Otwórz plik źródłowy `MarqueeControl` w **edytorze kodu**. Zaimplementuj metody `Start` i `Stop`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Zastąp <xref:System.Windows.Forms.Control.OnLayout%2A> metody.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>Utwórz kontrolkę podrzędną dla kontrolki niestandardowej

`MarqueeControl` będzie hostować dwa rodzaje kontrolki podrzędnej: formant `MarqueeBorder` i kontrolka `MarqueeText`.

- `MarqueeBorder`: ten formant maluje obramowanie "świateł" wokół jego krawędzi. Lampki są błyskowe, aby były widoczne wokół krawędzi. Szybkość, z jaką lampy błyskowe są kontrolowane przez właściwość o nazwie `UpdatePeriod`. Kilka innych właściwości niestandardowych określa inne aspekty wyglądu kontrolki. Dwie metody, nazywane `StartMarquee` i `StopMarquee`, kontrolują, kiedy animacja zaczyna się i zatrzyma.

- `MarqueeText`: ten formant maluje migający ciąg. Podobnie jak w przypadku kontrolki `MarqueeBorder`, szybkość, z jaką błysk tekstu jest kontrolowana przez właściwość `UpdatePeriod`. Kontrolka `MarqueeText` ma także metody `StartMarquee` i `StopMarquee` wspólne z formantem `MarqueeBorder`.

W czasie projektowania `MarqueeControlRootDesigner` zezwala na dodawanie tych dwóch typów formantów do `MarqueeControl` w dowolnej kombinacji.

Typowe funkcje obu formantów są uwzględniane w interfejsie o nazwie `IMarqueeWidget`. Dzięki temu `MarqueeControl` odnajdywania dowolnych kontrolek podrzędnych związanych z neonem i nadawać im specjalne traktowanie.

Aby zaimplementować funkcję okresowej animacji, użyjesz <xref:System.ComponentModel.BackgroundWorker> obiektów z przestrzeni nazw <xref:System.ComponentModel?displayProperty=nameWithType>. Można użyć <xref:System.Windows.Forms.Timer> obiektów, ale jeśli istnieją wiele obiektów `IMarqueeWidget`, wątek pojedynczego interfejsu użytkownika może nie być w stanie zachować animacji.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Aby utworzyć kontrolkę podrzędną dla kontrolki niestandardowej

1. Dodaj nowy element klasy do projektu `MarqueeControlLibrary`. Nadaj nowemu plikowi źródłowej nazwę podstawową "IMarqueeWidget".

2. Otwórz plik źródłowy `IMarqueeWidget` w **edytorze kodu** i zmień deklarację z `class` na `interface`:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. Dodaj następujący kod do interfejsu `IMarqueeWidget`, aby uwidocznić dwie metody i właściwość, która manipuluje animacją neonu:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. Dodaj nowy element **kontrolki niestandardowej** do projektu `MarqueeControlLibrary`. Nadaj nowemu plikowi źródłowej nazwę podstawową "MarqueeText".

5. Przeciągnij składnik <xref:System.ComponentModel.BackgroundWorker> z **przybornika** na kontrolkę `MarqueeText`. Ten składnik zezwoli formantowi `MarqueeText` do samodzielnego aktualizowania.

6. W oknie **Właściwości** ustaw właściwości `WorkerReportsProgress` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> składnika <xref:System.ComponentModel.BackgroundWorker> na **wartość true**. Te ustawienia umożliwiają składnikowi <xref:System.ComponentModel.BackgroundWorker> okresowe zgłaszanie zdarzenia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i anulowanie aktualizacji asynchronicznych.

   Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](backgroundworker-component.md).

7. Otwórz plik źródłowy `MarqueeText` w **edytorze kodu**. W górnej części pliku Zaimportuj następujące przestrzenie nazw:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. Zmień deklarację `MarqueeText`, aby dziedziczyć po <xref:System.Windows.Forms.Label> i zaimplementować interfejs `IMarqueeWidget`:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Zadeklaruj zmienne wystąpienia, które odpowiadają uwidocznionym właściwościom, i zainicjuj je w konstruktorze. Pole `isLit` określa, czy tekst ma być malowany w kolorze podanym przez właściwość `LightColor`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Implementowanie `IMarqueeWidget` interfejsu.

    Metody `StartMarquee` i `StopMarquee` wywołują metody <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> składnika <xref:System.ComponentModel.BackgroundWorker>, aby uruchomić i zatrzymać animację.

    Atrybuty <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> są stosowane do właściwości `UpdatePeriod`, dlatego pojawiają się w sekcji niestandardowej okno Właściwości o nazwie "Markiza".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Zaimplementuj metody dostępu do właściwości. Udostępnimy dwie właściwości klientom: `LightColor` i `DarkColor`. Atrybuty <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> są stosowane do tych właściwości, więc właściwości są wyświetlane w sekcji niestandardowej okno Właściwości o nazwie "neon".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. Zaimplementuj programy obsługi dla zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> składnika <xref:System.ComponentModel.BackgroundWorker>.

    Procedura obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> uśpienia dla liczby milisekund określonych przez `UpdatePeriod` następnie wywołuje zdarzenie <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dopóki kod nie zatrzyma animacji przez wywołanie <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    Obsługa zdarzeń <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> przełącza tekst między jego oświetleniem i ciemnym stanem w celu uzyskania migania.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Zastąp metodę <xref:System.Windows.Forms.Control.OnPaint%2A>, aby włączyć animację.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Naciśnij klawisz **F6** , aby skompilować rozwiązanie.

## <a name="create-the-marqueeborder-child-control"></a>Utwórz formant podrzędny MarqueeBorder

Formant `MarqueeBorder` jest nieco bardziej skomplikowany niż kontrolka `MarqueeText`. Ma więcej właściwości, a animacja w metodzie <xref:System.Windows.Forms.Control.OnPaint%2A> jest większa. Zasadniczo jest to bardzo podobne do kontrolki `MarqueeText`.

Ponieważ kontrolka `MarqueeBorder` może mieć kontrolki podrzędne, musi mieć świadomość zdarzeń <xref:System.Windows.Forms.Control.Layout>.

### <a name="to-create-the-marqueeborder-control"></a>Aby utworzyć formant MarqueeBorder

1. Dodaj nowy element **kontrolki niestandardowej** do projektu `MarqueeControlLibrary`. Nadaj nowemu plikowi źródłowej nazwę podstawową "MarqueeBorder".

2. Przeciągnij składnik <xref:System.ComponentModel.BackgroundWorker> z **przybornika** na kontrolkę `MarqueeBorder`. Ten składnik zezwoli formantowi `MarqueeBorder` do samodzielnego aktualizowania.

3. W oknie **Właściwości** ustaw właściwości `WorkerReportsProgress` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> składnika <xref:System.ComponentModel.BackgroundWorker> na **wartość true**. Te ustawienia umożliwiają składnikowi <xref:System.ComponentModel.BackgroundWorker> okresowe zgłaszanie zdarzenia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i anulowanie aktualizacji asynchronicznych. Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](backgroundworker-component.md).

4. W oknie **Właściwości** wybierz przycisk **zdarzenia** . Dołącz programy obsługi dla zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>.

5. Otwórz plik źródłowy `MarqueeBorder` w **edytorze kodu**. W górnej części pliku Zaimportuj następujące przestrzenie nazw:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. Zmień deklarację `MarqueeBorder`, aby dziedziczyć po <xref:System.Windows.Forms.Panel> i zaimplementować interfejs `IMarqueeWidget`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. Zadeklaruj dwa wyliczenia, aby zarządzać stanem kontrolki `MarqueeBorder`: `MarqueeSpinDirection`, która określa kierunek, w którym sygnalizatory "pokrętło" wokół obramowania i `MarqueeLightShape`, które określają kształt świateł (kwadrat lub okrągły). Należy umieścić te deklaracje przed deklaracją klasy `MarqueeBorder`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Zadeklaruj zmienne wystąpienia, które odpowiadają uwidocznionym właściwościom, i zainicjuj je w konstruktorze.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Implementowanie `IMarqueeWidget` interfejsu.

    Metody `StartMarquee` i `StopMarquee` wywołują metody <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> składnika <xref:System.ComponentModel.BackgroundWorker>, aby uruchomić i zatrzymać animację.

    Ponieważ kontrolka `MarqueeBorder` może zawierać kontrolki podrzędne, Metoda `StartMarquee` wylicza wszystkie kontrolki podrzędne i wywołuje `StartMarquee` na tych, które implementują `IMarqueeWidget`. Metoda `StopMarquee` ma podobną implementację.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Zaimplementuj metody dostępu do właściwości. Kontrolka `MarqueeBorder` ma kilka właściwości do kontrolowania jego wyglądu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. Zaimplementuj programy obsługi dla zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> składnika <xref:System.ComponentModel.BackgroundWorker>.

    Procedura obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> uśpienia dla liczby milisekund określonych przez `UpdatePeriod` następnie wywołuje zdarzenie <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dopóki kod nie zatrzyma animacji przez wywołanie <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    Program obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zwiększa położenie światła "Base", z którego jest określany stan światła/ciemnego innych sygnalizatorów, i wywołuje metodę <xref:System.Windows.Forms.Control.Refresh%2A>, aby spowodować, że formant będzie odświeżał sam siebie.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Zaimplementuj metody pomocnika, `IsLit` i `DrawLight`.

    Metoda `IsLit` określa kolor światła w danym położeniu. Światła "zapala się" są rysowane w kolorze podanym przez właściwość `LightColor`, a te, które są "ciemne" są rysowane w kolorze podanym przez właściwość `DarkColor`.

    Metoda `DrawLight` rysuje oświetlenie przy użyciu odpowiedniego koloru, kształtu i pozycji.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. Zastąp metody <xref:System.Windows.Forms.Control.OnLayout%2A> i <xref:System.Windows.Forms.Control.OnPaint%2A>.

    Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> rysuje światła wzdłuż krawędzi kontrolki `MarqueeBorder`.

    Ponieważ metoda <xref:System.Windows.Forms.Control.OnPaint%2A> zależy od wymiarów kontrolki `MarqueeBorder`, należy wywołać ją za każdym razem, gdy zmieni się układ. Aby to osiągnąć, Zastąp <xref:System.Windows.Forms.Control.OnLayout%2A> i <xref:System.Windows.Forms.Control.Refresh%2A>wywołania.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>Tworzenie projektanta niestandardowego dla właściwości cieni i filtru

Klasa `MarqueeControlRootDesigner` dostarcza implementację głównego projektanta. Oprócz tego projektanta, który działa na `MarqueeControl`, potrzebny będzie niestandardowy Projektant, który jest skojarzony z formantem `MarqueeBorder`. Ten Projektant udostępnia niestandardowe zachowanie odpowiednie w kontekście niestandardowego projektanta głównego.

W konkretnym `MarqueeBorderDesigner` będzie "Shadow" i filtruje pewne właściwości kontrolki `MarqueeBorder`, zmieniając ich interakcje ze środowiskiem projektowym.

Przechwycenie wywołań metody dostępu do właściwości jest znane jako "przesłanianie". Umożliwia projektantowi śledzenie wartości ustawionej przez użytkownika i opcjonalne przekazywanie tej wartości do zaprojektowanego składnika.

Na potrzeby tego przykładu właściwości <xref:System.Windows.Forms.Control.Visible%2A> i <xref:System.Windows.Forms.Control.Enabled%2A> zostaną obsłonięte przez `MarqueeBorderDesigner`, co uniemożliwi użytkownikowi nieukrywanie lub wyłączenie kontrolki `MarqueeBorder` w czasie projektowania.

Projektanci mogą również dodawać i usuwać właściwości. W tym przykładzie właściwość <xref:System.Windows.Forms.Control.Padding%2A> zostanie usunięta w czasie projektowania, ponieważ kontrolka `MarqueeBorder` programowo ustawia uzupełnienie na podstawie rozmiaru świateł określonych przez właściwość `LightSize`.

Klasa bazowa dla `MarqueeBorderDesigner` jest <xref:System.ComponentModel.Design.ComponentDesigner>, która ma metody, które mogą zmieniać atrybuty, właściwości i zdarzenia udostępniane przez formant w czasie projektowania:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Podczas zmiany interfejsu publicznego składnika przy użyciu tych metod wykonaj następujące reguły:

- Dodaj lub Usuń elementy tylko w `PreFilter` metodach

- Modyfikuj tylko istniejące elementy w metodach `PostFilter`

- Zawsze Wywołaj implementację bazową najpierw w metodach `PreFilter`

- Zawsze Wywołaj implementację podstawową jako ostatnią w metodach `PostFilter`

Przestrzeganie tych reguł zapewnia, że wszystkie projektanci w środowisku czasu projektowania mają spójny widok wszystkich składników, które są zaprojektowane.

Klasa <xref:System.ComponentModel.Design.ComponentDesigner> zawiera słownik służący do zarządzania wartościami właściwości cieniowanych, co zwalnia konieczność tworzenia określonych zmiennych wystąpień.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Aby utworzyć projektanta niestandardowego dla właściwości cieni i filtru

1. Kliknij prawym przyciskiem myszy folder **projekt** i Dodaj nową klasę. Nadaj plikowi źródłowej podstawową nazwę **MarqueeBorderDesigner**.

2. Otwórz plik źródłowy MarqueeBorderDesigner w **edytorze kodu**. W górnej części pliku Zaimportuj następujące przestrzenie nazw:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Zmień deklarację `MarqueeBorderDesigner` na dziedziczenie z <xref:System.Windows.Forms.Design.ParentControlDesigner>.

    Ponieważ kontrolka `MarqueeBorder` może zawierać kontrolki podrzędne, `MarqueeBorderDesigner` dziedziczy po <xref:System.Windows.Forms.Design.ParentControlDesigner>, który obsługuje interakcję nadrzędny-podrzędny.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Zastąp podstawową implementację <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. Zaimplementuj właściwości <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A>. Te implementacje zasłaniają właściwości kontrolki.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>Obsługa zmian składników

Klasa `MarqueeControlRootDesigner` udostępnia niestandardowe środowisko czasu projektowania dla wystąpień `MarqueeControl`. Większość funkcji czasu projektowania jest dziedziczona z klasy <xref:System.Windows.Forms.Design.DocumentDesigner>. Twój kod Zaimplementuj dwa specyficzne dostosowania: obsługa zmian składników i Dodawanie zleceń projektanta.

Podczas projektowania wystąpień `MarqueeControl` przez użytkowników Projektant główny będzie śledził zmiany w `MarqueeControl` i jego kontrolkach podrzędnych. Środowisko czasu projektowania oferuje wygodną usługę, <xref:System.ComponentModel.Design.IComponentChangeService>do śledzenia zmian stanu składnika.

Uzyskujesz odwołanie do tej usługi, badając środowisko przy użyciu metody <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>. Jeśli zapytanie zakończyło się pomyślnie, Projektant może dołączyć procedurę obsługi dla zdarzenia <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> i wykonać wszelkie zadania wymagane do zapewnienia spójnego stanu w czasie projektowania.

W przypadku klasy `MarqueeControlRootDesigner` należy wywołać metodę <xref:System.Windows.Forms.Control.Refresh%2A> dla każdego obiektu `IMarqueeWidget` zawartego w `MarqueeControl`. Spowoduje to, że obiekt `IMarqueeWidget` ma być odpowiednio odświeżany, gdy zostaną zmienione właściwości, takie jak <xref:System.Windows.Forms.Control.Size%2A> elementu nadrzędnego.

### <a name="to-handle-component-changes"></a>Aby obsłużyć zmiany składników

1. Otwórz plik źródłowy `MarqueeControlRootDesigner` w **edytorze kodu** i Zastąp metodę <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>. Wywołaj podstawową implementację <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> i zapytania dla <xref:System.ComponentModel.Design.IComponentChangeService>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. Zaimplementuj procedurę obsługi zdarzeń <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>. Przetestuj typ składnika wysyłającego, a jeśli jest to `IMarqueeWidget`, wywołaj jego <xref:System.Windows.Forms.Control.Refresh%2A> metodę.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>Dodawanie zleceń projektanta do projektanta niestandardowego

Zlecenie projektanta jest poleceniem menu połączonym z programem obsługi zdarzeń. Zlecenia projektanta są dodawane do menu skrótów składnika w czasie projektowania. Aby uzyskać więcej informacji, zobacz temat <xref:System.ComponentModel.Design.DesignerVerb>.

Do projektantów zostaną dodane dwa zlecenia projektanta: **Uruchom test** i **Zatrzymaj test**. Te czasowniki umożliwią wyświetlenie zachowania `MarqueeControl` w czasie wykonywania w czasie projektowania. Te zlecenia zostaną dodane do `MarqueeControlRootDesigner`.

Gdy jest wywoływany **Test Run** , program obsługi zdarzeń zlecenia wywoła metodę `StartMarquee` na `MarqueeControl`. Po wywołaniu **testu zatrzymania** program obsługi zdarzeń zlecenia wywoła metodę `StopMarquee` w `MarqueeControl`. Implementacja metod `StartMarquee` i `StopMarquee` wywoływanie tych metod na zawartych kontrolkach, które implementują `IMarqueeWidget`, tak aby wszystkie zawarte kontrolki `IMarqueeWidget` również uczestniczyły w teście.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Aby dodać czasowniki projektanta do niestandardowych projektantów

1. W klasie `MarqueeControlRootDesigner` Dodaj programy obsługi zdarzeń o nazwie `OnVerbRunTest` i `OnVerbStopTest`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Połącz te programy obsługi zdarzeń z odpowiednimi zleceniami projektanta. `MarqueeControlRootDesigner` dziedziczy <xref:System.ComponentModel.Design.DesignerVerbCollection> z klasy podstawowej. Utworzysz dwa nowe obiekty <xref:System.ComponentModel.Design.DesignerVerb> i dodasz je do tej kolekcji w metodzie <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>Tworzenie niestandardowego UITypeEditor

Podczas tworzenia niestandardowego środowiska czasu projektowania dla użytkowników często pożądane jest utworzenie interakcji niestandardowej z okno Właściwości. Można to zrobić, tworząc <xref:System.Drawing.Design.UITypeEditor>.

Formant `MarqueeBorder` uwidacznia kilka właściwości w okno Właściwości. Dwie z tych właściwości, `MarqueeSpinDirection` i `MarqueeLightShape` są reprezentowane przez wyliczenia. Aby zilustrować użycie edytora typów interfejsu użytkownika, właściwość `MarqueeLightShape` będzie miała skojarzoną klasę <xref:System.Drawing.Design.UITypeEditor>.

### <a name="to-create-a-custom-ui-type-editor"></a>Aby utworzyć niestandardowy Edytor typów interfejsu użytkownika

1. Otwórz plik źródłowy `MarqueeBorder` w **edytorze kodu**.

2. W definicji klasy `MarqueeBorder` deklaruj klasę o nazwie `LightShapeEditor`, która pochodzi z <xref:System.Drawing.Design.UITypeEditor>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. Zadeklaruj zmienną wystąpienia <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> o nazwie `editorService`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Zastąp <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody. Ta implementacja zwraca <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, co informuje środowisko projektowe o sposobie wyświetlania `LightShapeEditor`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Zastąp <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody. Ta implementacja wysyła zapytanie do środowiska projektowego dla obiektu <xref:System.Windows.Forms.Design.IWindowsFormsEditorService>. W przypadku pomyślnego utworzenia `LightShapeSelectionControl`. Metoda <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> jest wywoływana w celu uruchomienia `LightShapeEditor`. Wartość zwracana z tego wywołania jest zwracana do środowiska projektowego.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>Tworzenie kontrolki widoku dla niestandardowego UITypeEditor

Właściwość `MarqueeLightShape` obsługuje dwa typy świateł: `Square` i `Circle`. Utworzysz kontrolkę niestandardową używaną wyłącznie na potrzeby graficznego wyświetlania tych wartości w okno Właściwości. Ta kontrolka niestandardowa będzie używana przez <xref:System.Drawing.Design.UITypeEditor> do korzystania z okno Właściwości.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Aby utworzyć kontrolkę widoku dla niestandardowego edytora typów interfejsu użytkownika

1. Dodaj nowy element <xref:System.Windows.Forms.UserControl> do projektu `MarqueeControlLibrary`. Nadaj nowemu plikowi źródłowej nazwę bazową **LightShapeSelectionControl**.

2. Przeciągnij dwie <xref:System.Windows.Forms.Panel> kontrolki z **przybornika** na `LightShapeSelectionControl`. Nadaj mu nazwę `squarePanel` i `circlePanel`. Rozmieść je obok siebie. Ustaw właściwość <xref:System.Windows.Forms.Control.Size%2A> obu <xref:System.Windows.Forms.Panel> formantów na **(60, 60)** . Ustaw właściwość <xref:System.Windows.Forms.Control.Location%2A> kontrolki `squarePanel` na **(8, 10)** . Ustaw właściwość <xref:System.Windows.Forms.Control.Location%2A> kontrolki `circlePanel` na **(80, 10)** . Na koniec ustaw właściwość <xref:System.Windows.Forms.Control.Size%2A> `LightShapeSelectionControl` na wartość **(150, 80)** .

3. Otwórz plik źródłowy `LightShapeSelectionControl` w **edytorze kodu**. W górnej części pliku zaimportuj <xref:System.Windows.Forms.Design?displayProperty=nameWithType> przestrzeń nazw:

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. Zaimplementuj obsługę zdarzeń <xref:System.Windows.Forms.Control.Click> dla kontrolek `squarePanel` i `circlePanel`. Te metody wywołują <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>, aby zakończyć sesję niestandardowego <xref:System.Drawing.Design.UITypeEditor> edycji.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. Zadeklaruj zmienną wystąpienia <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> o nazwie `editorService`.

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. Zadeklaruj zmienną wystąpienia `MarqueeLightShape` o nazwie `lightShapeValue`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. W konstruktorze `LightShapeSelectionControl` Dołącz obsługę zdarzeń <xref:System.Windows.Forms.Control.Click> do `squarePanel` i `circlePanel` formantów <xref:System.Windows.Forms.Control.Click>. Ponadto Zdefiniuj przeciążenie konstruktora, które przypisuje wartość `MarqueeLightShape` ze środowiska projektowego do pola `lightShapeValue`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. W <xref:System.ComponentModel.Component.Dispose%2A> metodzie Odłącz <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** . Otwórz plik LightShapeSelectionControl.Designer.cs lub LightShapeSelectionControl. Designer. vb i usuń definicję domyślną metody <xref:System.ComponentModel.Component.Dispose%2A>.

10. Zaimplementuj Właściwość `LightShape`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Ta implementacja spowoduje narysowanie wypełnionego kwadratu i okręgu. Zostanie również wyświetlona wybrana wartość przez narysowanie obramowania wokół jednego kształtu lub drugiego.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>Testowanie kontrolki niestandardowej w projektancie

W tym momencie można skompilować projekt `MarqueeControlLibrary`. Przetestuj swoją implementację, tworząc kontrolkę, która dziedziczy z klasy `MarqueeControl` i korzystając z niej w formularzu.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Aby utworzyć niestandardową implementację MarqueeControl

1. Otwórz `DemoMarqueeControl` w Projektant formularzy systemu Windows. Spowoduje to utworzenie wystąpienia typu `DemoMarqueeControl` i wyświetlenie go w wystąpieniu typu `MarqueeControlRootDesigner`.

2. W **przyborniku**Otwórz kartę **składniki MarqueeControlLibrary** . Zobaczysz kontrolki `MarqueeBorder` i `MarqueeText` dostępne do wyboru.

3. Przeciągnij wystąpienie kontrolki `MarqueeBorder` na powierzchnię projektową `DemoMarqueeControl`. Zadokuj tę `MarqueeBorder` kontrolkę do kontrolki nadrzędnej.

4. Przeciągnij wystąpienie kontrolki `MarqueeText` na powierzchnię projektową `DemoMarqueeControl`.

5. Skompiluj rozwiązanie.

6. Kliknij prawym przyciskiem myszy `DemoMarqueeControl` i z menu skrótów wybierz opcję **Uruchom test** , aby rozpocząć animację. Kliknij przycisk **Zatrzymaj test** , aby zatrzymać animację.

7. Otwórz **formularz Form1** w widok Projekt.

8. Umieść dwa <xref:System.Windows.Forms.Button> kontrolki w formularzu. Nadaj mu nazwę `startButton` i `stopButton`i Zmień <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości tak, aby odpowiednio **uruchamiać** i **zatrzymywać**.

9. Zaimplementuj obsługę zdarzeń <xref:System.Windows.Forms.Control.Click> dla obu formantów <xref:System.Windows.Forms.Button>.

10. W **przyborniku**Otwórz kartę **składniki MarqueeControlTest** . Zobaczysz `DemoMarqueeControl` dostępne do wyboru.

11. Przeciągnij wystąpienie `DemoMarqueeControl` na powierzchnię projektu **Form1** .

12. W obsłudze zdarzeń <xref:System.Windows.Forms.Control.Click> wywołaj metody `Start` i `Stop` na `DemoMarqueeControl`.

    ```vb
    Private Sub startButton_Click(sender As Object, e As System.EventArgs)
        Me.demoMarqueeControl1.Start()
    End Sub 'startButton_Click

    Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Stop()
    End Sub 'stopButton_Click
    ```

    ```csharp
    private void startButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Start();
    }

    private void stopButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Stop();
    }
    ```

13. Ustaw projekt `MarqueeControlTest` jako projekt startowy i uruchom go. Zobaczysz formularz wyświetlający `DemoMarqueeControl`. Wybierz przycisk **Start** , aby rozpocząć animację. Powinieneś zobaczyć migający tekst i sygnalizatory poruszające się wokół obramowania.

## <a name="next-steps"></a>Następne kroki

`MarqueeControlLibrary` ilustruje prostą implementację formantów niestandardowych i skojarzonych projektantów. Ten przykład można zwiększyć na kilka sposobów:

- Zmień wartości właściwości `DemoMarqueeControl` w projektancie. Dodaj więcej formantów `MarqueBorder` i Zadokuj je w wystąpieniach nadrzędnych, aby utworzyć efekt zagnieżdżony. Eksperymentuj z różnymi ustawieniami `UpdatePeriod` i właściwościami jasnymi.

- Twórz własne implementacje `IMarqueeWidget`. Można na przykład utworzyć migający znak "neon" lub animowany znak z wieloma obrazami.

- Dalsze dostosowywanie środowiska czasu projektowania. Możesz wypróbować więcej właściwości niż <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A>i dodać nowe właściwości. Dodaj nowe czasowniki projektanta, aby uprościć typowe zadania, takie jak dokowanie formantów podrzędnych.

- Licencjonowanie `MarqueeControl`.

- Kontroluj sposób serializacji formantów i sposób generowania kodu. Aby uzyskać więcej informacji, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
