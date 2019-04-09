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
ms.openlocfilehash: d497dfd5580f1d2741e0edafa86e9dd39ec374ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191994"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Przewodnik: wiązanie z danymi w aplikacjach hybrydowych
Powiązanie źródła danych z kontrolką ma zasadnicze znaczenie dla zapewniając użytkownikom dostęp do danych bazowych, czy używasz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W tym instruktażu przedstawiono sposób korzystania powiązanie danych w aplikacjach hybrydowych, które zawierają zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu.  
  
-   Definiowanie szablonu danych.  
  
-   Określanie układu formularza.  
  
-   Określanie powiązania danych.  
  
-   Wyświetlanie danych za pomocą międzyoperacyjności.  
  
-   Dodawanie źródła danych do projektu.  
  
-   Powiązania ze źródłem danych.  
  
 Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [powiązanie danych w przykładowej aplikacji hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159983).  
  
 Gdy skończysz, konieczne będzie zrozumienie funkcji wiązania danych w aplikacjach hybrydowych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Program Visual Studio.  
  
-   Dostęp do przykładowej bazy danych Northwind uruchomiony program Microsoft SQL Server.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Aby utworzyć i skonfigurować projekt  
  
1.  Utwórz projekt aplikacji WPF, o nazwie `WPFWithWFAndDatabinding`.  
  
2.  W Eksploratorze rozwiązań należy dodać odwołania do następujących zestawów.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Otwieranie pliku MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  W <xref:System.Windows.Window> elementu, Dodaj następujący kod [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowania przestrzeni nazw.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Nazwa domyślna <xref:System.Windows.Controls.Grid> elementu `mainGrid` , przypisując <xref:System.Windows.FrameworkElement.Name%2A> właściwości.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Definiowanie szablonu danych  
 Zostanie wyświetlona lista wzorca odbiorców, w <xref:System.Windows.Controls.ListBox> kontroli. Poniższy przykład kodu przedstawia <xref:System.Windows.DataTemplate> obiektu o nazwie `ListItemsTemplate` sterującą drzewie wizualnym <xref:System.Windows.Controls.ListBox> kontroli. To <xref:System.Windows.DataTemplate> jest przypisany do <xref:System.Windows.Controls.ListBox> kontrolki <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości.  
  
#### <a name="to-define-the-data-template"></a>Aby zdefiniować szablon danych  
  
-   Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Określanie układu formularza  
 Układ formularza jest definiowany przez siatka zawierająca trzy wiersze i trzy kolumny. <xref:System.Windows.Controls.Label> Dzięki kontrolkom do identyfikowania każdej kolumny w tabeli Klienci.  
  
#### <a name="to-set-up-the-grid-layout"></a>Aby zdefiniować układ siatki  
  
-   Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Aby skonfigurować formantów etykiet  
  
-   Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Określanie powiązania danych  
 Zostanie wyświetlona lista wzorca odbiorców, w <xref:System.Windows.Controls.ListBox> kontroli. Dołączony `ListItemsTemplate` wiąże <xref:System.Windows.Controls.TextBlock> kontrolę `ContactName` pola z bazy danych.  
  
 Szczegóły poszczególnych rekordów klientów są wyświetlane w kilku <xref:System.Windows.Controls.TextBox> kontrolki.  
  
#### <a name="to-specify-data-bindings"></a>Aby określić powiązanie danych  
  
-   Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.  
  
     <xref:System.Windows.Data.Binding> Klasy powiązań <xref:System.Windows.Controls.TextBox> formanty do odpowiednich pól w bazie danych.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Wyświetlanie danych za pomocą międzyoperacyjności  
 Zamówienia odpowiadający wybranego klienta są wyświetlane w <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> formantu o nazwie `dataGridView1`. `dataGridView1` Kontrolka jest powiązana ze źródłem danych w pliku związanym z kodem. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> formant jest elementem nadrzędnym [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>Wyświetlanie danych w formancie DataGridView  
  
-   Skopiuj poniższy XAML do <xref:System.Windows.Controls.Grid> deklaracja elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Dodawanie źródła danych do projektu  
 Za pomocą programu Visual Studio można łatwo dodać źródło danych do projektu. Ta procedura dodaje silnie typizowany zestaw danych do projektu. Dodano także kilka innych klas pomocy technicznej, takie jak adapterów tabel dla każdej wybranej tabeli.  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
1.  Z **danych** menu, wybierz opcję **Dodaj nowe źródło danych**.  
  
2.  W **Kreatora konfiguracji źródła danych**, Utwórz połączenie z bazą danych Northwind za pomocą zestawu danych. Aby uzyskać więcej informacji, zobacz [jak: Łączenie z danymi w bazie danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).  
  
3.  Po wyświetleniu monitu przez **Kreatora konfiguracji źródła danych**, Zapisz parametry połączenia jako `NorthwindConnectionString`.  
  
4.  Po wyświetleniu monitu, aby wybrać obiekty bazy danych, wybierz `Customers` i `Orders` tabel i nazwę wygenerowanego zestawu danych `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Powiązania ze źródłem danych  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Składnik zapewnia ujednolicony interfejs dla źródła danych aplikacji. Powiązania ze źródłem danych jest zaimplementowana w pliku związanym z kodem.  
  
#### <a name="to-bind-to-the-data-source"></a>Aby powiązać ze źródłem danych  
  
1.  Otwórz plik związany z kodem, który nosi nazwę pliku MainWindow.xaml.vb lub MainWindow.xaml.cs.  
  
2.  Skopiuj następujący kod do `MainWindow` definicji klasy.  
  
     Ten kod deklaruje <xref:System.Windows.Forms.BindingSource> składników i klas pomocniczych skojarzone, łączących się z bazą danych.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3.  Skopiuj następujący kod do konstruktora.

     Ten kod tworzy i inicjuje <xref:System.Windows.Forms.BindingSource> składnika.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4.  Open MainWindow.xaml.

5.  W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.

6.  W oknie dialogowym właściwości kliknij **zdarzenia** kartę.

7.  Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.

8.  Skopiuj następujący kod do <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.

     Ten kod przypisuje <xref:System.Windows.Forms.BindingSource> składnika, ponieważ kontekst danych i wypełnienie `Customers` i `Orders` obiektów karty.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Skopiuj następujący kod do `MainWindow` definicji klasy.

     Ta metoda obsługuje <xref:System.Windows.Data.CollectionView.CurrentChanged> zdarzeń i aktualizacji bieżący element powiązania danych.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Powiązywanie danych w przykładowej aplikacji hybrydowych](https://go.microsoft.com/fwlink/?LinkID=159983)
- [Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hostowanie kontrolki złożonej WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
