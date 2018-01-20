---
title: "Wskazówki: tworzenie kontrolki formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
caps.latest.revision: "46"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4e84c665897159d08cec36b0f35b4f5f2674445
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>Wskazówki: tworzenie kontrolki formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio
Środowisko czasu projektowania dla kontrolek niestandardowych można zwiększyć przez tworzenia skojarzone projektanta niestandardowych.  
  
 W tym przewodniku ilustruje sposób tworzenia niestandardowych projektanta dla kontrolek niestandardowych. Zostaną zaimplementowane `MarqueeControl` typu i skojarzone projektowania klasy o nazwie `MarqueeControlRootDesigner`.  
  
 `MarqueeControl` Typ implementuje ekran podobny do ramkę kina animowany świateł i miga tekstem.  
  
 Projektanta dla tego formantu wchodzi w interakcję w środowisku projektowania, aby zapewnić środowisko czasu projektowania niestandardowego. Przy użyciu projektanta niestandardowych, można utworzyć niestandardowy `MarqueeControl` implementację animowany świateł i miga tekst w wielu kombinacji. Można użyć złożony kontrolkę w formularzu podobnie jak inne kontrolki formularza systemu Windows.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu  
  
-   Tworzenie projektu biblioteki formantu  
  
-   Odwołanie do projektu formantu niestandardowego  
  
-   Definiowanie kontrolkę niestandardową oraz jego niestandardowe Designer  
  
-   Utworzenie wystąpienia formantu niestandardowego  
  
-   Konfigurowanie projektu debugowanie w czasie projektowania  
  
-   Implementowanie formantu niestandardowego  
  
-   Tworzenie formantu podrzędnego dla formantu niestandardowego  
  
-   Utwórz formant podrzędny MarqueeBorder  
  
-   Tworzenie niestandardowych projektanta Cień i właściwości filtru  
  
-   Obsługa zmiany składnika  
  
-   Dodawanie poleceń projektanta do sieci niestandardowej projektanta  
  
-   Tworzenie niestandardowego elementu UITypeEditor.  
  
-   Testowanie formantu niestandardowego w Projektancie  
  
 Po ukończeniu formantu niestandardowego będą wyglądać następująco:  
  
 ![Możliwe formantu MarqueeControl](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 Lista kompletny kod znajduje się [porady: Tworzenie funkcji systemu Windows formularze kontroli czy ma korzystać z czasu projektowania](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Wystarczających uprawnień, aby mieć możliwość tworzenia i uruchamiania projektów aplikacji formularzy systemu Windows na komputerze, którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu aplikacji. Użyjesz tego projektu do tworzenia aplikacji, która obsługuje kontrolki niestandardowej.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz projekt aplikacji formularzy systemu Windows o nazwie "MarqueeControlTest." Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
## <a name="creating-a-control-library-project"></a>Tworzenie projektu biblioteki formantu  
 Następnym krokiem jest do tworzenia projektu biblioteki formantu. Spowoduje utworzenie nowej kontrolki niestandardowej i jego odpowiedniego projektanta niestandardowych.  
  
#### <a name="to-create-the-control-library-project"></a>Aby utworzyć projekt z kontroli biblioteki  
  
1.  Dodaj projekt Biblioteka formantów formularzy systemu Windows do rozwiązania. Nazwa projektu "MarqueeControlLibrary."  
  
2.  Przy użyciu **Eksploratora rozwiązań**, usuń formant domyślnego projektu przez usunięcie pliku źródłowego o nazwie "UserControl1.cs" lub "UserControl1.vb", w zależności od języka wybór. Aby uzyskać więcej informacji, zobacz [NIB: porady: usuwanie, usuwania i wykluczanie elementów](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do `MarqueeControlLibrary` projektu. Nadaj nowej plik źródłowy podstawowej nazwy "MarqueeControl."  
  
4.  Przy użyciu **Eksploratora rozwiązań**, Utwórz nowy folder w `MarqueeControlLibrary` projektu. Aby uzyskać więcej informacji, zobacz [NIB: porady: dodawanie nowych elementów projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Nazwa nowego folderu "Projekt".  
  
5.  Kliknij prawym przyciskiem myszy **projekt** folderu i Dodaj nową klasę. Nadaj pliku źródłowego z podstawowej nazwy "MarqueeControlRootDesigner."  
  
6.  Musisz użyć typów z zestawu System.Design, aby dodać to odwołanie do `MarqueeControlLibrary` projektu.  
  
    > [!NOTE]
    >  Aby użyć zestawu System.Design, projekt musi wskazywać na pełną wersję programu .NET Framework nie programu .NET Framework Client Profile. Aby zmienić platformę docelową, zobacz [porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).  
  
## <a name="referencing-the-custom-control-project"></a>Odwołanie do projektu formantu niestandardowego  
 Użyjesz `MarqueeControlTest` projektu do testowania kontrolki niestandardowej. Projekt testowy będzie znane kontrolki niestandardowej podczas Dodaj odwołanie projektu do `MarqueeControlLibrary` zestawu.  
  
#### <a name="to-reference-the-custom-control-project"></a>Odwołania do projektu formantu niestandardowego  
  
-   W `MarqueeControlTest` projekt, Dodaj odwołanie projektu do `MarqueeControlLibrary` zestawu. Należy użyć **projekty** karcie **Dodaj odwołanie** okno dialogowe zamiast odwołania do `MarqueeControlLibrary` zestawu bezpośrednio.  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a>Definiowanie kontrolkę niestandardową oraz jego niestandardowe Designer  
 Niestandardowe formantu będzie dziedziczyć <xref:System.Windows.Forms.UserControl> klasy. Dzięki temu formantu do zawierają inne formanty i zapewnia dużą domyślna funkcjonalność formantu.  
  
 Niestandardowe formantu ma skojarzone projektanta niestandardowych. Dzięki temu można utworzyć środowisko unikatowego projektu dostosowane specjalnie dla formantu niestandardowego.  
  
 Formant należy powiązać z jego projektanta przy użyciu <xref:System.ComponentModel.DesignerAttribute> klasy. Ponieważ tworzysz całego zachowania czasu projektowania formantu niestandardowego wdroży niestandardowych projektanta <xref:System.ComponentModel.Design.IRootDesigner> interfejsu.  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Aby zdefiniować kontrolkę niestandardową oraz jego niestandardowe designer  
  
1.  Otwórz `MarqueeControl` pliku źródłowego w **edytora kodu**. W górnej części pliku należy zaimportować następujących przestrzeni nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  Dodaj <xref:System.ComponentModel.DesignerAttribute> do `MarqueeControl` deklaracji klasy. Za pomocą projektanta jego skojarzenie kontrolki niestandardowej.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  Otwórz `MarqueeControlRootDesigner` pliku źródłowego w **edytora kodu**. W górnej części pliku należy zaimportować następujących przestrzeni nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  Zmień deklarację elementu `MarqueeControlRootDesigner` odziedziczone <xref:System.Windows.Forms.Design.DocumentDesigner> klasy. Zastosuj <xref:System.ComponentModel.ToolboxItemFilterAttribute> do określenia projektanta interakcji z **przybornika**.  
  
     **Uwaga** definicji `MarqueeControlRootDesigner` klasa ma został ujęty w przestrzeni nazw o nazwie "MarqueeControlLibrary.Design." Tej deklaracji umieszcza projektanta w specjalny obszar nazw zarezerwowanych dla typów związanych z projektu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  Zdefiniuj Konstruktor `MarqueeControlRootDesigner` klasy. Wstaw <xref:System.Diagnostics.Trace.WriteLine%2A> instrukcji w treści konstruktora. Spowoduje to być przydatne na potrzeby debugowania.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a>Utworzenie wystąpienia formantu niestandardowego  
 Aby przyjrzeć się zachowaniu czasu projektowania niestandardowego formantu, zostaną umieszczone wystąpienie formantu formularza w `MarqueeControlTest` projektu.  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a>Można utworzyć wystąpienia formantu niestandardowego  
  
1.  Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do `MarqueeControlTest` projektu. Nadaj nowej plik źródłowy podstawowej nazwy "DemoMarqueeControl."  
  
2.  Otwórz `DemoMarqueeControl` w pliku **edytora kodu**. W górnej części pliku, należy zaimportować `MarqueeControlLibrary` przestrzeni nazw:  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  Zmień deklarację elementu `DemoMarqueeControl` odziedziczone `MarqueeControl` klasy.  
  
2.  Skompiluj projekt.  
  
3.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
4.  Znajdź **składniki MarqueeControlTest** karcie **przybornika** i otwórz go. Przeciągnij `DemoMarqueeControl` z **przybornika** na formularzu.  
  
5.  Skompiluj projekt.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Konfigurowanie projektu debugowanie w czasie projektowania  
 Podczas tworzenia niestandardowego środowiska czasu projektowania, będzie konieczne do debugowania z formanty i składniki. Brak prosty sposób konfigurowania projektu w celu zezwolenia na debugowanie w czasie projektowania. Aby uzyskać więcej informacji, zobacz [wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Aby skonfigurować projekt dla debugowanie w czasie projektowania  
  
1.  Kliknij prawym przyciskiem myszy `MarqueeControlLibrary` projekt i wybierz **właściwości**.  
  
2.  W oknie dialogowym "MarqueeControlLibrary strony właściwości" Wybierz **debugowania** strony.  
  
3.  W **Akcja uruchamiania** zaznacz **Start programu zewnętrznego**. Można więc debugowanie osobnego wystąpienia programu Visual Studio, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby wyszukać środowiska IDE programu Visual Studio. Nazwa pliku wykonywalnego jest devenv.exe, a jeśli został zainstalowany w domyślnej lokalizacji ścieżki %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.  
  
4.  Kliknij przycisk OK, aby zamknąć okno dialogowe.  
  
5.  Kliknij prawym przyciskiem myszy `MarqueeControlLibrary` projekt i wybierz "Ustaw jako projekt startowy" Aby umożliwić tej konfiguracji debugowania.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 Teraz można przystąpić do debugowania zachowania czasu projektowania formantu niestandardowego. Po określeniu, czy środowisko debugowania jest prawidłowo skonfigurowane, przetestowaniu skojarzenie między formantu niestandardowego i niestandardowych projektanta.  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Aby przetestować debugowania środowiska i skojarzenia projektanta  
  
1.  Otwórz `MarqueeControlRootDesigner` pliku źródłowego w **edytora kodu** i umieść punkt przerwania na <xref:System.Diagnostics.Trace.WriteLine%2A> instrukcji.  
  
2.  Naciśnij klawisz F5, aby rozpocząć sesję debugowania. Należy pamiętać, że utworzono nowe wystąpienie programu Visual Studio.  
  
3.  W tym nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie "MarqueeControlTest". Można łatwo znaleźć rozwiązania, wybierając **ostatnich projektów** z **pliku** menu. Plik rozwiązania "MarqueeControlTest.sln" zostaną wyświetlone jako ostatnio używanych plików.  
  
4.  Otwórz `DemoMarqueeControl` w projektancie. Zauważ, że wystąpienie debugowania programu Visual Studio uzyskuje fokus i wykonywania zatrzymuje się na punkt przerwania. Naciśnij klawisz F5, aby kontynuować sesję debugowania.  
  
 W tym momencie jest wszystko, co umożliwia tworzenie i debugowanie formantu niestandardowego i jego skojarzony projektanta niestandardowych. W pozostałej części tego przewodnika będą skoncentrowane na szczegóły implementacji funkcji kontroli i projektanta.  
  
## <a name="implementing-your-custom-control"></a>Implementowanie formantu niestandardowego  
 `MarqueeControl` Jest <xref:System.Windows.Forms.UserControl> z niewielki dostosowania. Udostępnia ona dwóch metod: `Start`, co spowoduje włączenie animacji neonu i `Stop`, co uniemożliwia animacji. Ponieważ `MarqueeControl` zawiera formanty podrzędne, które implementują `IMarqueeWidget` interfejsu `Start` i `Stop` wyliczyć każdego formantu podrzędnego i wywołanie `StartMarquee` i `StopMarquee` metod, odpowiednio na każdej kontrolki podrzędnej implementującej `IMarqueeWidget`.  
  
 Wygląd `MarqueeBorder` i `MarqueeText` formantów jest zależna od układu, tak `MarqueeControl` zastępuje <xref:System.Windows.Forms.Control.OnLayout%2A> — metoda i wywołania <xref:System.Windows.Forms.Control.PerformLayout%2A> na formantów podrzędnych tego typu.  
  
 Jest to zakres `MarqueeControl` dostosowań. Funkcje środowiska wykonawczego są implementowane przez `MarqueeBorder` i `MarqueeText` kontrolek i funkcje czasu projektowania są implementowane przez `MarqueeBorderDesigner` i `MarqueeControlRootDesigner` klasy.  
  
#### <a name="to-implement-your-custom-control"></a>Aby zaimplementować formantu niestandardowego  
  
1.  Otwórz `MarqueeControl` pliku źródłowego w **edytora kodu**. Implementowanie `Start` i `Stop` metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  Zastąpienie <xref:System.Windows.Forms.Control.OnLayout%2A> metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a>Tworzenie formantu podrzędnego dla formantu niestandardowego  
 `MarqueeControl` Będzie obsługiwać dwa rodzaje formant podrzędny: `MarqueeBorder` kontroli i `MarqueeText` formantu.  
  
-   `MarqueeBorder`: Ten formant umożliwia malowanie "świateł" wokół jego krawędzi obramowania. Kontrolki flash w sekwencji, więc pojawią się one być przenoszenia obramowania. Szybkość, jaką flash kontrolki jest kontrolowany przez właściwość o nazwie `UpdatePeriod`. Kilka właściwości niestandardowe określają innych aspektów wygląd formantu. Dwie metody o nazwie `StartMarquee` i `StopMarquee`, kontrolować podczas uruchamiania i zatrzymywania w animacji.  
  
-   `MarqueeText`: Ten formant umożliwia malowanie miga ciągu. Podobnie jak `MarqueeBorder` szybkości, jaką miga tekst formantu jest kontrolowany przez `UpdatePeriod` właściwości. `MarqueeText` Formantu ma również `StartMarquee` i `StopMarquee` metody wspólnego z `MarqueeBorder` formantu.  
  
 W czasie projektowania `MarqueeControlRootDesigner` umożliwia tych typów kontroli dwóch mają zostać dodane do `MarqueeControl` w dowolnej kombinacji.  
  
 Wspólne funkcje dwóch formantów są rozkładane na interfejs o nazwie `IMarqueeWidget`. Dzięki temu `MarqueeControl` do odnalezienia formanty powiązane ustawiony na Marquee podrzędne i nadaj im szczególnego traktowania.  
  
 Aby wdrożyć funkcję okresowe animacji, użyje <xref:System.ComponentModel.BackgroundWorker> obiektów z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw. Można użyć <xref:System.Windows.Forms.Timer> obiektów, ale wiele `IMarqueeWidget` obiektów, pojedynczego wątku interfejsu użytkownika może być niemożliwe ze animacji.  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a>Aby utworzyć formant podrzędny dla formantu niestandardowego  
  
1.  Dodaj nowy element klasy do `MarqueeControlLibrary` projektu. Nadaj nowej plik źródłowy podstawowej nazwy "IMarqueeWidget."  
  
2.  Otwórz `IMarqueeWidget` pliku źródłowego w **edytora kodu** i zmień deklarację z `class` do `interface`:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  Dodaj następujący kod do `IMarqueeWidget` interfejs do udostępnienia dwie metody i właściwości, która manipulowania animacji neonu:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  Dodaj nową **formant niestandardowy** elementu do `MarqueeControlLibrary` projektu. Nadaj nowej plik źródłowy podstawowej nazwy "MarqueeText."  
  
5.  Przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika z **przybornika** na Twojej `MarqueeText` formantu. Ten składnik umożliwi `MarqueeText` kontroli sam aktualizację asynchronicznie.  
  
6.  W oknie właściwości ustaw <xref:System.ComponentModel.BackgroundWorker> składnika `WorkerReportsProgess` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`. Te ustawienia umożliwiają <xref:System.ComponentModel.BackgroundWorker> składnika okresowo podnieść <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń i anulować aktualizacje asynchroniczne. Aby uzyskać więcej informacji, zobacz [składnikiem BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
7.  Otwórz `MarqueeText` pliku źródłowego w **edytora kodu**. W górnej części pliku należy zaimportować następujących przestrzeni nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  Zmień deklarację elementu `MarqueeText` odziedziczone <xref:System.Windows.Forms.Label> i wdrożenie `IMarqueeWidget` interfejsu:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. Zadeklaruj zmienne wystąpienia, które odpowiadają ujawnionych właściwości i ich inicjowania w konstruktorze. `isLit` Pole określa, czy tekst ma zostać narysowany określany przez kolor `LightColor` właściwości.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. Implementowanie `IMarqueeWidget` interfejsu.  
  
     `StartMarquee` i `StopMarquee` wywołania metody <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody służące do uruchamiania i zatrzymywania animacji.  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atrybuty są stosowane do `UpdatePeriod` właściwości, aby był w niestandardowych części okna właściwości o nazwie "Ustawiony na Marquee."  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. Implementuje metody dostępu właściwości. Uwidoczni dwóch właściwości do klientów: `LightColor` i `DarkColor`. <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> atrybuty są stosowane do tych właściwości, więc właściwości znajdują się w sekcji niestandardowe okna właściwości o nazwie "Ustawiony na Marquee."  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. Programy obsługi wdrożenia <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Program obsługi zdarzeń zostanie uśpiony na liczbę milisekund określoną przez `UpdatePeriod` następnie wywołuje <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń, dopóki kod zatrzymuje animacji przez wywołanie metody <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Tekst między stanu jasnym i ciemnym umożliwiają wygląd miga przełącza obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. Zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metodę umożliwiającą włączenie animacji.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. Naciśnij klawisz F6 w celu skompilowania rozwiązania.  
  
## <a name="create-the-marqueeborder-child-control"></a>Utwórz formant podrzędny MarqueeBorder  
 `MarqueeBorder` Formant jest nieco bardziej złożone niż `MarqueeText` formantu. Zawiera więcej właściwości i animacji w <xref:System.Windows.Forms.Control.OnPaint%2A> metoda jest więcej wysiłku. Zasadniczo jest podobna do `MarqueeText` formantu.  
  
 Ponieważ `MarqueeBorder` formant może mieć formantów podrzędnych, należy mieć świadomość <xref:System.Windows.Forms.Control.Layout> zdarzenia.  
  
#### <a name="to-create-the-marqueeborder-control"></a>Można utworzyć formantu MarqueeBorder  
  
1.  Dodaj nową **formant niestandardowy** elementu do `MarqueeControlLibrary` projektu. Nadaj nowej plik źródłowy podstawowej nazwy "MarqueeBorder."  
  
2.  Przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika z **przybornika** na Twojej `MarqueeBorder` formantu. Ten składnik umożliwi `MarqueeBorder` kontroli sam aktualizację asynchronicznie.  
  
3.  W oknie właściwości ustaw <xref:System.ComponentModel.BackgroundWorker> składnika `WorkerReportsProgess` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`. Te ustawienia umożliwiają <xref:System.ComponentModel.BackgroundWorker> składnika okresowo podnieść <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń i anulować aktualizacje asynchroniczne. Aby uzyskać więcej informacji, zobacz [składnikiem BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md).  
  
4.  W oknie właściwości kliknij przycisk zdarzenia. Dołącz obsługi <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia.  
  
5.  Otwórz `MarqueeBorder` pliku źródłowego w **edytora kodu**. W górnej części pliku należy zaimportować następujących przestrzeni nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  Zmień deklarację elementu `MarqueeBorder` odziedziczone <xref:System.Windows.Forms.Panel> i wdrożenie `IMarqueeWidget` interfejsu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  Deklarowanie wyliczeń dwóch zarządzania `MarqueeBorder` stan formantu: `MarqueeSpinDirection`, która określa kierunek, w którym kontrolki "pokrętła" wokół granicy, i `MarqueeLightShape`, która określa kształt świateł (kwadratowe lub cykliczne). Umieść deklaracji przed `MarqueeBorder` deklaracji klasy.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  Zadeklaruj zmienne wystąpienia, które odpowiadają ujawnionych właściwości i ich inicjowania w konstruktorze.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. Implementowanie `IMarqueeWidget` interfejsu.  
  
     `StartMarquee` i `StopMarquee` wywołania metody <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody służące do uruchamiania i zatrzymywania animacji.  
  
     Ponieważ `MarqueeBorder` formant może zawierać formantów podrzędnych `StartMarquee` metoda wylicza wszystkie formanty podrzędne i wywołania `StartMarquee` tych, które implementują `IMarqueeWidget`. `StopMarquee` Metoda ma podobne implementacji.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. Implementuje metody dostępu właściwości. `MarqueeBorder` Formant ma kilka właściwości sterujące jego wyglądu.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. Programy obsługi wdrożenia <xref:System.ComponentModel.BackgroundWorker> składnika <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia.  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> Program obsługi zdarzeń zostanie uśpiony na liczbę milisekund określoną przez `UpdatePeriod` następnie wywołuje <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń, dopóki kod zatrzymuje animacji przez wywołanie metody <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Obsługi zdarzeń zwiększa położenie jasny "podstawowy", z którego stan jasny/ciemny inne kontrolki jest określana, i wywołania <xref:System.Windows.Forms.Control.Refresh%2A> metodę, aby spowodować, że formant do samej siebie odświeżenia.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. Implementuje metody pomocnicze `IsLit` i `DrawLight`.  
  
     `IsLit` Metoda określa kolor oświetlenia na określonej pozycji. Świateł, które są "włączone" są rysowane w kolorze przez `LightColor` właściwości oraz te, które są "ciemny" są rysowane w kolorze przez `DarkColor` właściwości.  
  
     `DrawLight` Metody rysuje światło przy użyciu odpowiednich kolorów, kształt i pozycji.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. Zastąpienie <xref:System.Windows.Forms.Control.OnLayout%2A> i <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> Metody rysuje świateł wzdłuż krawędzi `MarqueeBorder` formantu.  
  
     Ponieważ <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zależy od wymiary `MarqueeBorder` formantu, należy wywołać ją przy każdej zmianie układu. Aby to osiągnąć, należy zastąpić <xref:System.Windows.Forms.Control.OnLayout%2A> i Wywołaj <xref:System.Windows.Forms.Control.Refresh%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>Tworzenie niestandardowych projektanta Cień i właściwości filtru  
 `MarqueeControlRootDesigner` Klasa udostępnia implementację dla projektanta głównego. Oprócz tego projektanta, który działa na `MarqueeControl`, konieczne będzie niestandardowych projektanta, który jest szczegółowo skojarzony z `MarqueeBorder` formantu. Ten Projektant zawiera niestandardowe zachowania, które jest odpowiednie w kontekście projektanta głównego niestandardowych.  
  
 W szczególności `MarqueeBorderDesigner` "w tle", a niektóre właściwości filtru na `MarqueeBorder` kontroli, zmiana ich interakcji z środowisku projektowania.  
  
 Przechwytywaniu wywołania metody dostępu właściwości składnika nazywa się "cienia". Umożliwia projektanta do śledzenia wartości ustawionej przez użytkownika oraz opcjonalnie Przekaż tę wartość do składnika projektowania.  
  
 Na przykład <xref:System.Windows.Forms.Control.Visible%2A> i <xref:System.Windows.Forms.Control.Enabled%2A> właściwości będzie cieniowanie przez `MarqueeBorderDesigner`, który uniemożliwia wprowadzanie `MarqueeBorder` kontroli niewidocznego lub wyłączonego w czasie projektowania.  
  
 Projektanci można również dodawać i usuwać właściwości. Na przykład <xref:System.Windows.Forms.Control.Padding%2A> właściwość zostanie usunięte w czasie projektowania, ponieważ `MarqueeBorder` kontroli programowo ustawia wypełnienie zależnie od rozmiaru kontrolki określony przez `LightSize` właściwości.  
  
 Klasa podstawowa dla `MarqueeBorderDesigner` jest <xref:System.ComponentModel.Design.ComponentDesigner>, która zawiera metody, które można zmienić atrybutów, właściwości i zdarzeń udostępnianych przez formant w czasie projektowania:  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 Zmieniając interfejs publiczny składnika przy użyciu tych metod, należy wykonać następujące czynności:  
  
-   Dodawanie lub usuwanie elementów w `PreFilter` tylko metody  
  
-   Modyfikowanie istniejących elementów w `PostFilter` tylko metody  
  
-   Zawsze najpierw wywoływać implementację podstawową `PreFilter` metody  
  
-   Zawsze wywoływać implementację podstawową ostatnio `PostFilter` metody  
  
 Przestrzegać tych reguł gwarantuje, że wszystkie projektantów w środowisku projektowania spójne wyświetlanie wszystkich składników projektowania.  
  
 <xref:System.ComponentModel.Design.ComponentDesigner> Klasa zawiera słownik zarządzania wartości przesłanianej właściwości, które zwalnia z konieczności tworzenia zmiennych określonego wystąpienia.  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Aby utworzyć niestandardowe projektanta na tle i filtr właściwości  
  
1.  Kliknij prawym przyciskiem myszy **projekt** folderu i Dodaj nową klasę. Nadaj pliku źródłowego z podstawowej nazwy "MarqueeBorderDesigner."  
  
2.  Otwórz `MarqueeBorderDesigner` pliku źródłowego w **edytora kodu**. W górnej części pliku należy zaimportować następujących przestrzeni nazw:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  Zmień deklarację elementu `MarqueeBorderDesigner` odziedziczone <xref:System.Windows.Forms.Design.ParentControlDesigner>.  
  
     Ponieważ `MarqueeBorder` formant może zawierać formantów podrzędnych `MarqueeBorderDesigner` dziedziczy <xref:System.Windows.Forms.Design.ParentControlDesigner>, który obsługuje interakcji z relacją nadrzędny podrzędny.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  Zastąpienie Podstawowa implementacja <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  Implementowanie <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A> właściwości. Właściwości formantu w tle tych implementacji.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a>Obsługa zmiany składnika  
 `MarqueeControlRootDesigner` Klasa udostępnia środowisko czasu projektowania niestandardowego dla Twojego `MarqueeControl` wystąpień. Większość funkcjonalność czasu projektowania jest odziedziczone <xref:System.Windows.Forms.Design.DocumentDesigner> klasy; użytkownika zostanie kodu, wdrożenie dwóch określonych dostosowań: Obsługa zmiany składników i dodawanie zleceń projektanta.  
  
 Jako projekt użytkownikom ich `MarqueeControl` wystąpienia, z projektanta głównego będzie śledzić zmian do `MarqueeControl` i jej kontrolkach podrzędnych. Środowisko czasu projektowania oferuje wygodny usługi <xref:System.ComponentModel.Design.IComponentChangeService>, śledzenie zmian do stanu składnika.  
  
 Uzyskać odwołania do tej usługi, badając środowisko <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> metody. Jeśli zapytanie zakończy się pomyślnie, z projektantem można dołączyć program obsługi <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> zdarzeń i wykonywanie, niezależnie od zadania są zobowiązane do zachowania spójnego stanu w czasie projektowania.  
  
 W przypadku liczby `MarqueeControlRootDesigner` klasy będzie wywoływać <xref:System.Windows.Forms.Control.Refresh%2A> metody na każdym `IMarqueeWidget` obiektów znajdujących się `MarqueeControl`. Spowoduje to `IMarqueeWidget` odświeżanego obiektu się odpowiednio po właściwości, takie jak jego elementu nadrzędnego <xref:System.Windows.Forms.Control.Size%2A> są zmieniane.  
  
#### <a name="to-handle-component-changes"></a>Aby obsługiwać zmiany składnika  
  
1.  Otwórz `MarqueeControlRootDesigner` pliku źródłowego w **edytora kodu** i zastąpić <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody. Wywoływać implementację podstawową z <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> i można wyszukiwać <xref:System.ComponentModel.Design.IComponentChangeService>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  Implementowanie <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> obsługi zdarzeń. Typ składnika wysyłanie testu i jeśli jest `IMarqueeWidget`, wywołanie jego <xref:System.Windows.Forms.Control.Refresh%2A> metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a>Dodawanie poleceń projektanta do sieci niestandardowej projektanta  
 Zlecenie projektanta jest połączony z obsługi zdarzeń polecenia menu. Zleceń projektanta są dodawane do menu skrótów składnika w czasie projektowania. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Design.DesignerVerb>.  
  
 Dwa zleceń projektanta zostanie dodany do Twojej projektantów: **Uruchom Test** i **testu Zatrzymaj**. Te zleceń pozwala wyświetlić zachowanie środowiska wykonawczego `MarqueeControl` w czasie projektowania. Te polecenia zostaną dodane do `MarqueeControlRootDesigner`.  
  
 Gdy **uruchomienia testu** jest wywołane, program obsługi zdarzeń zlecenie wywoła `StartMarquee` metody w `MarqueeControl`. Gdy **zatrzymania testu** jest wywołane, program obsługi zdarzeń zlecenie wywoła `StopMarquee` metody w `MarqueeControl`. Implementacja `StartMarquee` i `StopMarquee` metod wywołania tych metod w formantach zawartych w niej, które implementują `IMarqueeWidget`, więc wszystkie zawarte `IMarqueeWidget` formantów będzie również częścią testu.  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Aby dodać zleceń projektanta do Twojej projektantów niestandardowych  
  
1.  W `MarqueeControlRootDesigner` klasy, Dodaj obsługę zdarzeń o nazwie `OnVerbRunTest` i `OnVerbStopTest`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  Połączenia te programy obsługi zdarzeń do ich odpowiednich zleceń projektanta. `MarqueeControlRootDesigner`dziedziczy <xref:System.ComponentModel.Design.DesignerVerbCollection> ze swojej klasy podstawowej. Utworzysz dwa nowe <xref:System.ComponentModel.Design.DesignerVerb> obiekty i dodaj je do tej kolekcji w <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> metody.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a>Tworzenie niestandardowego elementu UITypeEditor.  
 Podczas tworzenia niestandardowego środowisko czasu projektowania dla użytkowników często jest pożądane, aby utworzyć niestandardowe interakcji z okna właściwości. Można to zrobić, tworząc <xref:System.Drawing.Design.UITypeEditor>. Aby uzyskać więcej informacji, zobacz [porady: tworzenie Edytor typów interfejsu użytkownika](http://msdn.microsoft.com/library/292c6e33-8d85-4012-9b51-05835a6f6dfd).  
  
 `MarqueeBorder` Kontroli udostępnia kilka właściwości w oknie właściwości. Dwa z tych właściwości `MarqueeSpinDirection` i `MarqueeLightShape` są reprezentowane przez wyliczenia. Aby zilustrować stosowania Edytor typów interfejsu użytkownika, `MarqueeLightShape` właściwość będzie mieć skojarzony <xref:System.Drawing.Design.UITypeEditor> klasy.  
  
#### <a name="to-create-a-custom-ui-type-editor"></a>Aby utworzyć niestandardowy typ interfejsu użytkownika edytora  
  
1.  Otwórz `MarqueeBorder` pliku źródłowego w **edytora kodu**.  
  
2.  W definicji `MarqueeBorder` klasy zadeklarować klasy o nazwie `LightShapeEditor` która pochodzi z <xref:System.Drawing.Design.UITypeEditor>.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  Deklarowanie <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> zmienna wystąpienia o nazwie `editorService`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  Zastąpienie <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> metody. Ta implementacja zwraca <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, który określa, że środowisko projektowania sposób wyświetlania `LightShapeEditor`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  Zastąpienie <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> metody. Ta implementacja odpytuje środowiska projektowania dla <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> obiektu. Jeśli się powiedzie, tworzy `LightShapeSelectionControl`. <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> Uruchomić wywoływana jest metoda `LightShapeEditor`. Wartość zwrócona przez to wywołanie jest zwracana w środowisku projektowania.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>Tworzenie formantu widoku dla Twojego niestandardowego elementu UITypeEditor.  
  
1.  `MarqueeLightShape` Właściwość obsługuje dwa rodzaje światła kształtów: `Square` i `Circle`. Spowoduje utworzenie Kontrolki niestandardowe używane wyłącznie do celów graficznie wyświetlania tych wartości w oknie właściwości. Ten formant niestandardowy będzie używany przez Twoje <xref:System.Drawing.Design.UITypeEditor> wchodzić w interakcje z okna właściwości.  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Aby utworzyć formant widoku dla niestandardowego interfejsu użytkownika Edytor typów  
  
1.  Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do `MarqueeControlLibrary` projektu. Nadaj nowej plik źródłowy podstawowej nazwy "LightShapeSelectionControl."  
  
2.  Przeciągnij dwa <xref:System.Windows.Forms.Panel> formantów **przybornika** na `LightShapeSelectionControl`. Nazwa je `squarePanel` i `circlePanel`. Rozmieść je obok siebie. Ustaw <xref:System.Windows.Forms.Control.Size%2A> właściwość obu <xref:System.Windows.Forms.Panel> formanty (60, 60). Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwość `squarePanel` do kontrolować (8, 10). Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwość `circlePanel` do kontrolować (80, 10). Wreszcie, ustaw <xref:System.Windows.Forms.Control.Size%2A> właściwość `LightShapeSelectionControl` do (150, 80).  
  
3.  Otwórz `LightShapeSelectionControl` pliku źródłowego w **edytora kodu**. W górnej części pliku, należy zaimportować <xref:System.Windows.Forms.Design?displayProperty=nameWithType> przestrzeni nazw:  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  Implementowanie <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `squarePanel` i `circlePanel` kontrolki. Te metody invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> do końca niestandardowego <xref:System.Drawing.Design.UITypeEditor> sesji edytowania.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  Deklarowanie <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> zmienna wystąpienia o nazwie `editorService`.  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  Deklarowanie `MarqueeLightShape` zmienna wystąpienia o nazwie `lightShapeValue`.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  W `LightShapeSelectionControl` konstruktora, dołącz <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń do `squarePanel` i `circlePanel` formantów <xref:System.Windows.Forms.Control.Click> zdarzenia. Ponadto zdefiniować przeładowania konstruktora, który przypisuje `MarqueeLightShape` wartość z zakresu od środowiska projektowania `lightShapeValue` pola.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  W <xref:System.ComponentModel.Component.Dispose%2A> metody detach <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku. Otwórz plik LightShapeSelectionControl.Designer.cs lub LightShapeSelectionControl.Designer.vb i usunąć definicji domyślnej <xref:System.ComponentModel.Component.Dispose%2A> metody.  
  
5.  Implementowanie `LightShape` właściwości.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  Zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Ta implementacja będzie Rysuj wypełniony kwadrat i okrąg. Zostanie również zaznacz wybraną wartość za pomocą rysowania obramowania kształtu jednego lub drugiego.  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a>Testowanie formantu niestandardowego w Projektancie  
 W tym momencie można tworzyć `MarqueeControlLibrary` projektu. Testowania implementacji tworząc kontrolkę, która dziedziczy `MarqueeControl` klasy oraz używania go w formularzu.  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Do tworzenia niestandardowych implementacji MarqueeControl  
  
1.  Otwórz `DemoMarqueeControl` w narzędziu Projektant dla formularzy systemu Windows. Spowoduje to utworzenie wystąpienia `DemoMarqueeControl` typu i wyświetla je w wystąpieniu `MarqueeControlRootDesigner` typu.  
  
2.  W **przybornika**, otwórz **składniki MarqueeControlLibrary** kartę. Zobaczysz `MarqueeBorder` i `MarqueeText` formantów dostępnych do wyboru.  
  
3.  Przeciągnij wystąpienia `MarqueeBorder` kontrolować na `DemoMarqueeControl` powierzchnię projektu. Dokowanie to `MarqueeBorder` formant do formantu nadrzędnego.  
  
4.  Przeciągnij wystąpienia `MarqueeText` kontrolować na `DemoMarqueeControl` powierzchnię projektu.  
  
5.  Skompiluj rozwiązanie.  
  
6.  Kliknij prawym przyciskiem myszy `DemoMarqueeControl` i z menu skrótów wybierz opcję **Uruchom Test** opcję, aby uruchomić animacji. Kliknij przycisk **testu Zatrzymaj** przestanie animacji.  
  
7.  Otwórz **Form1** w widoku Projekt.  
  
8.  Umieść dwa <xref:System.Windows.Forms.Button> kontrolek w formularzu. Nazwa je `startButton` i `stopButton`i zmień <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości do **Start** i **zatrzymać**odpowiednio.  
  
9. Implementowanie <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla obu <xref:System.Windows.Forms.Button> kontrolki.  
  
10. W **przybornika**, otwórz **składniki MarqueeControlTest** kartę. Zobaczysz `DemoMarqueeControl` dostępne do wyboru.  
  
11. Przeciągnij wystąpienia `DemoMarqueeControl` na **Form1** powierzchnię projektu.  
  
12. W <xref:System.Windows.Forms.Control.Click> wywołanie procedury obsługi zdarzeń, `Start` i `Stop` metody `DemoMarqueeControl`.  
  
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
  
1.  Ustaw `MarqueeControlTest` projekt jako projekt startowy i uruchom go. Zobaczysz wyświetlania formularza z `DemoMarqueeControl`. Kliknij przycisk **Start** przycisk, aby uruchomić animacji. Powinien zostać wyświetlony tekst miga i świateł przenoszenia obramowania.  
  
## <a name="next-steps"></a>Następne kroki  
 `MarqueeControlLibrary` Przedstawiono prosty implementacji niestandardowych kontrolek i skojarzone projektantów. Można wprowadzić w tym przykładzie bardziej złożone na kilka sposobów:  
  
-   Zmiana wartości właściwości `DemoMarqueeControl` w projektancie. Dodaj więcej `MarqueBorder` formanty i dokowanie je w ramach ich wystąpienia nadrzędnego do utworzenia efektu zagnieżdżonych. Eksperymentów z różnymi ustawieniami dla `UpdatePeriod` i właściwości oświetlenia.  
  
-   Tworzenie własnych implementacje `IMarqueeWidget`. Można na przykład utworzyć miga "neon znaku" lub animowany logowania z wielu obrazów.  
  
-   Dodatkowe dostosowanie doświadczenie czasu projektowania. Można spróbować przesłanianie właściwości więcej niż <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A>, i można dodać nowych właściwości. Dodawanie nowych projektanta zleceń, aby uprościć typowych zadań, takich jak dokowanie formantów podrzędnych.  
  
-   Licencja `MarqueeControl`. Aby uzyskać więcej informacji, zobacz [porady: składniki licencji i formanty](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57).  
  
-   Kontrolować sposób formantów są serializowane i sposób generowania kodu dla nich. Aby uzyskać więcej informacji, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Design.ParentControlDesigner>  
 <xref:System.Windows.Forms.Design.DocumentDesigner>  
 <xref:System.ComponentModel.Design.IRootDesigner>  
 <xref:System.ComponentModel.Design.DesignerVerb>  
 <xref:System.Drawing.Design.UITypeEditor>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Porady: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)  
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Projektanci niestandardowych](http://msdn.microsoft.com/library/ca11988e-d38e-44d8-a05d-71362ae7844d)  
 [Biblioteka kształtu .NET: Projektanta próbki](http://windowsforms.net/articles/shapedesigner.aspx)
