---
title: 'Wskazówki: powiązanie z danymi w aplikacjach hybrydowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 1bb38436049e338ab6033ae3b6370732a457d520
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794226"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Wskazówki: powiązanie z danymi w aplikacjach hybrydowych

Powiązanie źródła danych z kontrolką jest niezbędne do zapewnienia użytkownikom dostępu do danych źródłowych, niezależnie od tego, czy używasz Windows Forms, czy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W tym instruktażu pokazano, jak można używać powiązań danych w aplikacjach hybrydowych, które zawierają zarówno Windows Forms, jak i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu.

- Definiowanie szablonu danych.

- Określanie układu formularza.

- Określanie powiązań danych.

- Wyświetlanie danych przy użyciu funkcji międzyoperacyjności.

- Dodawanie źródła danych do projektu.

- Powiązanie ze źródłem danych.

Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [powiązanie danych w przykładowych aplikacjach hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159983).

Po zakończeniu będziesz mieć świadomość funkcji powiązań danych w aplikacjach hybrydowych.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Program Visual Studio.

- Dostęp do przykładowej bazy danych Northwind działającej na Microsoft SQL Server.

## <a name="creating-the-project"></a>Tworzenie projektu

### <a name="to-create-and-set-up-the-project"></a>Aby utworzyć i skonfigurować projekt

1. Utwórz projekt aplikacji WPF o nazwie `WPFWithWFAndDatabinding`.

2. W Eksplorator rozwiązań Dodaj odwołania do następujących zestawów.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Otwórz MainWindow. XAML w projektancie WPF.

4. W <xref:System.Windows.Window> elementu Dodaj następujące Windows Forms mapowania przestrzeni nazw.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Nadaj <xref:System.Windows.Controls.Grid> domyślnemu elementowi `mainGrid`, przypisując Właściwość <xref:System.Windows.FrameworkElement.Name%2A>.

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Definiowanie szablonu danych

Główna lista klientów jest wyświetlana w kontrolce <xref:System.Windows.Controls.ListBox>. Poniższy przykład kodu definiuje obiekt <xref:System.Windows.DataTemplate> o nazwie `ListItemsTemplate`, który kontroluje drzewo wizualne kontrolki <xref:System.Windows.Controls.ListBox>. Ta <xref:System.Windows.DataTemplate> jest przypisana do właściwości <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> kontrolki <xref:System.Windows.Controls.ListBox>.

### <a name="to-define-the-data-template"></a>Aby zdefiniować szablon danych

- Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Określanie układu formularza

Układ formularza jest definiowany przez siatkę z trzema wierszami i trzema kolumnami. w celu zidentyfikowania każdej kolumny w tabeli Customers są udostępniane <xref:System.Windows.Controls.Label> formanty.

### <a name="to-set-up-the-grid-layout"></a>Aby skonfigurować układ siatki

- Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Aby skonfigurować kontrolki etykiet

- Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Określanie powiązań danych

Główna lista klientów jest wyświetlana w kontrolce <xref:System.Windows.Controls.ListBox>. Dołączony `ListItemsTemplate` wiąże formant <xref:System.Windows.Controls.TextBlock> z bazą danych `ContactName`.

Szczegóły każdego rekordu klienta są wyświetlane w kilku kontrolkach <xref:System.Windows.Controls.TextBox>.

### <a name="to-specify-data-bindings"></a>Aby określić powiązania danych

- Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.

     Klasa <xref:System.Windows.Data.Binding> wiąże kontrolki <xref:System.Windows.Controls.TextBox> z odpowiednimi polami w bazie danych.

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Wyświetlanie danych przy użyciu funkcji międzyoperacyjnych

Zamówienia odpowiadające wybranemu klientowi są wyświetlane w kontrolce <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> o nazwie `dataGridView1`. Formant `dataGridView1` jest powiązany ze źródłem danych w pliku związanym z kodem. Formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> jest elementem nadrzędnym tej kontrolki Windows Forms.

### <a name="to-display-data-in-the-datagridview-control"></a>Aby wyświetlić dane w formancie DataGridView

- Skopiuj następujący kod XAML do deklaracji elementu <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Dodawanie źródła danych do projektu

Za pomocą programu Visual Studio można łatwo dodać źródło danych do projektu. Ta procedura dodaje zestaw danych o jednoznacznie określonym typie do projektu. Dodawane są również kilka innych klas pomocniczych, takich jak karty tabel dla każdej z wybranych tabel.

### <a name="to-add-the-data-source"></a>Aby dodać źródło danych

1. Z menu **dane** wybierz pozycję **Dodaj nowe źródło danych**.

2. W **Kreatorze konfiguracji źródła danych**Utwórz połączenie z bazą danych Northwind przy użyciu zestawu danych. Aby uzyskać więcej informacji, zobacz [jak: łączenie z danymi w bazie danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).

3. Po wyświetleniu monitu w **Kreatorze konfiguracji źródła danych**Zapisz parametry połączenia jako `NorthwindConnectionString`.

4. Po wyświetleniu monitu o wybranie obiektów bazy danych wybierz tabele `Customers` i `Orders` i nadaj nazwę wygenerowanego zestawu danych `NorthwindDataSet`.

## <a name="binding-to-the-data-source"></a>Powiązanie ze źródłem danych

Składnik <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> zapewnia jednolity interfejs dla źródła danych aplikacji. Powiązanie ze źródłem danych jest zaimplementowane w pliku związanym z kodem.

### <a name="to-bind-to-the-data-source"></a>Aby powiązać ze źródłem danych

1. Otwórz plik związany z kodem o nazwie MainWindow. XAML. vb lub MainWindow.xaml.cs.

2. Skopiuj następujący kod do definicji klasy `MainWindow`.

     Ten kod deklaruje składnik <xref:System.Windows.Forms.BindingSource> i skojarzone klasy pomocnika, które łączą się z bazą danych.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Skopiuj poniższy kod do konstruktora.

     Ten kod tworzy i inicjuje składnik <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. Open MainWindow.xaml.

5. W widoku widok Projekt lub XAML wybierz element <xref:System.Windows.Window>.

6. W okno Właściwości kliknij kartę **zdarzenia** .

7. Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.

8. Skopiuj następujący kod do programu obsługi zdarzeń <xref:System.Windows.FrameworkElement.Loaded>.

     Ten kod przypisuje składnik <xref:System.Windows.Forms.BindingSource> jako kontekst danych i wypełnia obiekty `Customers` i `Orders` kart.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Skopiuj następujący kod do definicji klasy `MainWindow`.

     Ta metoda obsługuje zdarzenie <xref:System.Windows.Data.CollectionView.CurrentChanged> i aktualizuje bieżący element powiązania danych.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przykład powiązania danych w aplikacjach hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159983)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
