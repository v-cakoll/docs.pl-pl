---
title: 'Przewodnik: tworzenie kontrolki formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 53824336e1ae47870e6acffe20340f145caf9b4d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182594"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>Przewodnik: Tworzenie kontrolki korzystającej z funkcji czasu projektowania

Środowisko czasu projektowania dla kontrolki niestandardowej można rozszerzyć przez tworzenie skojarzonego projektanta niestandardowego.

W tym artykule przedstawiono sposób tworzenia niestandardowego projektanta dla kontrolki niestandardowej. Należy zaimplementować `MarqueeControl` typ i skojarzoną klasę projektanta o nazwie `MarqueeControlRootDesigner`.

`MarqueeControl` Typ implementuje ekran podobny do neonu, animowane sygnalizatory i migający tekst.

Projektant tej kontrolki współdziała z środowiskiem projektowym w celu zapewnienia niestandardowego środowiska czasu projektowania. Za pomocą projektanta niestandardowego można złożyć implementację niestandardową `MarqueeControl` z animowanymi sygnalizatorami i migającym tekstem w wielu kombinacjach. Możesz użyć asemblera kontrolki na formularzu podobnym do innego formantu Windows Forms.

Po zakończeniu pracy z tym przewodnikiem kontrolka niestandardowa będzie wyglądać następująco:

![Aplikacja wyświetlająca Neon z tekstem i przyciskami uruchamiania i zatrzymywania.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Aby zapoznać się z pełną listą [kodu, zobacz How to: Utwórz formant Windows Forms, który korzysta z funkcji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))czasu projektowania.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Pierwszym krokiem jest utworzenie projektu aplikacji. Ten projekt będzie używany do kompilowania aplikacji, która hostuje kontrolkę niestandardową.

W programie Visual Studio Utwórz nowy projekt aplikacji Windows Forms, a następnie nadaj mu nazwę **MarqueeControlTest**.

## <a name="create-the-control-library-project"></a>Tworzenie projektu biblioteki formantów

1. Dodaj projekt biblioteki formantów Windows Forms do rozwiązania. Nazwij projekt **MarqueeControlLibrary**.

2. Korzystając z **Eksplorator rozwiązań**, usuń domyślną kontrolkę projektu, usuwając plik źródłowy o nazwie "UserControl1.cs" lub "UserControl1. vb", w zależności od wybranego języka.

3. Dodaj nowy <xref:System.Windows.Forms.UserControl> element `MarqueeControlLibrary` do projektu. Nadaj nowemu plikowi źródłowej nazwę bazową **MarqueeControl**.

4. Za pomocą **Eksplorator rozwiązań**, Utwórz nowy folder w `MarqueeControlLibrary` projekcie.

5. Kliknij prawym przyciskiem myszy folder **projekt** i Dodaj nową klasę. Nadaj mu nazwę **MarqueeControlRootDesigner**.

6. Musisz użyć typów z zestawu System. Design, więc Dodaj to odwołanie do `MarqueeControlLibrary` projektu.

## <a name="reference-the-custom-control-project"></a>Odwołuje się do projektu kontrolki niestandardowej

Ten `MarqueeControlTest` projekt zostanie użyty do przetestowania kontrolki niestandardowej. Projekt testowy zostanie powiadomiony o kontrolce niestandardowej po dodaniu odwołania do projektu do `MarqueeControlLibrary` zestawu.

W projekcie Dodaj odwołanie do projektu do `MarqueeControlLibrary` zestawu. `MarqueeControlTest` Upewnij się, że korzystasz z karty **projekty** w oknie dialogowym **Dodaj odwołanie** zamiast bezpośrednio odwoływać się do `MarqueeControlLibrary` zestawu.

## <a name="define-a-custom-control-and-its-custom-designer"></a>Zdefiniuj kontrolkę niestandardową i jej projektanta niestandardowego

Kontrolka niestandardowa będzie pochodną <xref:System.Windows.Forms.UserControl> klasy. Dzięki temu formant może zawierać inne kontrolki i zapewnia kontrolę w dużej objęcie funkcją domyślną.

Kontrolka niestandardowa będzie dysponować skojarzonym projektantem niestandardowym. Pozwala to na utworzenie unikatowego środowiska projektowego dopasowanego specjalnie do kontrolki niestandardowej.

Formant można skojarzyć z jego projektantem za pomocą <xref:System.ComponentModel.DesignerAttribute> klasy. Ponieważ opracowujesz całe zachowanie w czasie projektowania niestandardowej kontrolki, Projektant niestandardowy Zaimplementuj <xref:System.ComponentModel.Design.IRootDesigner> interfejs.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Aby zdefiniować kontrolkę niestandardową i jej projektanta niestandardowego

1. Otwórz plik źródłowy w **edytorze kodu.** `MarqueeControl` W górnej części pliku Zaimportuj następujące przestrzenie nazw:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <xref:System.ComponentModel.DesignerAttribute> Dodaj`MarqueeControl` do deklaracji klasy. Powoduje to skojarzenie kontrolki niestandardowej z jej projektantem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Otwórz plik źródłowy w **edytorze kodu.** `MarqueeControlRootDesigner` W górnej części pliku Zaimportuj następujące przestrzenie nazw:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Zmień deklarację elementu `MarqueeControlRootDesigner` , aby dziedziczyć <xref:System.Windows.Forms.Design.DocumentDesigner> z klasy. Zastosuj, <xref:System.ComponentModel.ToolboxItemFilterAttribute> aby określić interakcję projektanta z **przybornikiem**.

   > [!NOTE]
   > Definicja `MarqueeControlRootDesigner` klasy została ujęta w przestrzeń nazw o nazwie MarqueeControlLibrary. Design. Ta deklaracja umieszcza projektanta w specjalnej przestrzeni nazw zarezerwowanej dla typów związanych z projektem.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. Zdefiniuj konstruktora dla `MarqueeControlRootDesigner` klasy. <xref:System.Diagnostics.Trace.WriteLine%2A> Wstaw instrukcję w treści konstruktora. Będzie to przydatne podczas debugowania.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>Tworzenie wystąpienia kontrolki niestandardowej

1. Dodaj nowy <xref:System.Windows.Forms.UserControl> element `MarqueeControlTest` do projektu. Nadaj nowemu plikowi źródłowej nazwę bazową **DemoMarqueeControl**.

2. Otwórz plik w **edytorze kodu.** `DemoMarqueeControl` W górnej części pliku zaimportuj `MarqueeControlLibrary` przestrzeń nazw:

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. Zmień deklarację elementu `DemoMarqueeControl` , aby dziedziczyć `MarqueeControl` z klasy.

4. Skompiluj projekt.

5. Otwórz formularz Form1 w Projektant formularzy systemu Windows.

6. Znajdź kartę **składniki MarqueeControlTest** w **przyborniku** i otwórz ją. Przeciągnij z `DemoMarqueeControl` **przybornika** do formularza.

7. Skompiluj projekt.

## <a name="set-up-the-project-for-design-time-debugging"></a>Konfigurowanie projektu na potrzeby debugowania w czasie projektowania

Podczas opracowywania niestandardowego środowiska czasu projektowania konieczne będzie Debugowanie formantów i składników. Istnieje prosty sposób skonfigurowania projektu w taki sposób, aby zezwalał na Debugowanie w czasie projektowania. Aby uzyskać więcej informacji, [zobacz Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)projektowania.

1. Kliknij prawym przyciskiem `MarqueeControlLibrary` myszy projekt i wybierz polecenie **Właściwości**.

2. W oknie dialogowym **MarqueeControlLibrary strony właściwości** wybierz stronę **debugowanie** .

3. W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny**. Debugujesz osobne wystąpienie programu Visual Studio, więc kliknij![przycisk wielokropka (przycisk wielokropka (...) w okno właściwości programu Visual Studio](./media/visual-studio-ellipsis-button.png)), aby wyszukać środowisko IDE programu Visual Studio. Nazwa pliku wykonywalnego to devenv. exe, a jeśli została zainstalowana w lokalizacji domyślnej, jego ścieżka to *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE\devenv.exe*.

4. Wybierz **przycisk OK** , aby zamknąć okno dialogowe.

5. Kliknij prawym przyciskiem myszy projekt MarqueeControlLibrary i wybierz pozycję **Ustaw jako projekt startowy** , aby włączyć tę konfigurację debugowania.

## <a name="checkpoint"></a>Punkt kontrolny

Teraz można przystąpić do debugowania zachowania niestandardowej kontrolki czasu projektowania. Po ustaleniu, że środowisko debugowania jest prawidłowo skonfigurowane, należy przetestować skojarzenie między kontrolką niestandardową a projektantem niestandardowym.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Aby przetestować środowisko debugowania i skojarzenie projektanta

1. Otwórz plik źródłowy MarqueeControlRootDesigner w **edytorze kodu** i umieść punkt przerwania w <xref:System.Diagnostics.Trace.WriteLine%2A> instrukcji.

2. Naciśnij klawisz **F5** , aby rozpocząć sesję debugowania.

   Zostanie utworzone nowe wystąpienie programu Visual Studio.

3. W nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie MarqueeControlTest. Możesz łatwo znaleźć rozwiązanie, wybierając pozycję **ostatnie projekty** z menu **plik** . Plik rozwiązania MarqueeControlTest. sln zostanie wyświetlony jako ostatnio używany plik.

4. `DemoMarqueeControl` Otwórz w projektancie.

   Wystąpienie debugowania programu Visual Studio uzyskuje fokus i wykonywanie jest zatrzymywane w punkcie przerwania. Naciśnij klawisz **F5** , aby kontynuować sesję debugowania.

W tym momencie wszystko jest używane do tworzenia i debugowania formantu niestandardowego oraz skojarzonego z nim projektanta niestandardowego. Pozostała część tego artykułu koncentruje się na szczegółach implementacji funkcji formantu i projektanta.

## <a name="implement-the-custom-control"></a>Implementowanie kontrolki niestandardowej

`MarqueeControl` Jestto<xref:System.Windows.Forms.UserControl> bardzo mały bit dostosowywania. Przedstawia dwie metody: `Start`, która uruchamia animację neonu i `Stop`, która powoduje zatrzymanie animacji. `StartMarquee` `IMarqueeWidget` `StopMarquee` `Stop` `Start` Ponieważ zawiera kontrolki podrzędne, które implementują interfejs, i wylicza każdą kontrolkę podrzędną i wywołuje odpowiednio metody i, w każdej kontrolce podrzędnej `MarqueeControl` który implementuje `IMarqueeWidget`.

`MarqueeBorder` Wygląd formantów i `MarqueeText` jest zależny od `MarqueeControl` <xref:System.Windows.Forms.Control.PerformLayout%2A> układu, dlatego zastępuje metodęiwywołaniaformantówpodrzędnychtegotypu.<xref:System.Windows.Forms.Control.OnLayout%2A>

Jest to zakres `MarqueeControl` dostosowań. Funkcje czasu wykonywania `MarqueeBorder` są implementowane przez i `MarqueeText` kontrolki, a `MarqueeBorderDesigner` funkcje czasu projektowania są implementowane przez klasy i `MarqueeControlRootDesigner` .

### <a name="to-implement-your-custom-control"></a>Aby zaimplementować kontrolkę niestandardową

1. Otwórz plik źródłowy w **edytorze kodu.** `MarqueeControl` Zaimplementuj metody `Stop`i. `Start`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Zastąp <xref:System.Windows.Forms.Control.OnLayout%2A> metody.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>Utwórz kontrolkę podrzędną dla kontrolki niestandardowej

Program będzie hostować dwa rodzaje kontrolki podrzędnej `MarqueeBorder` : formant i `MarqueeText` formant. `MarqueeControl`

- `MarqueeBorder`: Ta kontrolka maluje obramowanie "świateł" wokół jego krawędzi. Lampki są błyskowe, aby były widoczne wokół krawędzi. Szybkość, z jaką lampy błyskowe są kontrolowane przez właściwość o `UpdatePeriod`nazwie. Kilka innych właściwości niestandardowych określa inne aspekty wyglądu kontrolki. Dwie metody, nazywane `StartMarquee` i `StopMarquee`, kontrolują, kiedy animacja zaczyna się i kończy.

- `MarqueeText`: Ta kontrolka maluje migający ciąg. Podobnie jak `MarqueeBorder` w przypadku kontrolki, szybkość, z jaką błysk tekstu jest kontrolowana `UpdatePeriod` przez właściwość. Formant zawiera również `MarqueeBorder` metody `StopMarquee` i, które są wspólne z kontrolką. `StartMarquee` `MarqueeText`

W czasie projektowania, `MarqueeControlRootDesigner` umożliwia dodanie tych dwóch typów kontrolek `MarqueeControl` do dowolnej kombinacji.

Typowe funkcje obu formantów są uwzględniane w interfejsie o nazwie `IMarqueeWidget`. Umożliwia `MarqueeControl` to odnajdywanie wszelkich kontrolek podrzędnych związanych z neonem i nadawanie im specjalnej obróbki.

Aby zaimplementować funkcję okresowej animacji, użyjesz <xref:System.ComponentModel.BackgroundWorker> obiektów <xref:System.ComponentModel?displayProperty=nameWithType> z przestrzeni nazw. Można używać <xref:System.Windows.Forms.Timer> obiektów, ale gdy istnieje wiele `IMarqueeWidget` obiektów, wątek pojedynczego interfejsu użytkownika może nie być w stanie zachować animacji.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Aby utworzyć kontrolkę podrzędną dla kontrolki niestandardowej

1. Dodaj nowy element klasy do `MarqueeControlLibrary` projektu. Nadaj nowemu plikowi źródłowej nazwę podstawową "IMarqueeWidget".

2. Otwórz plik `class` `interface`źródłowy w **edytorze kodu** i zmień deklarację z na: `IMarqueeWidget`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. Dodaj następujący kod do `IMarqueeWidget` interfejsu, aby uwidocznić dwie metody i właściwość, która manipuluje animacją neonu:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. Dodaj nowy element **kontrolki niestandardowej** do `MarqueeControlLibrary` projektu. Nadaj nowemu plikowi źródłowej nazwę podstawową "MarqueeText".

5. Przeciągnij składnik z **przybornika** na `MarqueeText`kontrolkę <xref:System.ComponentModel.BackgroundWorker> . Ten składnik umożliwi `MarqueeText` formantowi aktualizację siebie asynchronicznie.

6. W oknie **Właściwości** Ustaw <xref:System.ComponentModel.BackgroundWorker> dla składnika `WorkerReportsProgress` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości **wartość true**. Te ustawienia umożliwiają <xref:System.ComponentModel.BackgroundWorker> składnikowi okresowe <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zgłaszanie zdarzenia i anulowanie aktualizacji asynchronicznych.

   Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](backgroundworker-component.md).

7. Otwórz plik źródłowy w **edytorze kodu.** `MarqueeText` W górnej części pliku Zaimportuj następujące przestrzenie nazw:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. Zmień deklarację `MarqueeText` , aby dziedziczyć <xref:System.Windows.Forms.Label> z i aby zaimplementować `IMarqueeWidget` interfejs:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Zadeklaruj zmienne wystąpienia, które odpowiadają uwidocznionym właściwościom, i zainicjuj je w konstruktorze. Pole określa, czy tekst ma być malowany w kolorze podanym `LightColor` przez właściwość. `isLit`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Implementowanie `IMarqueeWidget` interfejsu.

    `StartMarquee` Metodyi`StopMarquee` wywołują<xref:System.ComponentModel.BackgroundWorker> składnik i<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>metody , aby uruchomić i zatrzymać animację. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>

    Atrybuty i są<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> stosowane do właściwości,takabypojawiłysięwsekcjiniestandardowejoknowłaściwościonazwie"neon".`UpdatePeriod` <xref:System.ComponentModel.CategoryAttribute.Category%2A>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Zaimplementuj metody dostępu do właściwości. Udostępnimy dwie właściwości klientom: `LightColor` i. `DarkColor` Atrybuty <xref:System.ComponentModel.CategoryAttribute.Category%2A> i<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> są stosowane do tych właściwości, więc właściwości są wyświetlane w sekcji niestandardowej okno właściwości o nazwie "neon".

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. Zaimplementuj procedury obsługi dla <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.DoWork> składników i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń.

    Procedura obsługi `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>zdarzeń w stanie uśpienia przez liczbę milisekund określoną przez następnie wywołuje zdarzenie, dopóki kod nie zatrzyma animacji przez wywołanie. <xref:System.ComponentModel.BackgroundWorker.DoWork>

    Program <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> obsługi zdarzeń przełącza tekst między jasnym i ciemnym stanem, aby dać migający wygląd.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metodę, aby włączyć animację.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Naciśnij klawisz **F6** , aby skompilować rozwiązanie.

## <a name="create-the-marqueeborder-child-control"></a>Utwórz formant podrzędny MarqueeBorder

Kontrolka jest nieco bardziej zaawansowana `MarqueeText` niż kontrolka. `MarqueeBorder` Ma więcej właściwości, a animacja w <xref:System.Windows.Forms.Control.OnPaint%2A> metodzie jest większa. Zasadniczo jest to bardzo podobne do `MarqueeText` kontrolki.

Ponieważ kontrolka może mieć kontrolki podrzędne, musi mieć <xref:System.Windows.Forms.Control.Layout> świadomość zdarzeń. `MarqueeBorder`

### <a name="to-create-the-marqueeborder-control"></a>Aby utworzyć formant MarqueeBorder

1. Dodaj nowy element **kontrolki niestandardowej** do `MarqueeControlLibrary` projektu. Nadaj nowemu plikowi źródłowej nazwę podstawową "MarqueeBorder".

2. Przeciągnij składnik z **przybornika** na `MarqueeBorder`kontrolkę <xref:System.ComponentModel.BackgroundWorker> . Ten składnik umożliwi `MarqueeBorder` formantowi aktualizację siebie asynchronicznie.

3. W oknie **Właściwości** Ustaw <xref:System.ComponentModel.BackgroundWorker> dla składnika `WorkerReportsProgress` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości **wartość true**. Te ustawienia umożliwiają <xref:System.ComponentModel.BackgroundWorker> składnikowi okresowe <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zgłaszanie zdarzenia i anulowanie aktualizacji asynchronicznych. Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](backgroundworker-component.md).

4. W oknie **Właściwości** wybierz przycisk **zdarzenia** . Dołącz programy obsługi dla <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń i. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>

5. Otwórz plik źródłowy w **edytorze kodu.** `MarqueeBorder` W górnej części pliku Zaimportuj następujące przestrzenie nazw:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. Zmień deklarację `MarqueeBorder` , aby dziedziczyć <xref:System.Windows.Forms.Panel> z i aby zaimplementować `IMarqueeWidget` interfejs.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. Zadeklaruj dwa wyliczenia do zarządzania `MarqueeBorder` stanem formantu: `MarqueeSpinDirection`, który określa kierunek, w którym sygnalizatory "pokrętła" dookoła obramowania, i `MarqueeLightShape`, który określa kształt świateł (kwadrat lub okrągły). Należy `MarqueeBorder` umieścić te deklaracje przed deklaracją klasy.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Zadeklaruj zmienne wystąpienia, które odpowiadają uwidocznionym właściwościom, i zainicjuj je w konstruktorze.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Implementowanie `IMarqueeWidget` interfejsu.

    `StartMarquee` Metodyi`StopMarquee` wywołują<xref:System.ComponentModel.BackgroundWorker> składnik i<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>metody , aby uruchomić i zatrzymać animację. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>

    Ponieważ kontrolka może zawierać kontrolki podrzędne `StartMarquee` , Metoda wylicza wszystkie kontrolki podrzędne i wywołuje `StartMarquee` te, które implementują `IMarqueeWidget`. `MarqueeBorder` `StopMarquee` Metoda ma podobną implementację.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Zaimplementuj metody dostępu do właściwości. `MarqueeBorder` Kontrolka ma kilka właściwości do kontrolowania jej wyglądu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. Zaimplementuj procedury obsługi dla <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.DoWork> składników i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń.

    Procedura obsługi `UpdatePeriod` <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>zdarzeń w stanie uśpienia przez liczbę milisekund określoną przez następnie wywołuje zdarzenie, dopóki kod nie zatrzyma animacji przez wywołanie. <xref:System.ComponentModel.BackgroundWorker.DoWork>

    Program obsługi <xref:System.Windows.Forms.Control.Refresh%2A> zdarzeń zwiększa położenie światła "podstawowe", z którego jest określany stan światła i ciemny innych sygnalizatorów, i wywołuje metodę, aby spowodować, że formant będzie odświeżał sam siebie. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Zaimplementuj metody `IsLit` pomocnika i `DrawLight`.

    `IsLit` Metoda określa kolor światła w danym położeniu. Światła "zapala się" są rysowane w kolorze podanym przez `LightColor` właściwość, a te, które są "ciemne" są rysowane w kolorze podanym `DarkColor` przez właściwość.

    `DrawLight` Metoda rysuje światło przy użyciu odpowiedniego koloru, kształtu i pozycji.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. Zastąp metody <xref:System.Windows.Forms.Control.OnPaint%2A>i. <xref:System.Windows.Forms.Control.OnLayout%2A>

    Metoda rysuje sygnalizatory wzdłuż krawędzi `MarqueeBorder` formantu. <xref:System.Windows.Forms.Control.OnPaint%2A>

    Ponieważ metoda zależy od wymiarów `MarqueeBorder` kontrolki, należy wywołać ją za każdym razem, gdy zmieni się układ. <xref:System.Windows.Forms.Control.OnPaint%2A> Aby to osiągnąć, Przesłoń <xref:System.Windows.Forms.Control.OnLayout%2A> i Wywołaj. <xref:System.Windows.Forms.Control.Refresh%2A>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>Tworzenie projektanta niestandardowego dla właściwości cieni i filtru

`MarqueeControlRootDesigner` Klasa zawiera implementację głównego projektanta. Oprócz tego projektanta, który działa w `MarqueeControl`programie, potrzebny będzie niestandardowy Projektant, który jest skojarzony `MarqueeBorder` z formantem. Ten Projektant udostępnia niestandardowe zachowanie odpowiednie w kontekście niestandardowego projektanta głównego.

W konkretnym `MarqueeBorderDesigner` przypadku będzie to "cień" i filtruje pewne `MarqueeBorder` właściwości kontrolki, zmieniając ich interakcje ze środowiskiem projektowym.

Przechwycenie wywołań metody dostępu do właściwości jest znane jako "przesłanianie". Umożliwia projektantowi śledzenie wartości ustawionej przez użytkownika i opcjonalne przekazywanie tej wartości do zaprojektowanego składnika.

Na potrzeby tego przykładu <xref:System.Windows.Forms.Control.Visible%2A> właściwości <xref:System.Windows.Forms.Control.Enabled%2A> i zostaną obsłonięte przez `MarqueeBorderDesigner` `MarqueeBorder` , co uniemożliwi użytkownikowi nieukrywanie lub wyłączenie kontrolki w czasie projektowania.

Projektanci mogą również dodawać i usuwać właściwości. W tym przykładzie <xref:System.Windows.Forms.Control.Padding%2A> właściwość zostanie usunięta w czasie projektowania, `MarqueeBorder` ponieważ kontrolka programowo ustawia uzupełnienie na podstawie rozmiaru świateł określonych przez `LightSize` właściwość.

Klasa bazowa dla `MarqueeBorderDesigner` to <xref:System.ComponentModel.Design.ComponentDesigner>, która ma metody, które mogą zmieniać atrybuty, właściwości i zdarzenia udostępniane przez formant w czasie projektowania:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Podczas zmiany interfejsu publicznego składnika przy użyciu tych metod wykonaj następujące reguły:

- Dodaj lub Usuń elementy tylko w `PreFilter` metodach

- Modyfikuj istniejące elementy tylko w `PostFilter` metodach

- Zawsze Wywołaj implementację bazową najpierw `PreFilter` w metodach

- Zawsze Wywołaj implementację podstawową ostatnio w `PostFilter` metodach

Przestrzeganie tych reguł zapewnia, że wszystkie projektanci w środowisku czasu projektowania mają spójny widok wszystkich składników, które są zaprojektowane.

<xref:System.ComponentModel.Design.ComponentDesigner> Klasa zawiera słownik służący do zarządzania wartościami właściwości cieniowanych, co zwalnia konieczność tworzenia określonych zmiennych wystąpień.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Aby utworzyć projektanta niestandardowego dla właściwości cieni i filtru

1. Kliknij prawym przyciskiem myszy folder **projekt** i Dodaj nową klasę. Nadaj plikowi źródłowej podstawową nazwę **MarqueeBorderDesigner**.

2. Otwórz plik źródłowy MarqueeBorderDesigner w **edytorze kodu**. W górnej części pliku Zaimportuj następujące przestrzenie nazw:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Zmień deklarację elementu `MarqueeBorderDesigner` , aby <xref:System.Windows.Forms.Design.ParentControlDesigner>dziedziczyć.

    Ponieważ kontrolka może zawierać kontrolki podrzędne `MarqueeBorderDesigner` , dziedziczy <xref:System.Windows.Forms.Design.ParentControlDesigner>po, która obsługuje interakcję nadrzędny-podrzędny. `MarqueeBorder`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Zastąp podstawową implementację <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>programu.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. Zaimplementuj właściwości <xref:System.Windows.Forms.Control.Visible%2A>i. <xref:System.Windows.Forms.Control.Enabled%2A> Te implementacje zasłaniają właściwości kontrolki.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>Obsługa zmian składników

Klasa udostępnia niestandardowe środowisko czasu projektowania `MarqueeControl` dla wystąpień. `MarqueeControlRootDesigner` Większość funkcji czasu projektowania jest dziedziczona z <xref:System.Windows.Forms.Design.DocumentDesigner> klasy. Twój kod Zaimplementuj dwa specyficzne dostosowania: obsługa zmian składników i Dodawanie zleceń projektanta.

Gdy użytkownicy zaprojektowają swoje `MarqueeControl` wystąpienia, Projektant główny będzie śledził zmiany `MarqueeControl` w i jego kontrolkach podrzędnych. Środowisko czasu projektowania oferuje wygodną usługę <xref:System.ComponentModel.Design.IComponentChangeService>, umożliwiając śledzenie zmian stanu składnika.

Uzyskujesz odwołanie do tej usługi, badając środowisko przy użyciu <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody. Jeśli zapytanie zakończyło się pomyślnie, Projektant może dołączyć procedurę obsługi dla <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> zdarzenia i wykonać wszelkie zadania wymagane do zapewnienia spójnego stanu w czasie projektowania.

W przypadku `MarqueeControlRootDesigner` klasy, <xref:System.Windows.Forms.Control.Refresh%2A> Metoda zostanie wywołana dla `MarqueeControl`każdego `IMarqueeWidget` obiektu zawartego w. Spowoduje to, że `IMarqueeWidget` obiekt jest odpowiednio odświeżany, gdy właściwości, takie jak jego <xref:System.Windows.Forms.Control.Size%2A> element nadrzędny, zostaną zmienione.

### <a name="to-handle-component-changes"></a>Aby obsłużyć zmiany składników

1. Otwórz plik <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> źródłowy w edytorze kodu i Zastąp metodę. `MarqueeControlRootDesigner` Wywołaj podstawową implementację <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> i zapytaj <xref:System.ComponentModel.Design.IComponentChangeService>o.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. Zaimplementuj procedurę obsługi zdarzeń. <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> Przetestuj typ składnika wysyłającego, a jeśli jest `IMarqueeWidget`, wywołaj jego <xref:System.Windows.Forms.Control.Refresh%2A> metodę.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>Dodawanie zleceń projektanta do projektanta niestandardowego

Zlecenie projektanta jest poleceniem menu połączonym z programem obsługi zdarzeń. Zlecenia projektanta są dodawane do menu skrótów składnika w czasie projektowania. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Design.DesignerVerb>.

Do projektantów są dodawane dwa zlecenia projektanta: **Uruchom test** i **Zatrzymaj test**. Te czasowniki umożliwią wyświetlenie zachowania `MarqueeControl` w czasie wykonywania w czasie projektowania. Te zlecenia zostaną dodane do `MarqueeControlRootDesigner`.

Gdy jest wywoływany **Test Run** , program obsługi zdarzeń zlecenia wywoła `StartMarquee` metodę w. `MarqueeControl` Po wywołaniu **testu zatrzymania** program obsługi zdarzeń zlecenia wywoła `StopMarquee` metodę w. `MarqueeControl` Implementacja `StartMarquee` metod i `StopMarquee` wywołuje te metody na zawartych kontrolkach, które implementują `IMarqueeWidget`, tak aby wszystkie `IMarqueeWidget` zawarte kontrolki również uczestniczyły w teście.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Aby dodać czasowniki projektanta do niestandardowych projektantów

1. W klasie Dodaj programy obsługi zdarzeń o nazwach `OnVerbRunTest` i `OnVerbStopTest`. `MarqueeControlRootDesigner`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Połącz te programy obsługi zdarzeń z odpowiednimi zleceniami projektanta. `MarqueeControlRootDesigner`<xref:System.ComponentModel.Design.DesignerVerbCollection> dziedziczy z klasy bazowej. Utworzysz dwa nowe <xref:System.ComponentModel.Design.DesignerVerb> obiekty i dodasz je do tej kolekcji <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> w metodzie.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>Tworzenie niestandardowego UITypeEditor

Podczas tworzenia niestandardowego środowiska czasu projektowania dla użytkowników często pożądane jest utworzenie interakcji niestandardowej z okno Właściwości. Można to zrobić, tworząc <xref:System.Drawing.Design.UITypeEditor>.

`MarqueeBorder` Formant uwidacznia kilka właściwości w okno właściwości. Dwie z tych właściwości `MarqueeSpinDirection` i `MarqueeLightShape` są reprezentowane przez wyliczenia. Aby zilustrować użycie edytora typów interfejsu użytkownika, `MarqueeLightShape` właściwość będzie miała skojarzoną <xref:System.Drawing.Design.UITypeEditor> klasę.

### <a name="to-create-a-custom-ui-type-editor"></a>Aby utworzyć niestandardowy Edytor typów interfejsu użytkownika

1. Otwórz plik źródłowy w **edytorze kodu.** `MarqueeBorder`

2. W definicji `MarqueeBorder` klasy deklaruj klasę o nazwie `LightShapeEditor` , która dziedziczy z <xref:System.Drawing.Design.UITypeEditor>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. Zadeklaruj zmienną `editorService` <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> wystąpienia o nazwie.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Zastąp <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody. Ta implementacja zwraca <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, która informuje środowisko projektowe o sposobie `LightShapeEditor`wyświetlania.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Zastąp <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody. Ta implementacja wysyła zapytanie do środowiska projektowego <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> dla obiektu. Po pomyślnym utworzeniu `LightShapeSelectionControl`. Metoda jest wywoływana w celu `LightShapeEditor`uruchomienia. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Wartość zwracana z tego wywołania jest zwracana do środowiska projektowego.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>Tworzenie kontrolki widoku dla niestandardowego UITypeEditor

Właściwość obsługuje dwa typy jasnych kształtów: `Square` i `Circle`. `MarqueeLightShape` Utworzysz kontrolkę niestandardową używaną wyłącznie na potrzeby graficznego wyświetlania tych wartości w okno Właściwości. Ta kontrolka niestandardowa będzie używana <xref:System.Drawing.Design.UITypeEditor> przez użytkownika do korzystania z okno właściwości.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Aby utworzyć kontrolkę widoku dla niestandardowego edytora typów interfejsu użytkownika

1. Dodaj nowy <xref:System.Windows.Forms.UserControl> element `MarqueeControlLibrary` do projektu. Nadaj nowemu plikowi źródłowej nazwę bazową **LightShapeSelectionControl**.

2. Przeciągnij dwie <xref:System.Windows.Forms.Panel> kontrolki `LightShapeSelectionControl`z **przybornika** na. Nadaj mu `squarePanel` nazwę `circlePanel`i. Rozmieść je obok siebie. Ustaw właściwość obu <xref:System.Windows.Forms.Panel> kontrolek na **(60, 60).** <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> Ustaw właściwość `squarePanel` kontrolki na **(8, 10)** . <xref:System.Windows.Forms.Control.Location%2A> Ustaw właściwość `circlePanel` kontrolki na **(80, 10)** . Na koniec Ustaw <xref:System.Windows.Forms.Control.Size%2A> Właściwość `LightShapeSelectionControl` na **(150, 80)** .

3. Otwórz plik źródłowy w **edytorze kodu.** `LightShapeSelectionControl` W górnej części pliku zaimportuj <xref:System.Windows.Forms.Design?displayProperty=nameWithType> przestrzeń nazw:

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. Implementuj <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń `squarePanel` dla formantów i `circlePanel` . Te metody są <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> wywoływane, aby zakończyć <xref:System.Drawing.Design.UITypeEditor> sesję edycji niestandardowej.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. Zadeklaruj zmienną `editorService` <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> wystąpienia o nazwie.

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. Zadeklaruj zmienną `lightShapeValue` `MarqueeLightShape` wystąpienia o nazwie.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <xref:System.Windows.Forms.Control.Click> `squarePanel` `circlePanel` W konstruktorze Dołącz obsługę zdarzeń<xref:System.Windows.Forms.Control.Click> do zdarzeń i kontrolek. `LightShapeSelectionControl` Ponadto Zdefiniuj przeciążenie konstruktora, które przypisuje `MarqueeLightShape` wartość ze środowiska projektowego `lightShapeValue` do pola.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. W metodzie Odłącz procedury obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń. <xref:System.ComponentModel.Component.Dispose%2A>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** . Otwórz plik LightShapeSelectionControl.Designer.cs lub LightShapeSelectionControl. Designer. vb i usuń definicję <xref:System.ComponentModel.Component.Dispose%2A> domyślną metody.

10. Zaimplementuj `LightShape` właściwość.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Ta implementacja spowoduje narysowanie wypełnionego kwadratu i okręgu. Zostanie również wyświetlona wybrana wartość przez narysowanie obramowania wokół jednego kształtu lub drugiego.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>Testowanie kontrolki niestandardowej w projektancie

W tym momencie można skompilować `MarqueeControlLibrary` projekt. Przetestuj swoją implementację, tworząc kontrolkę, która dziedziczy `MarqueeControl` z klasy i korzystając z niej w formularzu.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Aby utworzyć niestandardową implementację MarqueeControl

1. Otwórz `DemoMarqueeControl` w Projektant formularzy systemu Windows. Spowoduje to utworzenie wystąpienia `DemoMarqueeControl` typu i wyświetlenie go w wystąpieniu `MarqueeControlRootDesigner` typu.

2. W **przyborniku**Otwórz kartę **składniki MarqueeControlLibrary** . Zobaczysz kontrolki `MarqueeText`idostępne do wyboru. `MarqueeBorder`

3. Przeciągnij wystąpienie `MarqueeBorder` kontrolki `DemoMarqueeControl` na powierzchnię projektu. Zadokuj tę `MarqueeBorder` kontrolkę z kontrolką nadrzędną.

4. Przeciągnij wystąpienie `MarqueeText` kontrolki `DemoMarqueeControl` na powierzchnię projektu.

5. Skompiluj rozwiązanie.

6. Kliknij prawym przyciskiem `DemoMarqueeControl` myszy i z menu skrótów wybierz opcję **Uruchom test** , aby rozpocząć animację. Kliknij przycisk **Zatrzymaj test** , aby zatrzymać animację.

7. Otwórz **formularz Form1** w widok Projekt.

8. Umieść dwie <xref:System.Windows.Forms.Button> kontrolki w formularzu. Nadaj mu `startButton` nazwę `stopButton`i i Zmień <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości, aby odpowiednio **uruchomić** i **zatrzymać**.

9. Implementuj <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń dla obu <xref:System.Windows.Forms.Button> formantów.

10. W **przyborniku**Otwórz kartę **składniki MarqueeControlTest** . Zobaczysz `DemoMarqueeControl` dostępne do wyboru.

11. Przeciągnij wystąpienie `DemoMarqueeControl` na powierzchnię projektu **Form1** .

12. W programach obsługi `Start` `Stop` `DemoMarqueeControl`zdarzeń wywołaj metody i w. <xref:System.Windows.Forms.Control.Click>

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

13. `MarqueeControlTest` Ustaw projekt jako projekt startowy i uruchom go. Zobaczysz formularz `DemoMarqueeControl`z. Wybierz przycisk **Start** , aby rozpocząć animację. Powinieneś zobaczyć migający tekst i sygnalizatory poruszające się wokół obramowania.

## <a name="next-steps"></a>Następne kroki

`MarqueeControlLibrary` Pokazuje prostą implementację formantów niestandardowych i skojarzonych projektantów. Ten przykład można zwiększyć na kilka sposobów:

- Zmień wartości `DemoMarqueeControl` właściwości w projektancie. Dodaj więcej `MarqueBorder` kontrolek i Zadokuj je w wystąpieniach nadrzędnych, aby utworzyć zagnieżdżony efekt. Eksperymentuj z różnymi ustawieniami `UpdatePeriod` i właściwościami ze światłami.

- Twórz własne implementacje programu `IMarqueeWidget`. Można na przykład utworzyć migający znak "neon" lub animowany znak z wieloma obrazami.

- Dalsze dostosowywanie środowiska czasu projektowania. Można wypróbować więcej właściwości niż <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A>i dodać nowe właściwości. Dodaj nowe czasowniki projektanta, aby uprościć typowe zadania, takie jak dokowanie formantów podrzędnych.

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
