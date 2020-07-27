---
title: 'Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika'
description: Dowiedz się, jak utworzyć niestandardową kontrolkę użytkownika, która może uczestniczyć w przesyłaniu danych metodą "przeciągnij i upuść" w Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 12ad47035a09995094014841b083062743fc2574
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168273"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika

W tym instruktażu pokazano, jak utworzyć niestandardową kontrolkę użytkownika, która może uczestniczyć w transferze danych metodą "przeciągnij i upuść" w temacie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] .

W tym instruktażu utworzysz niestandardową WPF, <xref:System.Windows.Controls.UserControl> która reprezentuje kształt okręgu. W celu umożliwienia przesyłania danych przez przeciąganie i upuszczanie zostanie wdrożona funkcja na formancie. Na przykład, jeśli przeciągniesz jeden z formantów okręgu do innego, dane koloru wypełnienia są kopiowane z okręgu źródłowego do obiektu docelowego. Jeśli przeciągniesz z kontrolki Circle do <xref:System.Windows.Controls.TextBox> , ciąg reprezentujący kolor wypełnienia jest kopiowany do <xref:System.Windows.Controls.TextBox> . Utworzysz również małą aplikację, która zawiera dwie kontrolki paneli i <xref:System.Windows.Controls.TextBox> do testowania funkcji przeciągania i upuszczania. Napiszesz kod, który umożliwi panelom przetwarzanie porzuconych danych o kółku, co umożliwi przenoszenie lub kopiowanie okręgów z kolekcji Children jednego panelu do drugiego.

W instruktażu przedstawiono następujące zagadnienia:

- Utwórz niestandardową kontrolkę użytkownika.

- Włącz kontrolkę użytkownika jako źródło przeciągania.

- Włącz kontrolkę użytkownika jako element docelowy upuszczania.

- Włącz panel do odbierania danych porzuconych z kontrolki użytkownika.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-application-project"></a>Tworzenie projektu aplikacji
 W tej sekcji utworzysz infrastrukturę aplikacji, która obejmuje stronę główną z dwoma panelami i <xref:System.Windows.Controls.TextBox> .

1. Utwórz nowy projekt aplikacji WPF w programie Visual Basic lub Visual C# o nazwie `DragDropExample` . Aby uzyskać więcej informacji, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

2. Otwórz MainWindow. XAML.

3. Dodaj następujące znaczniki między tagiem otwierającym i zamykającym <xref:System.Windows.Controls.Grid> .

     Ten znacznik tworzy interfejs użytkownika dla aplikacji testowej.

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>Dodaj nową kontrolkę użytkownika do projektu
 W tej sekcji dodasz nową kontrolkę użytkownika do projektu.

1. W menu Projekt wybierz polecenie **Dodaj kontrolkę użytkownika**.

2. W oknie dialogowym **Dodaj nowy element** Zmień nazwę na `Circle.xaml` , a następnie kliknij przycisk **Dodaj**.

     W projekcie zostanie dodany okrąg. XAML i jego kod.

3. Otwórz Circle. XAML.

     Ten plik będzie zawierać elementy interfejsu użytkownika kontrolki użytkownika.

4. Dodaj następujący znacznik do katalogu głównego, <xref:System.Windows.Controls.Grid> Aby utworzyć prostą kontrolkę użytkownika, która ma niebieski okrąg jako interfejs użytkownika.

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. Otwórz Circle.xaml.cs lub Circle. XAML. vb.

6. W języku C# Dodaj następujący kod po konstruktorze bez parametrów, aby utworzyć Konstruktor kopiujący. W Visual Basic Dodaj następujący kod, aby utworzyć zarówno konstruktora bez parametrów, jak i konstruktora kopiującego.

     Aby umożliwić skopiowanie kontrolki użytkownika, należy dodać metodę kopiowania konstruktora w pliku związanym z kodem. W uproszczonej kontrolce użytkownika kółka będziesz kopiować tylko wypełnienie i rozmiar kontrolki użytkownika.

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>Dodaj kontrolkę użytkownika do okna głównego

1. Otwórz MainWindow. XAML.

2. Dodaj następujący kod XAML do tagu otwierającego, <xref:System.Windows.Window> Aby utworzyć odwołanie do przestrzeni nazw XML dla bieżącej aplikacji.

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. W pierwszej kolejności <xref:System.Windows.Controls.StackPanel> Dodaj następujący kod XAML, aby utworzyć dwa wystąpienia kontrolki użytkownika Circle na pierwszym panelu.

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     Pełny kod XAML dla panelu wygląda podobnie do poniższego.

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>Implementowanie zdarzeń przeciągania źródła w kontrolce użytkownika
 W tej sekcji zastąpisz <xref:System.Windows.UIElement.OnMouseMove%2A> metodę i zainicjujesz operację przeciągania i upuszczania.

 Po rozpoczęciu przeciągania (przycisk myszy jest wciśnięty, a mysz jest przenoszona), dane zostaną spakowane w celu przeniesienia do programu <xref:System.Windows.DataObject> . W takim przypadku formant Circle spowoduje spakowanie trzech elementów danych; ciąg reprezentujący kolor wypełnienia, podwójną reprezentację wysokości i kopię siebie.

### <a name="to-initiate-a-drag-and-drop-operation"></a>Aby zainicjować operację przeciągania i upuszczania

1. Otwórz Circle.xaml.cs lub Circle. XAML. vb.

2. Dodaj następujące <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.MouseMove> zdarzenia.

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     To <xref:System.Windows.UIElement.OnMouseMove%2A> przesłonięcie wykonuje następujące zadania:

    - Sprawdza, czy lewy przycisk myszy jest wciśnięty podczas przesuwania myszy.

    - Pakuje dane okręgu do <xref:System.Windows.DataObject> . W takim przypadku Kierownica ma trzy elementy danych; ciąg reprezentujący kolor wypełnienia, podwójną reprezentację wysokości i kopię siebie.

    - Wywołuje metodę statyczną <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> w celu zainicjowania operacji przeciągania i upuszczania. Do metody przekazywane są następujące trzy parametry <xref:System.Windows.DragDrop.DoDragDrop%2A> :

        - `dragSource`— Odwołanie do tego formantu.

        - `data`— <xref:System.Windows.DataObject> Utworzono w poprzednim kodzie.

        - `allowedEffects`— Dozwolone operacje przeciągania i upuszczania, które są <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move> .

3. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.

4. Kliknij jedną z kontrolek okręgu i przeciągnij ją nad panele, drugi okrąg i <xref:System.Windows.Controls.TextBox> . Podczas przeciągania nad <xref:System.Windows.Controls.TextBox> kursor zmieni się, aby wskazać przeniesienie.

5. Przeciągając okrąg na <xref:System.Windows.Controls.TextBox> , naciśnij klawisz **Ctrl** . Zauważ, że kursor zmieni się, aby wskazać kopię.

6. Przeciągnij i upuść okrąg na <xref:System.Windows.Controls.TextBox> . Ciąg reprezentujący kolor wypełnienia okręgu jest dołączany do <xref:System.Windows.Controls.TextBox> .

     ![Ciąg reprezentujący kolor wypełnienia okręgu](./media/dragdrop-colorstring.png "DragDrop_ColorString")

Domyślnie kursor zmieni się w trakcie operacji przeciągania i upuszczania, aby wskazać, jaki efekt spowoduje porzucenie danych. Możesz dostosować opinię podaną użytkownikowi przez obsługę <xref:System.Windows.UIElement.GiveFeedback> zdarzenia i ustawienie innego kursora.

## <a name="give-feedback-to-the-user"></a>Przekaż opinię użytkownikowi

1. Otwórz Circle.xaml.cs lub Circle. XAML. vb.

2. Dodaj następujące <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.GiveFeedback> zdarzenia.

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     To <xref:System.Windows.UIElement.OnGiveFeedback%2A> przesłonięcie wykonuje następujące zadania:

    - Sprawdza <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości, które są ustawione w programie <xref:System.Windows.UIElement.DragOver> obsługi zdarzeń upuszczania docelowej.

    - Ustawia niestandardowy kursor na podstawie <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości. Kursor ma na celu umożliwienie wizualnej opinii użytkownika o tym, jaki wpływ na dane zostaną porzucane.

3. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.

4. Przeciągnij jedną z kontrolek okręgu na panele, drugi okrąg i <xref:System.Windows.Controls.TextBox> . Zauważ, że kursory są teraz kursorami niestandardowymi, które zostały określone w <xref:System.Windows.UIElement.OnGiveFeedback%2A> przesłonięciu.

     ![Przeciąganie i upuszczanie za pomocą niestandardowych kursorów](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. Wybierz tekst `green` z <xref:System.Windows.Controls.TextBox> .

6. Przeciągnij `green` tekst do kontrolki okręgu. Zauważ, że domyślne kursory są wyświetlane, aby wskazać efekty operacji przeciągania i upuszczania. Kursor opinii jest zawsze ustawiany przez źródło przeciągania.

## <a name="implement-drop-target-events-in-the-user-control"></a>Implementowanie docelowych zdarzeń upuszczania w kontrolce użytkownika
 W tej sekcji określisz, że formant użytkownika jest obiektem docelowym upuszczania, Zastąp metody, które umożliwiają kontrolowanie użytkownika jako element docelowy upuszczania, i przetwarzanie danych, które zostały przez niego usunięte.

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Aby włączyć kontrolkę użytkownika jako element docelowy upuszczania

1. Otwórz Circle. XAML.

2. W tagu otwierającym <xref:System.Windows.Controls.UserControl> Dodaj <xref:System.Windows.UIElement.AllowDrop%2A> Właściwość i ustaw ją na `true` .

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<xref:System.Windows.UIElement.OnDrop%2A>Metoda jest wywoływana, gdy <xref:System.Windows.UIElement.AllowDrop%2A> Właściwość jest ustawiona na `true` , a dane ze źródła przeciągania są porzucane w kontrolce użytkownika koła. W tej metodzie przetwarzasz dane, które zostały porzucone i stosują dane do okręgu.

### <a name="to-process-the-dropped-data"></a>Aby przetworzyć opuszczone dane

1. Otwórz Circle.xaml.cs lub Circle. XAML. vb.

2. Dodaj następujące <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.Drop> zdarzenia.

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     To <xref:System.Windows.UIElement.OnDrop%2A> przesłonięcie wykonuje następujące zadania:

    - Używa <xref:System.Windows.DataObject.GetDataPresent%2A> metody do sprawdzenia, czy przeciągane dane zawierają obiekt ciągu.

    - Używa <xref:System.Windows.DataObject.GetData%2A> metody do wyodrębnienia danych ciągu, jeśli są obecne.

    - Używa <xref:System.Windows.Media.BrushConverter> do próby przekonwertowania ciągu na <xref:System.Windows.Media.Brush> .

    - Jeśli konwersja zakończy się pomyślnie, program zastosuje Pędzel do <xref:System.Windows.Shapes.Shape.Fill%2A> elementu <xref:System.Windows.Shapes.Ellipse> , który zapewnia interfejs użytkownika kontrolki Circle.

    - Oznacza <xref:System.Windows.UIElement.Drop> zdarzenie jako obsłużone. Należy oznaczyć zdarzenie upuszczania jako obsłużone, tak aby inne elementy, które odbierają to zdarzenie, wiedziały, że kontrolka użytkownika kółka ją obsłuży.

3. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.

4. Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox> .

5. Przeciągnij tekst do kontrolki Circle i upuść ją. Okrąg zmieni się z niebieski na zielony.

     ![Konwertuj ciąg na pędzel](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. Wpisz tekst `green` w <xref:System.Windows.Controls.TextBox> .

7. Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox> .

8. Przeciągnij go do kontrolki okręgu i upuść. Zauważ, że kursor zmieni się, aby wskazać, że porzucanie jest dozwolone, ale kolor koła nie zmienia się, ponieważ nie `gre` jest prawidłowym kolorem.

9. Przeciągnij wskaźnik myszy z zielonego kółka i upuść go w kontrolce niebieskiego okręgu. Okrąg zmieni się z niebieski na zielony. Zauważ, że kursor jest pokazywany, zależy od tego, czy <xref:System.Windows.Controls.TextBox> okrąg jest źródłem przeciągania.

Ustawienie <xref:System.Windows.UIElement.AllowDrop%2A> właściwości na `true` i przetwarzanie porzuconych danych jest wymagane do włączenia elementu jako miejsca docelowego upuszczania. Aby jednak zapewnić lepsze środowisko użytkownika, należy również obsłużyć <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragLeave> zdarzenia, i <xref:System.Windows.UIElement.DragOver> . W tych zdarzeniach można wykonać testy i przekazać użytkownikowi dodatkowe opinie przed usunięciem danych.

Gdy dane są przeciągane za pomocą okrągłej kontrolki użytkownika, formant powinien poinformować Źródło przeciągania, czy może przetwarzać dane, które są przeciągane. Jeśli formant nie wie, jak przetwarzać dane, powinna odmówić usunięcia. W tym celu należy obsłużyć <xref:System.Windows.UIElement.DragOver> zdarzenie i ustawić <xref:System.Windows.DragEventArgs.Effects%2A> Właściwość.

### <a name="to-verify-that-the-data-drop-is-allowed"></a>Aby sprawdzić, czy usuwanie danych jest dozwolone

1. Otwórz Circle.xaml.cs lub Circle. XAML. vb.

2. Dodaj następujące <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragOver> zdarzenia.

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     To <xref:System.Windows.UIElement.OnDragOver%2A> przesłonięcie wykonuje następujące zadania:

    - Ustawia <xref:System.Windows.DragEventArgs.Effects%2A> Właściwość na <xref:System.Windows.DragDropEffects.None> .

    - Wykonuje te same kontrole, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodzie, aby określić, czy formant użytkownika kółka może przetwarzać przeciągnięte dane.

    - Jeśli kontrolka użytkownika może przetwarzać dane, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> Właściwość na <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move> .

3. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.

4. Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox> .

5. Przeciągnij tekst do kontrolki okręgu. Zauważ, że kursor teraz zmienia się, aby wskazać, że upuszczenie nie jest dozwolone, ponieważ `gre` nie jest prawidłowym kolorem.

 Możesz bardziej usprawnić środowisko użytkownika, stosując podgląd operacji usuwania. W przypadku kontrolki użytkownika Circle można zastąpić <xref:System.Windows.UIElement.OnDragEnter%2A> <xref:System.Windows.UIElement.OnDragLeave%2A> metody i. Gdy dane są przeciągane nad formantem, bieżące tło <xref:System.Windows.Shapes.Shape.Fill%2A> jest zapisywane w zmiennej zastępczej. Ciąg jest następnie konwertowany na pędzel i zastosowany do, <xref:System.Windows.Shapes.Ellipse> który zapewnia interfejs użytkownika koła. Jeśli dane są przeciągane z okręgu bez porzucenia, oryginalna <xref:System.Windows.Shapes.Shape.Fill%2A> wartość zostanie ponownie zastosowana do okręgu.

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Aby wyświetlić podgląd efektów operacji przeciągania i upuszczania

1. Otwórz Circle.xaml.cs lub Circle. XAML. vb.

2. W klasie Circle Zadeklaruj zmienną prywatną <xref:System.Windows.Media.Brush> o nazwie `_previousFill` i zainicjuj ją w `null` .

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. Dodaj następujące <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragEnter> zdarzenia.

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     To <xref:System.Windows.UIElement.OnDragEnter%2A> przesłonięcie wykonuje następujące zadania:

    - Zapisuje <xref:System.Windows.Shapes.Shape.Fill%2A> Właściwość <xref:System.Windows.Shapes.Ellipse> w `_previousFill` zmiennej.

    - Wykonuje te same kontrole, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodzie, aby określić, czy dane mogą być konwertowane na <xref:System.Windows.Media.Brush> .

    - Jeśli dane są konwertowane na prawidłowe <xref:System.Windows.Media.Brush> , stosuje je do <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> .

4. Dodaj następujące <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragLeave> zdarzenia.

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     To <xref:System.Windows.UIElement.OnDragLeave%2A> przesłonięcie wykonuje następujące zadania:

    - Stosuje <xref:System.Windows.Media.Brush> zapisany w `_previousFill` zmiennej do <xref:System.Windows.Shapes.Shape.Fill%2A> elementu <xref:System.Windows.Shapes.Ellipse> , który zapewnia interfejs użytkownika dla kontrolki użytkownik kółka.

5. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.

6. Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox> .

7. Przeciągnij tekst nad kontrolką okręgu bez porzucania go. Okrąg zmieni się z niebieski na zielony.

     ![Podgląd efektów przeciągnięcia&#45;i&#45;operacji upuszczania](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. Przeciągnij tekst poza formant okręgu. Okrąg zmieni się z zielonej z powrotem na niebieską.

## <a name="enable-a-panel-to-receive-dropped-data"></a>Włącz panel do odbierania porzuconych danych

W tej sekcji włączasz panele obsługujące kontrolki użytkownika kółka, aby pełnić rolę obiektów docelowych dla przeciąganych danych. Zaimplementowano kod, który umożliwia przesuwanie okręgu z jednego panelu do drugiego lub tworzenie kopii kontrolki okręgu przez przytrzymanie klawisza **Ctrl** podczas przeciągania i upuszczania okręgu.

1. Otwórz MainWindow. XAML.

2. Jak pokazano w poniższym kodzie XAML, w każdej <xref:System.Windows.Controls.StackPanel> kontrolce Dodaj programy obsługi dla <xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop> zdarzeń i. Nazwij <xref:System.Windows.UIElement.DragOver> program obsługi zdarzeń, `panel_DragOver` a następnie nazwij <xref:System.Windows.UIElement.Drop> procedurę obsługi zdarzeń `panel_Drop` .

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. Otwórz MainWindows.xaml.cs lub MainWindow. XAML. vb.

4. Dodaj następujący kod dla <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń.

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     Ten <xref:System.Windows.UIElement.DragOver> program obsługi zdarzeń wykonuje następujące zadania:

    - Sprawdza, czy przeciągane dane zawierają dane "obiekt", które zostały spakowane w <xref:System.Windows.DataObject> przez okrągłą kontrolkę użytkownika i przechodzą w wywołaniu <xref:System.Windows.DragDrop.DoDragDrop%2A> .

    - Jeśli istnieją dane "Object", sprawdź, czy klawisz **Ctrl** został naciśnięty.

    - Po naciśnięciu klawisza **Ctrl** ustawia <xref:System.Windows.DragEventArgs.Effects%2A> Właściwość na <xref:System.Windows.DragDropEffects.Copy> . W przeciwnym razie ustaw <xref:System.Windows.DragEventArgs.Effects%2A> Właściwość na <xref:System.Windows.DragDropEffects.Move> .

5. Dodaj następujący kod dla <xref:System.Windows.UIElement.Drop> programu obsługi zdarzeń.

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     Ten <xref:System.Windows.UIElement.Drop> program obsługi zdarzeń wykonuje następujące zadania:

    - Sprawdza, czy <xref:System.Windows.UIElement.Drop> zdarzenie zostało już obsłużone. Na przykład, jeśli okrąg zostanie porzucony w innym okręgu, który obsługuje <xref:System.Windows.UIElement.Drop> zdarzenie, nie chcesz, aby panel, który zawiera okrąg, również go obsłużyć.

    - Jeśli <xref:System.Windows.UIElement.Drop> zdarzenie nie jest obsługiwane, sprawdza, czy klawisz **Ctrl** został naciśnięty.

    - Jeśli klawisz **Ctrl** zostanie wciśnięty <xref:System.Windows.UIElement.Drop> , program tworzy kopię kontrolki Circle i dodaje ją do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji <xref:System.Windows.Controls.StackPanel> .

    - Jeśli klawisz **Ctrl** nie zostanie wciśnięty, przenosi okrąg z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji jego panelu nadrzędnego do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu, w którym została porzucona.

    - Ustawia właściwość w taki sposób, <xref:System.Windows.DragEventArgs.Effects%2A> Aby powiadamiał metodę o tym, <xref:System.Windows.DragDrop.DoDragDrop%2A> czy operacja przenoszenia lub kopiowania została wykonana.

6. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.

7. Wybierz tekst `green` z <xref:System.Windows.Controls.TextBox> .

8. Przeciągnij tekst nad kontrolką okręgu i upuść go.

9. Przeciągnij kontrolkę Circle z lewego panelu do prawego panelu i upuść ją. Okrąg zostanie usunięty z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lewego panelu i dodany do kolekcji Children panelu po prawej stronie.

10. Przeciągnij kontrolkę Circle z panelu do drugiego panelu i upuść ją podczas naciskania klawisza **Ctrl** . Okrąg jest kopiowany, a kopia zostanie dodana do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu odbiorczego.

     ![Przeciąganie okręgu podczas naciskania klawisza CTRL](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>Zobacz także

- [Przegląd Przeciąganie i upuszczanie](drag-and-drop-overview.md)
