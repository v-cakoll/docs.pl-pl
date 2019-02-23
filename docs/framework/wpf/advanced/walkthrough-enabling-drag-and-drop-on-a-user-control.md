---
title: 'Przewodnik: Włączanie przeciągania i upuszczania w kontrolce użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: a2aa1d09b922809f42fe14bd674c2a87b9e5a3f8
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747798"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Przewodnik: Włączanie przeciągania i upuszczania w kontrolce użytkownika

W tym instruktażu pokazano, jak utworzyć formant użytkownika niestandardowego, które mogą uczestniczyć w transferu danych przeciągnij i upuść [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].

W tym przewodniku utworzysz niestandardowego WPF <xref:System.Windows.Controls.UserControl> reprezentujący okrągłe. Funkcje zostaną zaimplementowane w kontrolce umożliwia transfer danych za pomocą przeciągania i upuszczania. Na przykład jeśli przeciągniesz z jednego formantu okrąg do innego, dane koloru wypełnienia zostanie skopiowana ze źródła okrąg do obiektu docelowego. Jeśli przeciągniesz w kontrolce okrąg do <xref:System.Windows.Controls.TextBox>, reprezentacja ciągu koloru wypełnienia jest kopiowany do <xref:System.Windows.Controls.TextBox>. Mała aplikacja, która zawiera dwie kontrolki panel zostanie również utworzony i <xref:System.Windows.Controls.TextBox> do testowania funkcji przeciągania i upuszczania. Trzeba napisać kod, który umożliwia paneli do przetwarzania danych porzuconych koła, która umożliwia przenoszenie lub kopiowanie okręgów z kolekcji elementów podrzędnych panelu jednego do drugiego.

W instruktażu przedstawiono następujące zagadnienia:

-   Tworzenie niestandardowej kontrolki użytkownika.

-   Włącz do źródła przeciągnij formant użytkownika.

-   Włącz kontrolkę użytkownika do miejsca docelowego.

-   Włączanie panelu na odbieranie danych z kontrolki użytkownika.

## <a name="prerequisites"></a>Wymagania wstępne

Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.

## <a name="create-the-application-project"></a>Utwórz projekt aplikacji
 W tej sekcji utworzysz infrastruktury aplikacji, która zawiera strona główna z dwa panele i <xref:System.Windows.Controls.TextBox>.

1.  Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `DragDropExample`. Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

2.  Open MainWindow.xaml.

3.  Dodaj następujący kod między otwierającym i zamykającym <xref:System.Windows.Controls.Grid> tagów.

     Ten kod znaczników tworzy interfejs użytkownika dla aplikacji testowej.

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>Dodaj nową kontrolkę użytkownika do projektu
 W tej sekcji dodasz nowy formant użytkownika do projektu.

1.  Z menu projektu wybierz **Dodaj kontrolkę użytkownika**.

2.  W **Dodaj nowy element** okna dialogowego pole, Zmień nazwę na `Circle.xaml`i kliknij przycisk **Dodaj**.

     Circle.XAML i jego związanym z kodem są dodawane do projektu.

3.  Open Circle.xaml.

     Ten plik zawiera elementy interfejsu użytkownika formantu użytkownika.

4.  Dodaj następujący kod do katalogu głównego <xref:System.Windows.Controls.Grid> utworzyć kontrolkę użytkownika proste jasnoniebieski okrąg jako jego interfejsie użytkownika.

     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.

6.  W języku C# Dodaj następujący kod po konstruktora domyślnego, aby utworzyć Konstruktor kopiujący. W języku Visual Basic Dodaj następujący kod, aby utworzyć domyślny konstruktor i Konstruktor kopiujący.

     Aby umożliwić kontrolki użytkownika, który ma być kopiowany, dodajesz metodę konstruktora kopiowania w pliku związanym z kodem. W kontrolce użytkownika uproszczone okrąg możesz zostaną skopiowane tylko wypełnienia i rozmiar kontrolki użytkownika.

     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>Dodaj kontrolkę użytkownika do głównego okna

1.  Open MainWindow.xaml.

2.  Dodaj następujące XAML do otwarcia <xref:System.Windows.Window> tagu, można utworzyć odwołania do przestrzeni nazw XML dla bieżącej aplikacji.

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3.  W pierwszym <xref:System.Windows.Controls.StackPanel>, Dodaj następujące XAML, aby utworzyć dwa wystąpienia kontrolki użytkownika okrąg w pierwszym panelu.

     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     Pełne XAML panelu wygląda podobnie do poniższego.

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>Implementowanie zdarzenia źródła przeciągania w kontrolce użytkownika
 W tej sekcji spowoduje przesłonięcie <xref:System.Windows.UIElement.OnMouseMove%2A> metody i zainicjuj operację przeciągania i upuszczania.

 Po uruchomieniu przeciągnij przycisk myszy jest wciśnięty i wskaźnik myszy zostanie przeniesiony, będzie spakować dane do przesłania do <xref:System.Windows.DataObject>. W takim przypadku kontrolka okrąg będzie pakietu trzy elementy danych; ciąg reprezentujący jego kolor wypełnienia, Podwójna reprezentacja jego wysokości i swoją kopię.

### <a name="to-initiate-a-drag-and-drop-operation"></a>Aby zainicjować operacji przeciągania i upuszczania

1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.

2.  Dodaj następujący kod <xref:System.Windows.UIElement.OnMouseMove%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.MouseMove> zdarzeń.

     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     To <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie wykonuje następujące zadania:

    -   Sprawdza, czy naciśnięciu lewego przycisku myszy, gdy wskaźnik myszy porusza się.

    -   Pakiety danych okrąg do <xref:System.Windows.DataObject>. W takim przypadku kontrolka okrąg pakietów trzy elementy danych; ciąg reprezentujący jego kolor wypełnienia, Podwójna reprezentacja jego wysokości i swoją kopię.

    -   Wywołuje statyczną <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metodę, aby zainicjować operację przeciągania i upuszczania. Przekaż następujące trzy parametry, aby <xref:System.Windows.DragDrop.DoDragDrop%2A> metody:

        -   `dragSource` — Odwołanie do tego formantu.

        -   `data` — <xref:System.Windows.DataObject> Utworzony w poprzednim kodzie.

        -   `allowedEffects` Dozwolone operacje przeciągania i upuszczania, które są <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.

3.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

4.  Kliknij jeden z formantów okrąg i przeciągnij go za pośrednictwem paneli, okrąg, a <xref:System.Windows.Controls.TextBox>. Podczas przeciągania przez <xref:System.Windows.Controls.TextBox>, zmiany kursor do wskazania przejście.

5.  Podczas przeciągania okręgu za pośrednictwem <xref:System.Windows.Controls.TextBox>, naciśnij klawisz **Ctrl** klucza. Zwróć uwagę, jak kursor zmienia się do wskazania kopię.

6.  Przeciąganie i upuszczanie koła na <xref:System.Windows.Controls.TextBox>. Kolor wypełnienia koła reprezentację ciągu jest dołączany do <xref:System.Windows.Controls.TextBox>.

     ![Ciąg reprezentujący kolor wypełnienia koła](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")

Domyślnie kursor zmieni się podczas operacji przeciągania i upuszczania, aby wskazać, będzie miał wpływ, jaki usunięcie danych. Można dostosować zwrotnych użytkownikowi obsługi <xref:System.Windows.UIElement.GiveFeedback> zdarzeń i ustawianie różnych kursora.

## <a name="give-feedback-to-the-user"></a>Prześlij opinię do użytkownika

1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.

2.  Dodaj następujący kod <xref:System.Windows.UIElement.OnGiveFeedback%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.GiveFeedback> zdarzeń.

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     To <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie wykonuje następujące zadania:

    -   Sprawdza, czy <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości, które są ustawiane w element docelowy upuszczania <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń.

    -   Ustawia kursor niestandardowych, na podstawie <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości. Kursor jest przeznaczona do przekazać wizualną opinię użytkownikowi o będzie mieć wpływ, jaki usunięcie danych.

3.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

4.  Przeciągnij jeden z okręgów kontroluje za pośrednictwem paneli, okrąg, a <xref:System.Windows.Controls.TextBox>. Zauważ, że kursory są teraz kursorów niestandardowych, które określiłeś w <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienia.

     ![Przeciąganie i upuszczanie za pomocą niestandardowych kursorów](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5.  Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.

6.  Przeciągnij `green` tekst do kontrolki okrąg. Zauważ, że kursory domyślny są wyświetlane w celu wskazania skutków operacji przeciągania i upuszczania. Kursor opinie zawsze jest ustawiany przez elementem źródłowym przeciągania.

## <a name="implement-drop-target-events-in-the-user-control"></a>Implementowanie docelowego upuszczania w kontrolce użytkownika
 W tej sekcji określisz, że kontrolka użytkownika znajduje się miejsca docelowego, zastąpienie metody, które umożliwia użytkownikowi kontrolowanie jako miejsca docelowego i przetwarzania danych, który został upuszczony na nim.

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Aby włączyć funkcję Kontrola użytkownika jako miejsca docelowego

1.  Open Circle.xaml.

2.  W przypadku otwarcia <xref:System.Windows.Controls.UserControl> tagów, należy dodać <xref:System.Windows.UIElement.AllowDrop%2A> właściwości i ustaw ją na `true`.

     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<xref:System.Windows.UIElement.OnDrop%2A> Metoda jest wywoływana, gdy <xref:System.Windows.UIElement.AllowDrop%2A> właściwość jest ustawiona na `true` i dane ze źródła przeciągania został upuszczony na formant użytkownika okrąg. W przypadku tej metody spowoduje przetwarzania danych, który został upuszczony i zastosować je do koła.

### <a name="to-process-the-dropped-data"></a>Do przetwarzania elementów usuniętych danych

1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.

2.  Dodaj następujący kod <xref:System.Windows.UIElement.OnDrop%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.Drop> zdarzeń.

     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     To <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie wykonuje następujące zadania:

    -   Używa <xref:System.Windows.DataObject.GetDataPresent%2A> metodę sprawdzania, czy przeciąganego danych zawiera obiekt ciągu.

    -   Używa <xref:System.Windows.DataObject.GetData%2A> metodę, aby wyodrębnić dane ciągu, jeśli jest obecny.

    -   Używa <xref:System.Windows.Media.BrushConverter> próbował przekonwertować ciąg do <xref:System.Windows.Media.Brush>.

    -   Jeśli konwersja się powiedzie, ma zastosowanie pędzla, który ma <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewniający interfejsu użytkownika formantu okrąg.

    -   Znaczniki <xref:System.Windows.UIElement.Drop> zdarzeń jako obsługiwane. Zdarzenie upuszczania należy oznaczyć jako obsłużony, dzięki czemu inne elementy, które odbierają to zdarzenie wiadomo, kontrolki użytkownika okrąg obsługiwania go.

3.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

4.  Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.

5.  Przeciągnij tekst do kontrolki okrąg i upuść go. Koło zmienia się od niebieskiego na zielony.

     ![Konwertowanie ciągu pędzel](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6.  Wpisz tekst `green` w <xref:System.Windows.Controls.TextBox>.

7.  Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.

8.  Przeciągnij go do kontroli okrąg i upuść go. Należy zauważyć, że kursor zmienia się na wskazują, że listy jest dozwolone, ale nie zmienia kolor koła, ponieważ `gre` nie jest prawidłowym kolorem.

9. Przeciągnij z zielonym kontroli okrąg i upuść na niebieski sterowania okrąg. Koło zmienia się od niebieskiego na zielony. Należy zauważyć, że jest wyświetlany kursor, który jest zależny od tego, czy <xref:System.Windows.Controls.TextBox> lub koła jest elementem źródłowym przeciągania.

Ustawienie <xref:System.Windows.UIElement.AllowDrop%2A> właściwość `true` i przetwarzanie danych porzuconych wszystko, co jest wymagane do włączenia elementu do miejsca docelowego. Jednakże, aby zapewnić lepsze środowisko użytkownika, należy również obsługiwać <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, i <xref:System.Windows.UIElement.DragOver> zdarzenia. W ramach tych zdarzeń można wykonać testy i Prześlij dodatkową opinię do użytkownika, zanim danych zostało porzucone.

Po danych jest przeciągany nad kontrolki użytkownika koła, formant powinien Powiadom elementem źródłowym przeciągania czy może przetworzyć dane, które przeciągania. Jeśli formant nie potrafi do przetwarzania danych, należy go odmówić listy. Aby to zrobić, będziesz obsługiwać <xref:System.Windows.UIElement.DragOver> zdarzeń i ustaw <xref:System.Windows.DragEventArgs.Effects%2A> właściwości.

### <a name="to-verify-that-the-data-drop-is-allowed"></a>Aby sprawdzić, czy listy danych jest dozwolone

1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.

2.  Dodaj następujący kod <xref:System.Windows.UIElement.OnDragOver%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragOver> zdarzeń.

     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     To <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie wykonuje następujące zadania:

    -   Zestawy <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragDropEffects.None>.

    -   Wykonuje ten sam testów, które są wykonywane w ramach <xref:System.Windows.UIElement.OnDrop%2A> metodę pozwala ustalić, czy okrąg kontrolki użytkownika można przetwarzać dane przeciąganego.

    -   Jeśli kontrolka użytkownika może przetwarzać dane, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.

3.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

4.  Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.

5.  Przeciągnij tekst do kontrolki okrąg. Należy zauważyć, że kursor zmienia się teraz do wskazania, że listy jest niedozwolona, ponieważ `gre` nie jest prawidłowym kolorem.

 Może dodatkowo ulepszyć środowisko użytkownika, stosując Podgląd wykonać operacji usuwania. Kontrolki użytkownika koła, spowoduje to zastąpienie <xref:System.Windows.UIElement.OnDragEnter%2A> i <xref:System.Windows.UIElement.OnDragLeave%2A> metody. Jeśli danych jest przeciągnięty ponad kontrolką, bieżące tło <xref:System.Windows.Shapes.Shape.Fill%2A> są zapisywane w zmiennej symbol zastępczy. Ciąg jest konwertowany na pędzel i zastosowane do <xref:System.Windows.Shapes.Ellipse> zapewniający koła interfejsu użytkownika. Jeśli danych jest przeciągnąć poza okręgu bez Trwa porzucanie, oryginalnym <xref:System.Windows.Shapes.Shape.Fill%2A> wartość jest ponownie zastosować koła.

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Aby wyświetlić podgląd skutków operacji przeciągania i upuszczania

1.  Otwórz Circle.xaml.cs lub Circle.xaml.vb.

2.  W klasie Circle zadeklarować prywatnej <xref:System.Windows.Media.Brush> zmiennej o nazwie `_previousFill` i zainicjować jej do `null`.

     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3.  Dodaj następujący kod <xref:System.Windows.UIElement.OnDragEnter%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragEnter> zdarzeń.

     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     To <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie wykonuje następujące zadania:

    -   Zapisuje <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość <xref:System.Windows.Shapes.Ellipse> w `_previousFill` zmiennej.

    -   Wykonuje ten sam testów, które są wykonywane w ramach <xref:System.Windows.UIElement.OnDrop%2A> metodę pozwala ustalić, czy dane mogą być konwertowane na <xref:System.Windows.Media.Brush>.

    -   Jeśli danych jest konwertowany na prawidłowym <xref:System.Windows.Media.Brush>, stosuje ją do <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.

4.  Dodaj następujący kod <xref:System.Windows.UIElement.OnDragLeave%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragLeave> zdarzeń.

     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     To <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie wykonuje następujące zadania:

    -   Stosuje <xref:System.Windows.Media.Brush> zapisane w `_previousFill` zmienną <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewniający interfejsu użytkownika formantu użytkownika okrąg.

5.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

6.  Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.

7.  Przeciągnij tekst nad formantem koła, bez usuwania go. Koło zmienia się od niebieskiego na zielony.

     ![Efekty przeciągnij&#45;i&#45;porzucić operacji](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8.  Przeciągnij tekst od kontroli okrąg. Koło zmienia się z zielonym kopii na niebieski.

## <a name="enable-a-panel-to-receive-dropped-data"></a>Włączanie panelu na odbieranie danych porzuconych

W tej sekcji możesz włączyć paneli, które hostowanie kontrolki użytkownika koła, aby pełnić rolę miejsc docelowych dla przeciąganego danych okrąg. Wdroży kod, który umożliwia Aby przenieść jeden panel okrąg lub kopię kontroli koła, przytrzymując **Ctrl** klucza podczas przeciągania i upuszczania okrąg.

1.  Open MainWindow.xaml.

2.  Jak pokazano w poniższym XAML, we wszystkich <xref:System.Windows.Controls.StackPanel> formantów, Dodaj programy obsługi dla <xref:System.Windows.UIElement.DragOver> i <xref:System.Windows.UIElement.Drop> zdarzenia. Nazwa <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń `panel_DragOver`i nadaj <xref:System.Windows.UIElement.Drop> programu obsługi zdarzeń `panel_Drop`.

     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3.  Otwórz MainWindows.xaml.cs lub MainWindow.xaml.vb.

4.  Dodaj następujący kod do <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń.

     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     To <xref:System.Windows.UIElement.DragOver> program obsługi zdarzeń wykonuje następujące zadania:

    -   Sprawdza, czy przeciąganego danych zawiera dane "Object", która została spakowana w <xref:System.Windows.DataObject> przez funkcję Kontrola użytkownika okrąg i przekazywane w wywołaniu <xref:System.Windows.DragDrop.DoDragDrop%2A>.

    -   Jeśli dane "Object" jest obecna, sprawdza czy **Ctrl** naciśnięcia klawisza.

    -   Jeśli **Ctrl** zostanie naciśnięty klawisz, zestawy <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragDropEffects.Copy>. W przeciwnym wypadku ustaw <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragDropEffects.Move>.

5.  Dodaj następujący kod do <xref:System.Windows.UIElement.Drop> programu obsługi zdarzeń.

     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     To <xref:System.Windows.UIElement.Drop> program obsługi zdarzeń wykonuje następujące zadania:

    -   Sprawdza, czy <xref:System.Windows.UIElement.Drop> zdarzenie jest już obsługiwane. Na przykład po przerwaniu koła na innym koło, które obsługuje <xref:System.Windows.UIElement.Drop> zdarzenia mają być panel, który zawiera koła, również go obsłużyć.

    -   Jeśli <xref:System.Windows.UIElement.Drop> zdarzeń nie jest obsługiwany, sprawdza czy **Ctrl** naciśnięcia klawisza.

    -   Jeśli **Ctrl** naciśnięciu klawisza, gdy <xref:System.Windows.UIElement.Drop> się stanie, sprawia, że kopia okręgu kontroli i dodać go do <xref:System.Windows.Controls.Panel.Children%2A> zbiór <xref:System.Windows.Controls.StackPanel>.

    -   Jeśli **Ctrl** nie jest wciśnięty klawisz przenosi koło z <xref:System.Windows.Controls.Panel.Children%2A> zbiór jego nadrzędnego panelu <xref:System.Windows.Controls.Panel.Children%2A> zbiór panel, który został upuszczony.

    -   Zestawy <xref:System.Windows.DragEventArgs.Effects%2A> właściwości, aby powiadomić <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda czy wykonano operację przenoszenia lub kopiowania.

6.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

7.  Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.

8.  Przeciągnij tekst nad formantem okrąg i upuść go.

9. Przeciągnij formant koło z lewego panelu na prawym panelu i upuść go. Koło zostanie usunięty z <xref:System.Windows.Controls.Panel.Children%2A> zbiór panelu po lewej stronie i dodawane do kolekcji elementów podrzędnych w prawym panelu.

10. Przeciągnij formant koło z panelu jest do innego panelu i upuść go podczas naciśnięcie **Ctrl** klucza. Koło jest kopiowana, a kopia zostanie dodany do <xref:System.Windows.Controls.Panel.Children%2A> zbiór odbieranie panelu.

     ![Przeciąganie okrąg w trakcie naciskania klawisza CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>Zobacz także

- [Przegląd przeciągania i upuszczania](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)