---
title: 'Przewodnik: wiązanie z danymi w aplikacjach hybrydowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: ef5f14cdbecab8bc780cb7b2a642429970a25316
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972278"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Przewodnik: wiązanie z danymi w aplikacjach hybrydowych

Powiązanie źródła danych z kontrolką jest niezbędne do zapewnienia użytkownikom dostępu do danych źródłowych, niezależnie od tego, czy używasz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], czy też. W tym instruktażu pokazano, jak można używać powiązań danych w aplikacjach hybrydowych [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] które zawierają zarówno formanty, jak i.

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

3. Otwórz MainWindow. XAML w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

4. W elemencie Dodaj następujące [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowanie przestrzeni nazw. <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Nadaj nazwę <xref:System.Windows.Controls.Grid> elementowi `mainGrid` domyślnemu, <xref:System.Windows.FrameworkElement.Name%2A> przypisując właściwość.

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Definiowanie szablonu danych

Główna lista klientów jest wyświetlana w <xref:System.Windows.Controls.ListBox> formancie. Poniższy przykład kodu definiuje <xref:System.Windows.DataTemplate> obiekt o nazwie `ListItemsTemplate` kontrolujący drzewo <xref:System.Windows.Controls.ListBox> wizualizacji formantu. Jest <xref:System.Windows.DataTemplate> to przypisane <xref:System.Windows.Controls.ListBox> do <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości kontrolki.

### <a name="to-define-the-data-template"></a>Aby zdefiniować szablon danych

- Skopiuj następujący kod XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Określanie układu formularza

Układ formularza jest definiowany przez siatkę z trzema wierszami i trzema kolumnami. <xref:System.Windows.Controls.Label>dostępne są formanty umożliwiające zidentyfikowanie każdej kolumny w tabeli Customers.

### <a name="to-set-up-the-grid-layout"></a>Aby skonfigurować układ siatki

- Skopiuj następujący kod XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Aby skonfigurować kontrolki etykiet

- Skopiuj następujący kod XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Określanie powiązań danych

Główna lista klientów jest wyświetlana w <xref:System.Windows.Controls.ListBox> formancie. Dołączona `ListItemsTemplate` wartość wiąże <xref:System.Windows.Controls.TextBlock> formant `ContactName` z polem z bazy danych.

Szczegóły każdego rekordu klienta są wyświetlane w kilku <xref:System.Windows.Controls.TextBox> kontrolkach.

### <a name="to-specify-data-bindings"></a>Aby określić powiązania danych

- Skopiuj następujący kod XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.

     Klasa wiąże <xref:System.Windows.Controls.TextBox> kontrolki z odpowiednimi polami w bazie danych. <xref:System.Windows.Data.Binding>

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Wyświetlanie danych przy użyciu funkcji międzyoperacyjnych

Zamówienia odpowiadające wybranemu klientowi są wyświetlane w <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> formancie o nazwie. `dataGridView1` `dataGridView1` Formant jest powiązany ze źródłem danych w pliku związanym z kodem. Formant jest elementem nadrzędnym tej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

### <a name="to-display-data-in-the-datagridview-control"></a>Aby wyświetlić dane w formancie DataGridView

- Skopiuj następujący kod XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Dodawanie źródła danych do projektu

Za pomocą programu Visual Studio można łatwo dodać źródło danych do projektu. Ta procedura dodaje zestaw danych o jednoznacznie określonym typie do projektu. Dodawane są również kilka innych klas pomocniczych, takich jak karty tabel dla każdej z wybranych tabel.

### <a name="to-add-the-data-source"></a>Aby dodać źródło danych

1. Z menu **dane** wybierz pozycję **Dodaj nowe źródło danych**.

2. W **Kreatorze konfiguracji źródła danych**Utwórz połączenie z bazą danych Northwind przy użyciu zestawu danych. Aby uzyskać więcej informacji, zobacz [jak: Nawiąż połączenie z danymi w](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))bazie danych.

3. Po wyświetleniu monitu w **Kreatorze konfiguracji źródła danych**Zapisz parametry połączenia jako `NorthwindConnectionString`.

4. Po wyświetleniu monitu o wybranie obiektów bazy danych wybierz `Customers` tabele i `Orders` i nazwij wygenerowany zestaw `NorthwindDataSet`danych.

## <a name="binding-to-the-data-source"></a>Powiązanie ze źródłem danych

<xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Składnik zapewnia jednolity interfejs dla źródła danych aplikacji. Powiązanie ze źródłem danych jest zaimplementowane w pliku związanym z kodem.

### <a name="to-bind-to-the-data-source"></a>Aby powiązać ze źródłem danych

1. Otwórz plik związany z kodem o nazwie MainWindow. XAML. vb lub MainWindow.xaml.cs.

2. Skopiuj poniższy kod do `MainWindow` definicji klasy.

     Ten kod deklaruje <xref:System.Windows.Forms.BindingSource> składnik i skojarzone z nią klasy pomocnika, które łączą się z bazą danych.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Skopiuj poniższy kod do konstruktora.

     Ten kod tworzy i inicjuje <xref:System.Windows.Forms.BindingSource> składnik.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. Open MainWindow.xaml.

5. W widoku Widok Projekt lub XAML wybierz <xref:System.Windows.Window> element.

6. W okno Właściwości kliknij kartę **zdarzenia** .

7. Kliknij <xref:System.Windows.FrameworkElement.Loaded> dwukrotnie zdarzenie.

8. Skopiuj następujący kod do <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.

     Ten kod przypisuje <xref:System.Windows.Forms.BindingSource> składnik jako kontekst danych i wypełnia `Customers` `Orders` obiekty adapterów.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Skopiuj poniższy kod do `MainWindow` definicji klasy.

     Ta metoda obsługuje <xref:System.Windows.Data.CollectionView.CurrentChanged> zdarzenie i aktualizuje bieżący element powiązania danych.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przykład powiązania danych w aplikacjach hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159983)
- [Przewodnik: Hostowanie złożonego formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: Hostowanie złożonego formantu WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
