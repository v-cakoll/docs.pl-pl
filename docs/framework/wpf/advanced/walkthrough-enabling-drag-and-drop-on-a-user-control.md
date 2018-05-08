---
title: 'Wskazówki: włączanie przeciągania i upuszczania w kontrolce użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: e4dba856b973f1210f2d088de3ed8ae5df2c6988
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Wskazówki: włączanie przeciągania i upuszczania w kontrolce użytkownika
Ten przewodnik przedstawia sposób tworzenia formant użytkownika niestandardowego, który mogą uczestniczyć w transferu danych przeciągania i upuszczania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 W tym przewodniku spowoduje utworzenie niestandardowych WPF <xref:System.Windows.Controls.UserControl> reprezentujący okrągłego kształtu. Funkcje zostaną zaimplementowane w formancie umożliwia transfer danych za pośrednictwem przeciągania i upuszczania. Na przykład jeśli przeciąganie z jednego formantu okrąg na inny dane koloru wypełnienia zostanie skopiowana ze źródła koło z obiektem docelowym. Jeśli zostanie przeciągnięty za pomocą formantu okręgu do <xref:System.Windows.Controls.TextBox>, reprezentację ciągu kolor wypełnienia jest kopiowany do <xref:System.Windows.Controls.TextBox>. Zostanie również utworzona mała aplikacji, która zawiera dwa formanty panelu i <xref:System.Windows.Controls.TextBox> Aby przetestować funkcje przeciągania i upuszczania. Napiszesz kod, który umożliwia paneli do przetworzenia porzuconych danych koło, co umożliwi przenosić i kopiować okręgi z kolekcji Children elementu panel jednego do drugiego.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie formantu użytkownika niestandardowego.  
  
-   Kontrola użytkownika jako źródła przeciągania.  
  
-   Kontrola użytkownika jako miejsca docelowego.  
  
-   Włącz panelu na odbieranie danych z kontrolki użytkownika.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Visual Studio 2010  
  
## <a name="creating-the-application-project"></a>Tworzenie projektu aplikacji  
 W tej sekcji utworzysz infrastruktury aplikacji, w tym strony głównej z dwa panele i <xref:System.Windows.Controls.TextBox>.  
  
### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `DragDropExample`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Open MainWindow.xaml.  
  
3.  Dodaj następujący kod między otwarcia i zamknięcia <xref:System.Windows.Controls.Grid> tagów.  
  
     Ten kod znaczników tworzy interfejsu użytkownika dla aplikacji testu.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a>Dodawanie nowej kontrolki użytkownika do projektu  
 W tej sekcji nową kontrolkę użytkownika zostaną dodane do projektu.  
  
### <a name="to-add-a-new-user-control"></a>Aby dodać nową kontrolkę użytkownika  
  
1.  W menu Projekt wybierz **Dodaj kontrolkę użytkownika**.  
  
2.  W oknie dialogowym Dodawanie nowego elementu, Zmień nazwę, aby `Circle.xaml`i kliknij przycisk **Dodaj**.  
  
     Circle.XAML i jej kodem jest dodane do projektu.  
  
3.  Open Circle.xaml.  
  
     Ten plik zawiera elementy interfejsu użytkownika kontrolki użytkownika.  
  
4.  Dodaj następujący kod do katalogu głównego <xref:System.Windows.Controls.Grid> można utworzyć formantu proste użytkownika, który ma niebieskie koło jako jego interfejsie użytkownika.  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.  
  
6.  W języku C# Dodaj następujący kod po można utworzyć konstruktora kopiującego konstruktora domyślnego. W języku Visual Basic Dodaj następujący kod do utworzenia zarówno konstruktora domyślnego i Konstruktor kopiujący.  
  
     Aby umożliwić kontrolki użytkownika do skopiowania, należy dodać metody konstruktora kopiowania pliku CodeBehind. W formancie użytkownika koło uproszczony spowoduje tylko skopiowanie wypełnienia i rozmiar kontrolki użytkownika.  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a>Aby dodać kontrolkę użytkownika do głównego okna  
  
1.  Open MainWindow.xaml.  
  
2.  Dodaj następujące XAML do otwarcia <xref:System.Windows.Window> tag, aby utworzyć odwołanie do przestrzeni nazw XML dla bieżącej aplikacji.  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  W pierwszym <xref:System.Windows.Controls.StackPanel>, Dodaj następujące XAML, aby utworzyć dwa wystąpienia kontrolki użytkownika koło w pierwszym panelu.  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     Pełna XAML panelu wygląda następująco.  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a>Implementowanie zdarzeń źródła przeciągania w formancie użytkownika  
 W tej sekcji zostanie zastąpione <xref:System.Windows.UIElement.OnMouseMove%2A> — metoda i Inicjowanie operacji przeciągania i upuszczania.  
  
 Po uruchomieniu przeciągnij (przycisk myszy jest wciśnięty i wskaźnik myszy zostanie przesunięty), będzie pakiet danych ma zostać przesłany do <xref:System.Windows.DataObject>. W takim przypadku sterowania koło będzie pakietu trzy elementy danych; Reprezentacja ciągu jego kolor wypełnienia, podwójnej reprezentacji wysokości i swoją kopię.  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a>Aby zainicjować operacji przeciągania i upuszczania  
  
1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.  
  
2.  Dodaj następujące <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.MouseMove> zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     To <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie wykonuje następujące zadania:  
  
    -   Sprawdza, czy naciśnięciu lewego przycisku myszy, gdy wskaźnik myszy porusza się.  
  
    -   Pakiety danych okręgu do <xref:System.Windows.DataObject>. W takim przypadku sterowania koło pakietów trzy elementy danych; Reprezentacja ciągu jego kolor wypełnienia, podwójnej reprezentacji wysokości i swoją kopię.  
  
    -   Wywołuje statycznych <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metodę, aby zainicjować operację przeciągania i upuszczania. Następujące trzy parametry do przekazania <xref:System.Windows.DragDrop.DoDragDrop%2A> metody:  
  
        -   `dragSource` — Odwołanie do tego formantu.  
  
        -   `data` — <xref:System.Windows.DataObject> Utworzony w poprzednim kodzie.  
  
        -   `allowedEffects` Dozwolonych operacji przeciągania i upuszczania, które są <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
4.  Formantów koło kliknij i przeciągnij go za pośrednictwem panele innych okręgu i <xref:System.Windows.Controls.TextBox>. Podczas przeciągania za pośrednictwem <xref:System.Windows.Controls.TextBox>, oznaczać przenoszenie zmiany kursora.  
  
5.  Podczas przeciągania koło za pośrednictwem <xref:System.Windows.Controls.TextBox>, naciśnij klawisz CTRL. Zwróć uwagę, jak kursor zmienia się na wskazać kopię.  
  
6.  Przeciągnij i upuść okrąg na <xref:System.Windows.Controls.TextBox>. Kolor wypełnienia koła reprezentację ciągu jest dołączany do <xref:System.Windows.Controls.TextBox>.  
  
     ![Ciąg reprezentację kolor wypełnienia okręgu](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")  
  
 Domyślnie gdy kursor zmieni się podczas operacji przeciągania i upuszczania, aby wskazać, będą miały wpływ, jaki usunięcie danych. Można dostosować zwrotnych użytkownikowi Obsługa <xref:System.Windows.UIElement.GiveFeedback> zdarzeń i ustawienie różnych kursora.  
  
### <a name="to-give-feedback-to-the-user"></a>Aby przekazać opinię do użytkownika  
  
1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.  
  
2.  Dodaj następujące <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.GiveFeedback> zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     To <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie wykonuje następujące zadania:  
  
    -   Sprawdza <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości, które są ustawiane w celu upuszczania <xref:System.Windows.UIElement.DragOver> obsługi zdarzeń.  
  
    -   Ustawia kursor niestandardowych, na podstawie <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości. Kursor ma umożliwić wizualne dla użytkownika o będą miały wpływ, jaki usunięcie danych.  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
4.  Przeciągnij jeden okręgu kontroluje za pośrednictwem panele innych okręgu i <xref:System.Windows.Controls.TextBox>. Kursory są teraz niestandardowych kursorów, które zostały określone w <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienia.  
  
     ![Przeciągnij i upuść z niestandardowych kursorów](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")  
  
5.  Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.  
  
6.  Przeciągnij `green` tekst formantu okręgu. Należy zauważyć, że kursory domyślne są wyświetlane, aby wskazać skutków operacji przeciągania i upuszczania. Kursor opinii ma zawsze wartość źródła przeciągania.  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a>Implementowanie docelowego upuszczania w formancie użytkownika  
 W tej sekcji zostanie Określ, czy kontrolka użytkownika jest element docelowy upuszczania zastąpienie metody, które umożliwiają użytkownikowi do miejsca docelowego można kontrolować i przetwarzania danych, które są przenoszone na nim.  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Aby włączyć kontrolę użytkownika jako miejsca docelowego  
  
1.  Open Circle.xaml.  
  
2.  W otwarcia <xref:System.Windows.Controls.UserControl> tagów, Dodaj <xref:System.Windows.UIElement.AllowDrop%2A> właściwości i wartości `true`.  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <xref:System.Windows.UIElement.OnDrop%2A> Metoda jest wywoływana, gdy <xref:System.Windows.UIElement.AllowDrop%2A> właściwość jest ustawiona na `true` i kontrola użytkownika koło jest upuszczony danych ze źródła przeciągania. W przypadku tej metody możesz przetwarzania danych, która została usunięta i dotyczą danych okręgu.  
  
### <a name="to-process-the-dropped-data"></a>Do przetwarzania danych porzuconych  
  
1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.  
  
2.  Dodaj następujące <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.Drop> zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     To <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie wykonuje następujące zadania:  
  
    -   Używa <xref:System.Windows.DataObject.GetDataPresent%2A> metodę sprawdzania, czy dane przeciągane zawiera obiekt ciągu.  
  
    -   Używa <xref:System.Windows.DataObject.GetData%2A> metodę, aby wyodrębnić dane ciągu, jeśli jest obecny.  
  
    -   Używa <xref:System.Windows.Media.BrushConverter> spróbuj przekonwertować ciągu do <xref:System.Windows.Media.Brush>.  
  
    -   Jeśli konwersja zakończy się pomyślnie, stosuje pędzla do <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewnia koło formantu interfejsu użytkownika.  
  
    -   Znaczniki <xref:System.Windows.UIElement.Drop> zdarzenie, ponieważ obsługiwane. Zdarzenie upuszczania powinny zostać oznaczone jako obsługi, aby poinformować inne elementy, które odbierają to zdarzenie kontrolki użytkownika koło obsługiwane go.  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
4.  Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.  
  
5.  Przeciągnij tekst do formantu koło i upuść go. Zmiany koło z blue zielony.  
  
     ![Konwertowanie ciągu pędzel](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")  
  
6.  Wpisz tekst `green` w <xref:System.Windows.Controls.TextBox>.  
  
7.  Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.  
  
8.  Przeciągnij go do kontroli koło i upuść go. Należy zauważyć, że kursor zmienia się na wskazują, że listy jest dozwolone, ale nie zmienia kolor okręgu, ponieważ `gre` nie jest prawidłowy kolor.  
  
9. Przeciągnij z formantu zielone koło i usunąć niebieskie formantu koło. Zmiany koło z blue zielony. Należy zauważyć, że jest wyświetlany kursor, który jest zależny od tego, czy <xref:System.Windows.Controls.TextBox> lub okręgu jest elementem źródłowym przeciągania.  
  
 Ustawienie <xref:System.Windows.UIElement.AllowDrop%2A> właściwości `true` i przetwarzania danych porzuconych jest wszystko, co jest wymagane w celu włączenia element jako element docelowy upuszczania. Jednak aby zapewnić lepsze środowisko użytkownika, możesz również obsługi <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, i <xref:System.Windows.UIElement.DragOver> zdarzenia. W tych zdarzeń można wykonać kontroli i wyrazić swoją opinię dodatkowe do użytkownika, zanim danych zostanie porzucony.  
  
 Gdy danych zostanie przeciągnięty nad formantem użytkownika koło, formantu powiadamiać źródła przeciągania, czy może przetwarzać dane, które przeciągania. Jeśli formant nie może określić sposób przetwarzania danych, należy go odmówić listy. Aby to zrobić, będzie obsługiwać <xref:System.Windows.UIElement.DragOver> zdarzeń i zestaw <xref:System.Windows.DragEventArgs.Effects%2A> właściwości.  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a>Aby sprawdzić, czy jest dozwolone porzucenia danych  
  
1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.  
  
2.  Dodaj następujące <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.DragOver> zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     To <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie wykonuje następujące zadania:  
  
    -   Ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.None>.  
  
    -   Wykonuje tej samej testy, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodę, aby określić, czy formant użytkownika koło może przetwarzać przeciąganego danych.  
  
    -   Jeśli formant użytkownika może przetwarzać danych, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
4.  Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.  
  
5.  Przeciągnij tekst formantu okręgu. Należy zauważyć, że kursor zmienia się teraz na wskazują, że listy jest niedozwolona, ponieważ `gre` nie jest prawidłowy kolor.  
  
 Może dodatkowo ulepszyć środowisko użytkownika, stosując Podgląd operacji usuwania. Kontrolki użytkownika koło, spowoduje zastąpienie <xref:System.Windows.UIElement.OnDragEnter%2A> i <xref:System.Windows.UIElement.OnDragLeave%2A> metody. Po danych zostanie przeciągnięty nad formantem bieżące tło <xref:System.Windows.Shapes.Shape.Fill%2A> jest zapisywany w zmiennej symbolu zastępczego. Ciąg jest następnie konwertowana pędzla i stosowane do <xref:System.Windows.Shapes.Ellipse> zapewnia okręgu interfejsu użytkownika. Jeśli dane zostanie przeciągnięty poza okręgu bez usuwane oryginalnej <xref:System.Windows.Shapes.Shape.Fill%2A> wartość jest ponownie stosowana do okręgu.  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Aby wyświetlić podgląd skutków operacji przeciągania i upuszczania  
  
1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.  
  
2.  W klasie koło zadeklarować prywatnej <xref:System.Windows.Media.Brush> zmiennej o nazwie `_previousFill` i zainicjować go do `null`.  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  Dodaj następujące <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.DragEnter> zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     To <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie wykonuje następujące zadania:  
  
    -   Zapisuje <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość <xref:System.Windows.Shapes.Ellipse> w `_previousFill` zmiennej.  
  
    -   Wykonuje tej samej testy, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodę, aby określić, czy dane mogą być konwertowane na <xref:System.Windows.Media.Brush>.  
  
    -   Jeśli dane są konwertowane na prawidłową <xref:System.Windows.Media.Brush>, stosuje je do <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.  
  
4.  Dodaj następujące <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.DragLeave> zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     To <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie wykonuje następujące zadania:  
  
    -   Stosuje <xref:System.Windows.Media.Brush> zapisane w `_previousFill` zmienną <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewnia interfejsu użytkownika koło kontrolki użytkownika.  
  
5.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
6.  Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.  
  
7.  Przeciągnij tekst nad formantem okręgu bez porzuceniem jej. Zmiany koło z blue zielony.  
  
     ![Efekty przeciągnij&#45;i&#45;porzucić operacji](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")  
  
8.  Przeciągnij tekst od kontroli okręgu. Zmiany koło z zielonym kopii na niebieski.  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a>Włączanie panelu do odbierania porzucony danych  
 W tej sekcji zostaną włączone zespoły obsługujące kontrolek użytkownika okrąg na działanie jako miejsc docelowych przeciąganego danych okręgu. Kod, który umożliwia przenieść koło z jednego panelu lub utworzyć kopię formantu koło, przytrzymując klawisz CTRL podczas przeciągania i upuszczania koło zostaną zaimplementowane.  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a>Aby włączyć panelu jako miejsca docelowego  
  
1.  Open MainWindow.xaml.  
  
2.  Jak pokazano w poniższych XAML, w każdym <xref:System.Windows.Controls.StackPanel> formantów, Dodaj obsługę <xref:System.Windows.UIElement.DragOver> i <xref:System.Windows.UIElement.Drop> zdarzenia. Nazwa <xref:System.Windows.UIElement.DragOver> program obsługi zdarzeń, `panel_DragOver`i nazwij <xref:System.Windows.UIElement.Drop> program obsługi zdarzeń, `panel_Drop`.  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  Otwórz MainWindows.xaml.cs lub MainWindow.xaml.vb.  
  
4.  Dodaj następujący kod do <xref:System.Windows.UIElement.DragOver> obsługi zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     To <xref:System.Windows.UIElement.DragOver> obsługi zdarzeń wykonuje następujące zadania:  
  
    -   Sprawdza, czy dane przeciągane zawiera dane "Obiektu", które zostało umieszczone w <xref:System.Windows.DataObject> przez formant użytkownika koło i przekazywane w wywołaniu <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
    -   Jeśli dane "Obiektu" jest obecny, sprawdza, czy zostanie naciśnięty klawisz CTRL.  
  
    -   Jeśli zostanie naciśnięty klawisz CTRL, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Copy>. W przeciwnym razie wartość <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Move>.  
  
5.  Dodaj następujący kod do <xref:System.Windows.UIElement.Drop> obsługi zdarzeń.  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     To <xref:System.Windows.UIElement.Drop> obsługi zdarzeń wykonuje następujące zadania:  
  
    -   Sprawdza, czy <xref:System.Windows.UIElement.Drop> zdarzenie jest już obsługiwane. Na przykład po przerwaniu okrąg na innym koło, które uchwytów <xref:System.Windows.UIElement.Drop> zdarzeń, nie ma panelu, zawierający kółko, aby również je obsłużyć.  
  
    -   Jeśli <xref:System.Windows.UIElement.Drop> zdarzeń nie jest obsługiwana, sprawdza czy zostanie naciśnięty klawisz CTRL.  
  
    -   Jeśli po naciśnięciu klawisza CTRL <xref:System.Windows.UIElement.Drop> następuje, sprawia, że kopia okręgu kontroli i dodać go do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji <xref:System.Windows.Controls.StackPanel>.  
  
    -   Jeśli nie zostanie naciśnięty klawisz CTRL, przenosi koło z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji nadrzędnej panel do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu, który został porzucony na.  
  
    -   Ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości powiadomiono <xref:System.Windows.DragDrop.DoDragDrop%2A> metody czy zostało przeprowadzone operacji przenoszenia lub kopiowania.  
  
6.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
7.  Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.  
  
8.  Przeciągnij tekst nad formantem koło i upuść go.  
  
9. Przeciągnij formant koło z lewego panelu na prawym panelu i upuść go. Okręgu zostanie usunięty z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lewego panelu i dodany do kolekcji elementów podrzędnych w prawym panelu.  
  
10. Przeciągnij formant koło z panelu, w którym się do innych panelu i upuść naciskaj klawisz CTRL. Okręgu jest kopiowany i dodawane do kopii <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu docelowego.  
  
     ![Przeciąganie koło naciskaj klawisz CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd przeciągania i upuszczania](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
