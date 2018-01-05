---
title: "Wskazówki: powiązanie z danymi w aplikacjach hybrydowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3afc0d2eabb7554d64a40863b182a6edefe169f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Wskazówki: powiązanie z danymi w aplikacjach hybrydowych
Powiązanie z formantem źródła danych jest istotne dla zapewnia użytkownikom dostęp do danych, czy używasz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W tym przewodniku przedstawiono używania wiązania z danymi w aplikacjach hybrydowych, które obejmują zarówno [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu.  
  
-   Definiowanie szablonu danych.  
  
-   Określenie układu formularza.  
  
-   Określanie powiązań danych.  
  
-   Wyświetlanie danych przy użyciu współdziałanie.  
  
-   Dodawanie źródła danych do projektu.  
  
-   Powiązania ze źródłem danych.  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [powiązania danych w przykładowej aplikacji hybrydowych](http://go.microsoft.com/fwlink/?LinkID=159983).  
  
 Po ukończeniu będzie mieć zrozumienia funkcji wiązania danych w aplikacji hybrydowych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].,  
  
-   Dostęp do przykładowej bazy danych Northwind uruchomione przez program Microsoft SQL Server.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Tworzenie i konfigurowanie projektu  
  
1.  Utwórz projekt aplikacji WPF o nazwie `WPFWithWFAndDatabinding`.  
  
2.  W Eksploratorze rozwiązań Dodaj odwołania do następujących zestawów.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Otwórz MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  W <xref:System.Windows.Window> elementu, Dodaj następujący [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapowania przestrzeni nazw.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Nazwa domyślna <xref:System.Windows.Controls.Grid> elementu `mainGrid` przypisując <xref:System.Windows.FrameworkElement.Name%2A> właściwości.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Definiowanie szablonu danych  
 Listę wzorcową klientów jest wyświetlany w <xref:System.Windows.Controls.ListBox> formantu. Poniższy przykładowy kod definiuje <xref:System.Windows.DataTemplate> obiektu o nazwie `ListItemsTemplate` steruje drzewie wizualnym <xref:System.Windows.Controls.ListBox> formantu. To <xref:System.Windows.DataTemplate> jest przypisany do <xref:System.Windows.Controls.ListBox> formantu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości.  
  
#### <a name="to-define-the-data-template"></a>Aby zdefiniować szablon danych  
  
-   Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Określenie układu formularza  
 Układu formularza jest zdefiniowana przez siatkę z trzy wiersze i trzy kolumny. <xref:System.Windows.Controls.Label>Formanty są dostarczane do identyfikowania każdej kolumny w tabeli Klienci.  
  
#### <a name="to-set-up-the-grid-layout"></a>Aby skonfigurować układ siatki  
  
-   Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Aby skonfigurować formantów etykiet  
  
-   Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Określanie powiązania danych  
 Listę wzorcową klientów jest wyświetlany w <xref:System.Windows.Controls.ListBox> formantu. Dołączony `ListItemsTemplate` wiąże <xref:System.Windows.Controls.TextBlock> formant `ContactName` pole z bazy danych.  
  
 Szczegóły każdego rekordu klienta są wyświetlane w kilku <xref:System.Windows.Controls.TextBox> kontrolki.  
  
#### <a name="to-specify-data-bindings"></a>Aby określić powiązania danych  
  
-   Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.  
  
     <xref:System.Windows.Data.Binding> Klasy wiązania <xref:System.Windows.Controls.TextBox> formanty do odpowiednich pól w bazie danych.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Wyświetlanie danych przy użyciu współdziałanie  
 Zamówienia odpowiadającego danego odbiorcy są wyświetlane w <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> formantu o nazwie `dataGridView1`. `dataGridView1` Kontrolka jest powiązana ze źródłem danych w pliku CodeBehind. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolka jest elementem nadrzędnym [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>Aby wyświetlić dane w formancie DataGridView  
  
-   Skopiuj następujące XAML do <xref:System.Windows.Controls.Grid> deklaracji elementu.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Dodawanie źródła danych do projektu  
 Z [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], można łatwo dodać źródło danych do projektu. Ta procedura dodaje silnie typizowanego zestaw danych do projektu. Dodano również kilka innych klas pomocy technicznej, takie jak karty tabeli dla wszystkich wybranych tabel.  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
1.  Z **danych** menu, wybierz opcję **Dodaj nowe źródło danych**.  
  
2.  W **Kreator konfiguracji źródła danych**, Utwórz połączenie z bazą danych Northwind przy użyciu zestawu danych. Aby uzyskać więcej informacji, zobacz [porady: łączenie z danymi w bazie danych](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).  
  
3.  Po wyświetleniu monitu przez **Kreator konfiguracji źródła danych**, Zapisz parametry połączenia jako `NorthwindConnectionString`.  
  
4.  Po wyświetleniu monitu, aby wybrać obiekty bazy danych, wybierz `Customers` i `Orders` tabel i nazwę wygenerowanego zestawu danych `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Powiązania ze źródłem danych  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Stanowi ujednolicony interfejs dla źródła danych aplikacji. Powiązania ze źródłem danych jest zaimplementowana w pliku CodeBehind.  
  
#### <a name="to-bind-to-the-data-source"></a>Aby powiązać ze źródłem danych  
  
1.  Otwórz plik CodeBehind, który jest nazwane MainWindow.xaml.vb lub MainWindow.xaml.cs.  
  
2.  Skopiuj następujący kod do `MainWindow` definicji klasy.  
  
     Ten kod deklaruje <xref:System.Windows.Forms.BindingSource> składnika i klasy pomocnicze skojarzony, które połączenia z bazą danych.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  Skopiuj następujący kod do konstruktora.  
  
     Ten kod tworzy i inicjuje <xref:System.Windows.Forms.BindingSource> składnika.  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  Otwórz MainWindow.xaml.  
  
5.  W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.  
  
6.  Kliknij w oknie właściwości **zdarzenia** kartę.  
  
7.  Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.  
  
8.  Skopiuj następujący kod do <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.  
  
     Ten kod przypisuje <xref:System.Windows.Forms.BindingSource> składnika jako kontekst danych i wypełnienie `Customers` i `Orders` obiektów karty.  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. Skopiuj następujący kod do `MainWindow` definicji klasy.  
  
     Ta metoda obsługuje <xref:System.Windows.Data.CollectionView.CurrentChanged> zdarzeń i aktualizuje bieżącego elementu powiązania danych.  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Wiązanie danych w przykładowej aplikacji hybrydowych](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
