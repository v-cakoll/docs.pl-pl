---
title: 'Przewodnik: Tworzenie kontrolki formularzy Windows wykorzystującego funkcje czasu projektowania w programie Visual Studio'
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
ms.openlocfilehash: cb102ec9b3a7eb4673f42c2ca5ad876e049ff59c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146280"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>Przewodnik: Tworzenie kontrolki formularzy Windows wykorzystującego funkcje czasu projektowania w programie Visual Studio
Środowisko czasu projektowania formantu niestandardowego może zostać poprawione tworząc skojarzone niestandardowego projektanta.  
  
 W tym instruktażu przedstawiono sposób tworzenia niestandardowego projektanta dla formantu niestandardowego. Zostaną zaimplementowane `MarqueeControl` typu i skojarzone projektanta klasę o nazwie `MarqueeControlRootDesigner`.  
  
 `MarqueeControl` Typ implementuje ekran podobny do ramkę theater animowany światła i migających tekstem.  
  
 Projektanta dla tego formantu wchodzi w interakcje ze środowiskiem projektowania w celu zapewnienia niestandardowe środowiska czasu projektowania. Za pomocą niestandardowego projektanta, można utworzyć niestandardowy `MarqueeControl` implementację animowany światła i migających tekst w wielu kombinacji. Można użyć zmontowanych kontrolki na formularzu jak inne kontrolki Windows Forms.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu  
  
-   Tworzenie projektu biblioteki kontrolek  
  
-   Odwołanie do projektu kontrolki niestandardowej  
  
-   Definiowanie niestandardowego formantu i jego niestandardowego projektanta  
  
-   Utworzenie wystąpienia formantu niestandardowego  
  
-   Konfigurowanie projektu dla debugowania w czasie projektowania  
  
-   Implementowanie kontrolki niestandardowej  
  
-   Tworzenie kontrolki podrzędnej kontrolki niestandardowej  
  
-   Tworzenie kontrolki podrzędnej MarqueeBorder  
  
-   Tworzenie niestandardowego projektanta w tle i właściwości filtru  
  
-   Obsługa zmiany składnika  
  
-   Dodanie zlecenia projektanta do niestandardowego projektanta  
  
-   Tworzenie niestandardowych UITypeEditor  
  
-   Testowanie niestandardowego formantu w Projektancie  
  
 Po zakończeniu niestandardową kontrolkę będą wyglądać następująco:  
  
 ![Możliwe formantu MarqueeControl](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 Lista kompletny kod znajduje się [jak: Tworzenie formantu formularzy Windows wykorzystującego funkcje czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu aplikacji. Użyjesz tego projektu do kompilowania aplikacji, który jest hostem kontrolki niestandardowej.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz projekt Windows Forms aplikacji o nazwie "MarqueeControlTest" (**pliku** > **New** > **projektu**  >   **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
## <a name="creating-a-control-library-project"></a>Tworzenie projektu biblioteki kontrolek  
 Następnym krokiem jest, aby utworzyć projekt Biblioteka formantów. Utworzysz nowego formantu niestandardowego i jego odpowiedniego niestandardowego projektanta.  
  
#### <a name="to-create-the-control-library-project"></a>Aby utworzyć projekt Biblioteka formantów  
  
1.  Dodaj projekt Biblioteka kontrolek formularzy Windows do rozwiązania. Nazwij projekt "MarqueeControlLibrary."  
  
2.  Za pomocą **Eksploratora rozwiązań**, usunąć projekt domyślny formant przez usunięcie pliku źródłowego o nazwie "UserControl1.cs" lub "UserControl1.vb", w zależności od tego, w wybranym języku. Aby uzyskać więcej informacji, zobacz [jak: Usuń Delete i wykluczyć elementy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).  
  
3.  Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do `MarqueeControlLibrary` projektu. Nazwij nowy plik źródłowy podstawowego elementu "MarqueeControl."  
  
4.  Za pomocą **Eksploratora rozwiązań**, Utwórz nowy folder w `MarqueeControlLibrary` projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodaj nowe elementy projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)). Nadaj nazwę nowego folderu "Projekt".  
  
5.  Kliknij prawym przyciskiem myszy **projektowania** folderze i Dodaj nową klasę. Nadaj plikowi źródła podstawowej nazwy "MarqueeControlRootDesigner."  
  
6.  Należy używać typów z zestawu System.Design, dlatego należy dodać to odwołanie do `MarqueeControlLibrary` projektu.  
  
    > [!NOTE]
    >  Aby użyć zestawu System.Design, projekt musi być przeznaczony pełną wersję programu .NET Framework nie .NET Framework Client Profile. Aby zmienić platformę docelową, zobacz [jak: Docelowa wersja systemu .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).  
  
## <a name="referencing-the-custom-control-project"></a>Odwołanie do projektu kontrolki niestandardowej  
 Użyjesz `MarqueeControlTest` projekt do przetestowania kontrolki niestandardowej. Projekt testowy, dowie się o formant niestandardowy, podczas dodawania odwołania projektu do `MarqueeControlLibrary` zestawu.  
  
#### <a name="to-reference-the-custom-control-project"></a>Aby odwoływać się do projektu kontrolki niestandardowej  
  
-   W `MarqueeControlTest` projektu, należy dodać odwołanie projektu do `MarqueeControlLibrary` zestawu. Należy użyć **projektów** karcie **Dodaj odwołanie** okno dialogowe zamiast odwoływać się do `MarqueeControlLibrary` bezpośrednio w zestawie.  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a>Definiowanie niestandardowego formantu i jego niestandardowego projektanta  
 Niestandardową kontrolkę, z której pochodzą z <xref:System.Windows.Forms.UserControl> klasy. Dzięki temu kontrolki zawiera inne kontrolki, a także zapewnia kontroli nad dużym stopniem funkcje domyślne.  
  
 Kontrolki niestandardowe mają skojarzone niestandardowego projektanta. Dzięki temu można utworzyć środowisko projektowania unikatowy dostosowanych specjalnie dla formantu niestandardowego.  
  
 Kojarzenie kontrolki za pomocą projektanta jej przy użyciu <xref:System.ComponentModel.DesignerAttribute> klasy. Ponieważ tworzysz całego zachowania niestandardową kontrolkę w czasie projektowania niestandardowego projektanta wdroży <xref:System.ComponentModel.Design.IRootDesigner> interfejsu.  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Aby zdefiniować kontrolkę niestandardową i jej niestandardowego projektanta  
  
1.  Otwórz `MarqueeControl` pliku źródłowego w **Edytor kodu**. W górnej części pliku zaimportuj następujące przestrzenie nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  Dodaj <xref:System.ComponentModel.DesignerAttribute> do `MarqueeControl` deklaracji klasy. Skojarzenie formantu niestandardowego za pomocą swojego projektanta.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  Otwórz `MarqueeControlRootDesigner` pliku źródłowego w **Edytor kodu**. W górnej części pliku zaimportuj następujące przestrzenie nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  Zmień deklarację `MarqueeControlRootDesigner` odziedziczone <xref:System.Windows.Forms.Design.DocumentDesigner> klasy. Zastosuj <xref:System.ComponentModel.ToolboxItemFilterAttribute> do określenia projektanta interakcji z **przybornika**.  
  
     **Uwaga** definicji `MarqueeControlRootDesigner` klasy ma został ujęty w przestrzeni nazw o nazwie "MarqueeControlLibrary.Design." Ta deklaracja umieszcza projektanta w specjalnych przestrzeni nazw zarezerwowane dla typów projektu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  Definiowanie konstruktora dla `MarqueeControlRootDesigner` klasy. Wstaw <xref:System.Diagnostics.Trace.WriteLine%2A> instrukcji w treści konstruktora. Spowoduje to być przydatne na potrzeby debugowania.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a>Utworzenie wystąpienia formantu niestandardowego  
 Aby obserwować niestandardowe zachowania formantu w czasie projektowania, zostaną umieszczone wystąpienie formantu w formularzu w `MarqueeControlTest` projektu.  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a>Aby utworzyć wystąpienie kontrolki niestandardowej  
  
1.  Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do `MarqueeControlTest` projektu. Nazwij nowy plik źródłowy podstawowego elementu "DemoMarqueeControl."  
  
2.  Otwórz `DemoMarqueeControl` w pliku **Edytor kodu**. W górnej części pliku, należy zaimportować `MarqueeControlLibrary` przestrzeni nazw:  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  Zmień deklarację `DemoMarqueeControl` odziedziczone `MarqueeControl` klasy.  
  
2.  Skompiluj projekt.  
  
3.  Otwórz `Form1` w programie Windows Forms Designer.  
  
4.  Znajdź **składniki MarqueeControlTest** karcie **przybornika** i otwórz go. Przeciągnij `DemoMarqueeControl` z **przybornika** do formularza.  
  
5.  Skompiluj projekt.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Konfigurowanie projektu dla debugowania w czasie projektowania  
 Podczas tworzenia niestandardowego środowiska czasu projektowania, będzie trzeba debugować swoje formanty i składniki. Brak prosty sposób skonfigurować projekt w celu zezwolenia na debugowanie w czasie projektowania. Aby uzyskać więcej informacji, zobacz [instruktażu: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Aby skonfigurować projekt do debugowania w czasie projektowania  
  
1.  Kliknij prawym przyciskiem myszy `MarqueeControlLibrary` projektu, a następnie wybierz **właściwości**.  
  
2.  W oknie dialogowym "MarqueeControlLibrary stron właściwości" Wybierz **debugowania** strony.  
  
3.  W **Akcja uruchamiania** zaznacz **Uruchom zewnętrzny Program**. Można więc debugowanie osobnego wystąpienia programu Visual Studio, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby przejść do środowiska IDE programu Visual Studio. Nazwa pliku wykonywalnego jest devenv.exe, a jeśli został zainstalowany w lokalizacji domyślnej, jego ścieżka jest %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.  
  
4.  Kliknij przycisk OK, aby zamknąć okno dialogowe.  
  
5.  Kliknij prawym przyciskiem myszy `MarqueeControlLibrary` projektu, a następnie wybierz pozycję "Ustaw jako projekt startowy" Aby umożliwić tej konfiguracji debugowania.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 Teraz można przystąpić do debugowania zachowania w czasie projektowania formantu niestandardowego. Po określeniu, czy środowisko debugowania jest prawidłowo skonfigurowane, przetestujesz skojarzenie między formantu niestandardowego i niestandardowego projektanta.  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Aby przetestować środowisko debugowania i skojarzenia projektanta  
  
1.  Otwórz `MarqueeControlRootDesigner` pliku źródłowego w **Edytor kodu** i umieść punkt przerwania na <xref:System.Diagnostics.Trace.WriteLine%2A> instrukcji.  
  
2.  Naciśnij klawisz F5, aby rozpocząć sesję debugowania. Należy pamiętać, że tworzone jest nowe wystąpienie programu Visual Studio.  
  
3.  Nowe wystąpienie programu Visual Studio Otwórz rozwiązanie "MarqueeControlTest". Rozwiązanie można łatwo znaleźć, wybierając **ostatnich projektów** z **pliku** menu. Plik rozwiązania "MarqueeControlTest.sln" będą wyświetlane zgodnie z ostatnio używanych plików.  
  
4.  Otwórz `DemoMarqueeControl` w projektancie. Należy pamiętać, że wystąpienie debugowania programu Visual Studio uzyskuje fokus i wykonywania zatrzymuje się na punkt przerwania. Naciśnij klawisz F5, aby kontynuować sesję debugowania.  
  
 W tym momencie jest wszystko, co umożliwia programowanie i debugowanie niestandardową kontrolkę i jego skojarzone niestandardowego projektanta. W pozostałej części tego przewodnika koncentruje się na szczegółowe informacje o implementacji funkcji kontroli i projektanta.  
  
## <a name="implementing-your-custom-control"></a>Implementowanie kontrolki niestandardowej  
 `MarqueeControl` Jest <xref:System.Windows.Forms.UserControl> z trochę dostosowywania. Udostępnia dwie metody: `Start`, co spowoduje włączenie animacji neonu i `Stop`, co uniemożliwia animacji. Ponieważ `MarqueeControl` zawiera formanty podrzędne, które implementują `IMarqueeWidget` interfejsu `Start` i `Stop` wyliczanie każdej kontrolki podrzędnej i wywołania `StartMarquee` i `StopMarquee` metod, odpowiednio, na każdej kontrolki podrzędnej implementującej `IMarqueeWidget`.  
  
 Wygląd `MarqueeBorder` i `MarqueeText` kontrolki jest zależna od układu, dzięki czemu `MarqueeControl` zastępuje <xref:System.Windows.Forms.Control.OnLayout%2A> metodę i wywołuje <xref:System.Windows.Forms.Control.PerformLayout%2A> kontrolek podrzędnych tego typu.  
  
 Jest to zakres `MarqueeControl` dostosowań. Funkcje środowiska wykonawczego są implementowane przez `MarqueeBorder` i `MarqueeText` formanty i funkcje czasu projektowania są implementowane przez `MarqueeBorderDesigner` i `MarqueeControlRootDesigner` klasy.  
  
#### <a name="to-implement-your-custom-control"></a>Aby zaimplementować formant niestandardowy  
  
1.  Otwórz `MarqueeControl` pliku źródłowego w **Edytor kodu**. Implementowanie `Start` i `Stop` metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  Zastąp <xref:System.Windows.Forms.Control.OnLayout%2A> metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a>Tworzenie kontrolki podrzędnej kontrolki niestandardowej  
 `MarqueeControl` Będzie obsługiwać dwa rodzaje kontrolki podrzędnej: `MarqueeBorder` kontroli i `MarqueeText` kontroli.  
  
-   `MarqueeBorder`: Ten formant do malowania obramowanie "światła" wokół jego krawędzi. Kontrolki programu flash w sekwencji, aby były widoczne przemieszczają się wokół obramowania. Szybkość jaką flash kontrolki jest kontrolowana przez właściwość o nazwie `UpdatePeriod`. Kilka właściwości niestandardowe, określ inne aspekty wyglądu formantu. Dwie metody, o nazwie `StartMarquee` i `StopMarquee`, kontrolować podczas uruchamiania i zatrzymywania w animacji.  
  
-   `MarqueeText`: Ten formant do malowania migające ciągu. Podobnie jak `MarqueeBorder` kontrolki, szybkość jaką miga tekst jest kontrolowana przez `UpdatePeriod` właściwości. `MarqueeText` Kontroli ma również `StartMarquee` i `StopMarquee` metody wspólnego z `MarqueeBorder` kontroli.  
  
 W czasie projektowania `MarqueeControlRootDesigner` umożliwia te typy dwóch kontrolek do dodania do `MarqueeControl` w dowolnej kombinacji.  
  
 Często używane funkcje dwóch formantów są rozkładane na interfejs o nazwie `IMarqueeWidget`. Dzięki temu `MarqueeControl` próbę odnalezienia formanty powiązane ramki podrzędne i nadaj im specjalnego traktowania.  
  
 Aby zaimplementować funkcję okresowe animacji, należy skorzystać <xref:System.ComponentModel.BackgroundWorker> obiekty <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw. Można użyć <xref:System.Windows.Forms.Timer> obiektów, ale gdy wiele `IMarqueeWidget` obiektów, pojedynczego wątku interfejsu użytkownika nie będą mogli nadążyć za animacji.  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a>Aby utworzyć kontrolki podrzędnej kontrolki niestandardowej  
  
1.  Dodaj nowy element klasy do `MarqueeControlLibrary` projektu. Nazwij nowy plik źródłowy podstawowego elementu "IMarqueeWidget."  
  
2.  Otwórz `IMarqueeWidget` pliku źródłowego w **Edytor kodu** i zmień deklarację z `class` do `interface`:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  Dodaj następujący kod do `IMarqueeWidget` interfejsu, aby udostępnić dwie metody i właściwości, która manipulowania animacji neon:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  Dodaj nową **kontrolkę niestandardową** elementu do `MarqueeControlLibrary` projektu. Nazwij nowy plik źródłowy podstawowego elementu "MarqueeText."  
  
5.  Przeciągnij <xref:System.ComponentModel.BackgroundWorker> z **przybornika** na Twoje `MarqueeText` kontroli. Umożliwi to składnik `MarqueeText` kontrola samodzielne zaktualizowanie asynchronicznie się.  
  
6.  W oknie właściwości ustaw <xref:System.ComponentModel.BackgroundWorker> składnika `WorkerReportsProgess` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`. Te ustawienia umożliwiają <xref:System.ComponentModel.BackgroundWorker> składnika, aby okresowo podnieść <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń i anulowania asynchronicznych aktualizacji. Aby uzyskać więcej informacji, zobacz [BackgroundWorker, składnik](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
7.  Otwórz `MarqueeText` pliku źródłowego w **Edytor kodu**. W górnej części pliku zaimportuj następujące przestrzenie nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  Zmień deklarację `MarqueeText` odziedziczone <xref:System.Windows.Forms.Label> i wdrożenia `IMarqueeWidget` interfejsu:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. Zadeklaruj zmienne wystąpienia, które odpowiadają narażonych właściwości i ich inicjowania w konstruktorze. `isLit` Pola określa, czy tekst ma być rysowane w kolorze przez `LightColor` właściwości.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. Implementowanie `IMarqueeWidget` interfejsu.  
  
     `StartMarquee` i `StopMarquee` wywołania metody <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody, aby uruchomić i zatrzymać animację.  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atrybuty są stosowane do `UpdatePeriod` właściwość tak, aby pojawił się w sekcji niestandardowe w oknie właściwości o nazwie "Neon."  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. Implementowanie metod dostępu właściwości. Udostępni dwie właściwości dla klientów: `LightColor` i `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atrybuty są stosowane do tych właściwości, więc właściwości są wyświetlane w sekcji niestandardowe w oknie właściwości o nazwie "Neon."  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. Implementowanie obsługi dla <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Programu obsługi zdarzeń zostaje uśpione na liczbę milisekund, określony przez `UpdatePeriod` następnie zgłasza <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia, dopóki kod zatrzymuje animacji, wywołując <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Program obsługi zdarzeń przełącza tekst pomiędzy stanu jasny i ciemny, aby nadać wygląd migające.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metodę umożliwiającą włączenie animacji.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. Naciśnij klawisz F6, aby skompilować rozwiązanie.  
  
## <a name="create-the-marqueeborder-child-control"></a>Tworzenie kontrolki podrzędnej MarqueeBorder  
 `MarqueeBorder` Formant jest nieco bardziej zaawansowane niż `MarqueeText` kontroli. Ma więcej właściwości i animacji w <xref:System.Windows.Forms.Control.OnPaint%2A> metodą jest więcej wysiłku. W zasadzie jest podobna do `MarqueeText` kontroli.  
  
 Ponieważ `MarqueeBorder` formant może mieć formanty podrzędne, musi ona mieć świadomość <xref:System.Windows.Forms.Control.Layout> zdarzenia.  
  
#### <a name="to-create-the-marqueeborder-control"></a>Aby utworzyć formant MarqueeBorder  
  
1.  Dodaj nową **kontrolkę niestandardową** elementu do `MarqueeControlLibrary` projektu. Nazwij nowy plik źródłowy podstawowego elementu "MarqueeBorder."  
  
2.  Przeciągnij <xref:System.ComponentModel.BackgroundWorker> z **przybornika** na Twoje `MarqueeBorder` kontroli. Umożliwi to składnik `MarqueeBorder` kontrola samodzielne zaktualizowanie asynchronicznie się.  
  
3.  W oknie właściwości ustaw <xref:System.ComponentModel.BackgroundWorker> składnika `WorkerReportsProgess` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`. Te ustawienia umożliwiają <xref:System.ComponentModel.BackgroundWorker> składnika, aby okresowo podnieść <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń i anulowania asynchronicznych aktualizacji. Aby uzyskać więcej informacji, zobacz [BackgroundWorker, składnik](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
4.  W oknie dialogowym właściwości kliknij przycisk zdarzenia. Dołącz programy obsługi dla <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia.  
  
5.  Otwórz `MarqueeBorder` pliku źródłowego w **Edytor kodu**. W górnej części pliku zaimportuj następujące przestrzenie nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  Zmień deklarację `MarqueeBorder` odziedziczone <xref:System.Windows.Forms.Panel> i wdrożenia `IMarqueeWidget` interfejsu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  Deklarowanie wyliczeń dwóch zarządzania `MarqueeBorder` stan formantu: `MarqueeSpinDirection`, który określa kierunek, w którym światła "Uruchom" wokół obramowania, i `MarqueeLightShape`, która określa kształt światła (kwadratowy lub cykliczne). Umieszczenie tych deklaracji przed `MarqueeBorder` deklaracji klasy.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  Zadeklaruj zmienne wystąpienia, które odpowiadają narażonych właściwości i ich inicjowania w konstruktorze.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. Implementowanie `IMarqueeWidget` interfejsu.  
  
     `StartMarquee` i `StopMarquee` wywołania metody <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody, aby uruchomić i zatrzymać animację.  
  
     Ponieważ `MarqueeBorder` formant może zawierać formantów podrzędnych `StartMarquee` metoda wylicza wszystkie formanty podrzędne i wywołania `StartMarquee` na te, które implementują `IMarqueeWidget`. `StopMarquee` Metoda ma podobne implementacji.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. Implementowanie metod dostępu właściwości. `MarqueeBorder` Kontrolka ma kilka właściwości do kontrolowania jego wyglądu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. Implementowanie obsługi dla <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Programu obsługi zdarzeń zostaje uśpione na liczbę milisekund, określony przez `UpdatePeriod` następnie zgłasza <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia, dopóki kod zatrzymuje animacji, wywołując <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Programu obsługi zdarzeń zwiększa położenie światła "podstawowe", z którego jest określana stan jasny/ciemny inne kontrolki, i wywołuje <xref:System.Windows.Forms.Control.Refresh%2A> metodę, aby spowodować, że formant do odświeżenia sam.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. Implementuje metody pomocnika `IsLit` i `DrawLight`.  
  
     `IsLit` Metoda określa koloru światła na określonej pozycji. Światła, które są "włączone" są rysowane w kolorze przez `LightColor` właściwości i te, które są "ciemny" są rysowane w kolorze przez `DarkColor` właściwości.  
  
     `DrawLight` Metoda rysuje światło przy użyciu odpowiednich kolor, kształtu i położenia.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. Zastąp <xref:System.Windows.Forms.Control.OnLayout%2A> i <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda rysuje kontrolki wzdłuż krawędzi `MarqueeBorder` kontroli.  
  
     Ponieważ <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zależy od wymiary `MarqueeBorder` kontrolki, należy wywołać go zawsze wtedy, gdy zmienia się układ. Aby to osiągnąć, należy zastąpić <xref:System.Windows.Forms.Control.OnLayout%2A> i wywołać <xref:System.Windows.Forms.Control.Refresh%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>Tworzenie niestandardowego projektanta w tle i właściwości filtru  
 `MarqueeControlRootDesigner` Klasa udostępnia implementację dla projektanta głównego. Oprócz tego projektanta, która działa na `MarqueeControl`, konieczne będzie niestandardowego projektanta, w szczególności skojarzony z `MarqueeBorder` kontroli. Projektant zawiera niestandardowe zachowanie, która jest odpowiednia w kontekście Projektant główny niestandardowych.  
  
 W szczególności `MarqueeBorderDesigner` będzie "w tle" i przefiltruj niektórych właściwości `MarqueeBorder` kontrolki, zmieniając ich interakcje ze środowiskiem projektowania.  
  
 Przechwytuje wywołania metody dostępu właściwości składnika jest nazywany "przesłanianie". Umożliwia projektanta w celu śledzenia wartości ustawione przez użytkownika oraz opcjonalnie przekazać tę wartość do składnika projektowania.  
  
 W tym przykładzie <xref:System.Windows.Forms.Control.Visible%2A> i <xref:System.Windows.Forms.Control.Enabled%2A> właściwości, zostanie pada przez `MarqueeBorderDesigner`, która uniemożliwia użytkownikowi wprowadzanie `MarqueeBorder` kontroli niewidoczne lub wyłączone w czasie projektowania.  
  
 Projektanci można również dodawać i usuwać właściwości. W tym przykładzie <xref:System.Windows.Forms.Control.Padding%2A> właściwości zostaną usunięte w czasie projektowania, ponieważ `MarqueeBorder` kontroli programowo ustawia wypełnienie na podstawie rozmiaru kontrolki określonej przez `LightSize` właściwości.  
  
 Klasa bazowa dla `MarqueeBorderDesigner` jest <xref:System.ComponentModel.Design.ComponentDesigner>, która zawiera metody, które można zmienić atrybutów, właściwości i zdarzenia udostępnianych przez formantu w czasie projektowania:  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 Podczas zmiany publicznego interfejsu składnika za pomocą tych metod, należy wykonać następujące czynności:  
  
-   Dodawanie lub usuwanie elementów w `PreFilter` tylko metody  
  
-   Modyfikowanie istniejących elementów w `PostFilter` tylko metody  
  
-   Zawsze najpierw wywoływać implementację podstawową `PreFilter` metody  
  
-   Zawsze wywoływać implementację podstawową ostatnia `PostFilter` metody  
  
 Przestrzeganiu tych zasad zapewnia wszystkich projektantów w środowisku projektowania spójny widok wszystkich składników projektowania.  
  
 <xref:System.ComponentModel.Design.ComponentDesigner> Klasy zawiera słownik zarządzania wartości właściwości zasłonięte, zwalniające potrzebę tworzenia zmiennych do konkretnego wystąpienia.  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Aby utworzyć niestandardowe projektanta w tle i filtr właściwości  
  
1.  Kliknij prawym przyciskiem myszy **projektowania** folderze i Dodaj nową klasę. Nadaj plikowi źródła podstawowej nazwy "MarqueeBorderDesigner."  
  
2.  Otwórz `MarqueeBorderDesigner` pliku źródłowego w **Edytor kodu**. W górnej części pliku zaimportuj następujące przestrzenie nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  Zmień deklarację `MarqueeBorderDesigner` odziedziczone <xref:System.Windows.Forms.Design.ParentControlDesigner>.  
  
     Ponieważ `MarqueeBorder` formant może zawierać formantów podrzędnych `MarqueeBorderDesigner` dziedziczy <xref:System.Windows.Forms.Design.ParentControlDesigner>, która obsługuje interakcje nadrzędny podrzędny.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  Przesłoń implementację podstawową <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  Implementowanie <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A> właściwości. Tych implementacji w tle właściwości formantu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a>Obsługa zmiany składnika  
 `MarqueeControlRootDesigner` Klasa udostępnia niestandardowe środowiska czasu projektowania dla Twojego `MarqueeControl` wystąpień. Większość funkcji czasu projektowania jest dziedziczony z <xref:System.Windows.Forms.Design.DocumentDesigner> klasy; usługi będzie kodu, wdrożenie dwóch określonych dostosowań: Obsługa zmiany składnika i dodanie zlecenia projektanta.  
  
 Jako projekt użytkownikom ich `MarqueeControl` przypadkach projektanta głównego będzie śledzić zmian `MarqueeControl` i jego formantów podrzędnych. Środowisko czasu projektowania oferuje wygodny usługi <xref:System.ComponentModel.Design.IComponentChangeService>, śledzić zmiany stanu składnika.  
  
 Możesz uzyskać odwołanie do tej usługi, badając środowisko o <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody. Jeśli zapytanie zakończy się pomyślnie, projektanta, można dołączyć program obsługi <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> zdarzenia i wykonywać dowolne zadania są zobowiązane do zachowania spójnego stanu w czasie projektowania.  
  
 W przypadku właściwości `MarqueeControlRootDesigner` klasy będzie wywoływać <xref:System.Windows.Forms.Control.Refresh%2A> metody na każdym `IMarqueeWidget` obiektów znajdujących się `MarqueeControl`. Spowoduje to `IMarqueeWidget` obiektów do odświeżenia sam odpowiednio, gdy właściwości, takie jak jego element nadrzędny <xref:System.Windows.Forms.Control.Size%2A> są zmieniane.  
  
#### <a name="to-handle-component-changes"></a>Aby obsługiwać zmiany składnika  
  
1.  Otwórz `MarqueeControlRootDesigner` pliku źródłowego w **Edytor kodu** i zastąpić <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody. Wywoływać implementację podstawową <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> i można wyszukiwać <xref:System.ComponentModel.Design.IComponentChangeService>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  Implementowanie <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> programu obsługi zdarzeń. Typ składnika wysyłania testu oraz czy jest `IMarqueeWidget`, wywołać jej <xref:System.Windows.Forms.Control.Refresh%2A> metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a>Dodanie zlecenia projektanta do niestandardowego projektanta  
 Zlecenia projektanta jest polecenia menu, połączyć programu obsługi zdarzeń. Zlecenia projektanta są dodawane do menu skrótów składnika w czasie projektowania. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Design.DesignerVerb>.  
  
 Zlecenia projektanta dwóch zostanie dodany do Twojego projektantów: **Uruchom Test** i **zatrzymania testu**. Tych poleceń pozwala wyświetlić zachowanie środowiska wykonawczego `MarqueeControl` w czasie projektowania. Tych poleceń, które zostaną dodane do `MarqueeControlRootDesigner`.  
  
 Gdy **Uruchom Test** jest wywołana, program obsługi zdarzeń zlecenie, wywoła `StartMarquee` metody `MarqueeControl`. Gdy **Zatrzymaj Test** jest wywołana, program obsługi zdarzeń zlecenie, wywoła `StopMarquee` metody `MarqueeControl`. Implementacja `StartMarquee` i `StopMarquee` metody wywołania tych metod w zawartych w nim formantów, które implementują `IMarqueeWidget`, więc wszystkie zawarty `IMarqueeWidget` kontrolek również będą uczestniczyć w teście.  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Aby dodać zlecenia projektanta do Twojej niestandardowi projektanci  
  
1.  W `MarqueeControlRootDesigner` klasy, należy dodać procedury obsługi zdarzeń o nazwie `OnVerbRunTest` i `OnVerbStopTest`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  Połącz te programy obsługi zdarzeń do ich odpowiednich zleceń projektanta. `MarqueeControlRootDesigner` dziedziczy <xref:System.ComponentModel.Design.DesignerVerbCollection> od swojej klasy bazowej. Utworzysz dwie nowe <xref:System.ComponentModel.Design.DesignerVerb> obiektów i dodać je do tej kolekcji w <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a>Tworzenie niestandardowych UITypeEditor  
 Podczas tworzenia niestandardowego środowiska czasu projektowania dla użytkowników często jest pożądane tworzenie niestandardowych interakcji w oknie właściwości. Można to zrobić, tworząc <xref:System.Drawing.Design.UITypeEditor>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie edytora typów Interfejsu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).  
  
 `MarqueeBorder` Kontroli udostępnia kilka właściwości w oknie dialogowym właściwości. Dwa z tych właściwości `MarqueeSpinDirection` i `MarqueeLightShape` są reprezentowane przez wyliczenia. Aby zilustrować korzystanie z edytora typów Interfejsu `MarqueeLightShape` właściwość będzie miał skojarzoną <xref:System.Drawing.Design.UITypeEditor> klasy.  
  
#### <a name="to-create-a-custom-ui-type-editor"></a>Aby utworzyć niestandardowy typ interfejsu użytkownika w edytorze  
  
1.  Otwórz `MarqueeBorder` pliku źródłowego w **Edytor kodu**.  
  
2.  W definicji `MarqueeBorder` klasy, Zadeklaruj klasę o nazwie `LightShapeEditor` który pochodzi od klasy <xref:System.Drawing.Design.UITypeEditor>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  Zadeklaruj <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> wystąpienie zmiennej o nazwie `editorService`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  Zastąp <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody. Ta implementacja zwraca <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, która informuje środowisko projektowania sposób wyświetlania `LightShapeEditor`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  Zastąp <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody. Ta implementacja wykonuje kwerendę w środowisku projektowania dla <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> obiektu. Jeśli operacja się powiedzie, tworzy `LightShapeSelectionControl`. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Metoda jest wywoływana, aby rozpocząć `LightShapeEditor`. Wartość zwrócona przez to wywołanie jest zwracana do środowiska projektowania.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>Tworzenie formantu widoku dla Twojego niestandardowego UITypeEditor  
  
1.  `MarqueeLightShape` Właściwość obsługuje dwa rodzaje kształtów światła: `Square` i `Circle`. Utworzysz formant niestandardowy, używane wyłącznie na potrzeby graficznie wyświetlania tych wartości w oknie dialogowym właściwości. Tej kontrolki niestandardowej, które będą używane przez usługi <xref:System.Drawing.Design.UITypeEditor> do interakcji z okna właściwości.  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Aby utworzyć formant widoku dla niestandardowego interfejsu użytkownika edytora typów  
  
1.  Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do `MarqueeControlLibrary` projektu. Nazwij nowy plik źródłowy podstawowego elementu "LightShapeSelectionControl."  
  
2.  Przeciągnij dwa <xref:System.Windows.Forms.Panel> kontrolki z **przybornika** na `LightShapeSelectionControl`. Nazwij je `squarePanel` i `circlePanel`. Rozmieść je obok siebie. Ustaw <xref:System.Windows.Forms.Control.Size%2A> właściwość obu <xref:System.Windows.Forms.Panel> mające na celu (60, 60). Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwość `squarePanel` kontrolę (8, 10). Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwość `circlePanel` kontrolę (80, 10). Wreszcie, ustaw <xref:System.Windows.Forms.Control.Size%2A> właściwość `LightShapeSelectionControl` do (150, 80).  
  
3.  Otwórz `LightShapeSelectionControl` pliku źródłowego w **Edytor kodu**. W górnej części pliku, należy zaimportować <xref:System.Windows.Forms.Design?displayProperty=nameWithType> przestrzeni nazw:  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  Implementowanie <xref:System.Windows.Forms.Control.Click> programy obsługi zdarzeń dla `squarePanel` i `circlePanel` kontrolki. Wywoływanie tych metod <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> do końca niestandardowej <xref:System.Drawing.Design.UITypeEditor> edytowanie sesję.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  Zadeklaruj <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> wystąpienie zmiennej o nazwie `editorService`.  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  Zadeklaruj `MarqueeLightShape` wystąpienie zmiennej o nazwie `lightShapeValue`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  W `LightShapeSelectionControl` konstruktora, dołącz <xref:System.Windows.Forms.Control.Click> programów obsługi zdarzeń do `squarePanel` i `circlePanel` kontrolek <xref:System.Windows.Forms.Control.Click> zdarzenia. Ponadto zdefiniować przeciążenia konstruktora, który przypisuje `MarqueeLightShape` wartość ze środowiska projektowania do `lightShapeValue` pola.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  W <xref:System.ComponentModel.Component.Dispose%2A> metody detach <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku. Otwórz plik LightShapeSelectionControl.Designer.cs lub LightShapeSelectionControl.Designer.vb i usuń definicję domyślną <xref:System.ComponentModel.Component.Dispose%2A> metody.  
  
5.  Implementowanie `LightShape` właściwości.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Ta implementacja będzie Rysuj wypełniony kwadrat i okrąg. Będą również wyróżniać wybranej wartości za pomocą rysowania obramowanie jeden kształt lub innych.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a>Testowanie niestandardowego formantu w Projektancie  
 W tym momencie możesz tworzyć `MarqueeControlLibrary` projektu. Testowania implementacji, tworząc formant, który dziedziczy z `MarqueeControl` klasy i korzystania z niego w formularzu.  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Aby utworzyć niestandardową implementację MarqueeControl  
  
1.  Otwórz `DemoMarqueeControl` w programie Windows Forms Designer. Spowoduje to utworzenie wystąpienia `DemoMarqueeControl` wpisz i wyświetla go w wystąpieniu `MarqueeControlRootDesigner` typu.  
  
2.  W **przybornika**, otwórz **składniki MarqueeControlLibrary** kartę. Zostanie wyświetlony `MarqueeBorder` i `MarqueeText` kontrolek dostępnych do wyboru.  
  
3.  Przeciągnij wystąpienie `MarqueeBorder` kontrolować na `DemoMarqueeControl` powierzchni projektowej. Dokowanie to `MarqueeBorder` kontrolki do kontrolki nadrzędnej.  
  
4.  Przeciągnij wystąpienie `MarqueeText` kontrolować na `DemoMarqueeControl` powierzchni projektowej.  
  
5.  Skompiluj rozwiązanie.  
  
6.  Kliknij prawym przyciskiem myszy `DemoMarqueeControl` i z menu skrótów wybierz opcję **Uruchom Test** opcji uruchamiania animacji. Kliknij przycisk **Zatrzymaj Test** Aby zatrzymać animację.  
  
7.  Otwórz **Form1** w widoku Projekt.  
  
8.  Umieść dwa <xref:System.Windows.Forms.Button> kontrolek w formularzu. Nazwij je `startButton` i `stopButton`i zmień <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości do **Start** i **zatrzymać**odpowiednio.  
  
9. Implementowanie <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń dla obu <xref:System.Windows.Forms.Button> kontrolki.  
  
10. W **przybornika**, otwórz **składniki MarqueeControlTest** kartę. Zostanie wyświetlony `DemoMarqueeControl` dostępne do wyboru.  
  
11. Przeciągnij wystąpienie `DemoMarqueeControl` na **Form1** powierzchni projektowej.  
  
12. W <xref:System.Windows.Forms.Control.Click> wywoływanie programów obsługi zdarzeń, `Start` i `Stop` metod `DemoMarqueeControl`.  
  
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
  
1.  Ustaw `MarqueeControlTest` projekt jako projekt startowy i uruchomimy ją. Zostanie wyświetlony formularz, wyświetlając Twoje `DemoMarqueeControl`. Kliknij przycisk **Start** przycisku do uruchamiania animacji. Powinien zostać wyświetlony tekst miga i świateł poruszanie się w granicy.  
  
## <a name="next-steps"></a>Następne kroki  
 `MarqueeControlLibrary` Przedstawia proste wdrażanie niestandardowych formantów i projektanci skojarzone. Można wprowadzić w tym przykładzie bardziej zaawansowanych na kilka sposobów:  
  
-   Zmiana wartości właściwości `DemoMarqueeControl` w projektancie. Dodaj więcej `MarqueBorder` kontroluje i dokowanie je w ramach wystąpienia ich nadrzędnego w taki sposób, aby utworzyć efekt zagnieżdżonych. Doświadczenia z różnymi ustawieniami dla `UpdatePeriod` i właściwości oświetlenia.  
  
-   Tworzenie własnych implementacji `IMarqueeWidget`. Można na przykład utworzyć migające "neon znaku" lub animowany logowania przy użyciu wielu obrazów.  
  
-   Dodatkowo dostosować środowisko czasu projektowania. Możesz spróbować przesłanianie więcej właściwości, niż <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A>, i dodać nowe właściwości. Dodaj nowe zlecenia projektanta, aby uprościć typowych zadań, takich jak dokowanie formantów podrzędnych.  
  
-   Licencja `MarqueeControl`. Aby uzyskać więcej informacji, zobacz [jak: Licencjonowanie składników i kontrolek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).  
  
-   Kontrolować, jak kontrolki są serializowane i jak kod jest generowany dla nich. Aby uzyskać więcej informacji, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb> 
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- [Instrukcje: Tworzenie formantu formularzy Windows wykorzystującego funkcje czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
- [Rozszerzenie obsługi w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)) 
- [Niestandardowi projektanci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))
