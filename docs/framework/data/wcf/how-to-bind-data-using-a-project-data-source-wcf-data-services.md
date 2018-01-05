---
title: "Porady: wiązanie danych przy użyciu źródła danych projektu (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94ca7614e6df2d82216fa869309dff2da8eee634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Porady: wiązanie danych przy użyciu źródła danych projektu (usługi danych WCF)
Można utworzyć źródła danych, które są oparte na obiekty danych wygenerowanych w [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] aplikacji klienckiej. Podczas dodawania odwołania do usług danych przy użyciu **Dodaj odwołanie do usługi** okna dialogowego, wraz z klas danych wygenerowanego klienta utworzeniu źródła danych projektu. Jedno źródło danych jest tworzony dla każdego zestawu jednostek, usługa ujawnia danych. Możesz utworzyć formularze, które są wyświetlane dane z usługi przez przeciągnięcie tych elementów źródła danych z **źródeł danych** okna do projektanta. Te elementy stają się formanty, które są powiązane ze źródłem danych. Podczas wykonywania tego źródła danych jest powiązany z wystąpieniem <xref:System.Data.Services.Client.DataServiceCollection%601> klasy, która jest wypełniony obiektów, które są zwracane przez zapytanie do usługi danych. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Przykłady w tym temacie usługę Northwind przykładowych danych i dane klienta automatycznie wygenerowaną usługi klasy. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-use-a-project-data-source-in-a-wpf-window"></a>Aby używać źródła danych projektu w oknie WPF  
  
1.  W projekcie WPF Dodaj odwołanie do usługi danych Northwind. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie odwołania do danych usługi](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
2.  W **źródeł danych** okna, rozwiń węzeł `Customers` w węźle **NorthwindEntities** źródła danych projektu.  
  
3.  Kliknij przycisk **CustomerID** element, wybierz opcję **ComboBox** z listy, a następnie przeciągnij **CustomerID** elementu z **klientów** węzła Projektant.  
  
     Spowoduje to utworzenie następujących elementów obiektu w pliku XAML w oknie:  
  
    -   A <xref:System.Windows.Data.CollectionViewSource> elementu o nazwie `customersViewSource`. <xref:System.Windows.FrameworkElement.DataContext%2A> Właściwość najwyższego poziomu <xref:System.Windows.Controls.Grid> element obiektu jest ustawiony na tym nowy <xref:System.Windows.Data.CollectionViewSource>.  
  
    -   Z danymi <xref:System.Windows.Controls.ComboBox> o nazwie `CustomerID`.  
  
    -   A <xref:System.Windows.Controls.Label>.  
  
4.  Przeciągnij **zamówień** właściwości nawigacji do projektanta.  
  
     Spowoduje to utworzenie następujących elementów dodatkowych obiektów w pliku XAML w oknie:  
  
    -   Drugi <xref:System.Windows.Data.CollectionViewSource> elementu o nazwie `customersOrdersViewSource`, którego źródłem jest `customerViewSource`.  
  
    -   Z danymi <xref:System.Windows.Controls.DataGrid> formantu o nazwie `ordersDataGrid`.  
  
5.  (Opcjonalnie) Przeciągnij dodatkowe elementy z **klientów** węzła do projektanta.  
  
6.  Otwórz stronę kodu formularza i dodaj następującą `using` instrukcje (`Imports` w języku Visual Basic):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]  
  
7.  W klasie częściowej definiuje formularza, Dodaj następujący kod, który tworzy <xref:System.Data.Objects.ObjectContext> wystąpienia i definiuje `customerID` stałej.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]  
  
8.  W Projektancie wybierz okno.  
  
    > [!NOTE]
    >  Upewnij się, wybierz okno, a nie zawartości, która znajduje się w oknie Wybieranie. Jeśli wybrano okna, **nazwa** pole tekstowe w górnej części **właściwości** okno powinno zawierać nazwę okna.  
  
9. W **właściwości** wybierz **zdarzenia** przycisku.  
  
10. Znajdź **Loaded** zdarzeń, a następnie kliknij dwukrotnie plik listy rozwijanej obok tego zdarzenia.  
  
     Program Visual Studio otworzy plik CodeBehind dla okna i generuje <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.  
  
11. W nowo utworzonej <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń, skopiuj i wklej poniższy kod.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]  
  
12. Ten kod tworzy wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601> dla `Customers` typ oparty na wykonanie zapytania LINQ, która zwraca <xref:System.Collections.Generic.IEnumerable%601> z `Customers` wraz z powiązanych `Orders` obiektów z usług danych Northwind i wiąże go `customersViewSource`.  
  
### <a name="to-use-a-project-data-source-in-a-windows-form"></a>Aby używać źródła danych projektu w formularzu systemu Windows  
  
1.  W **źródeł danych** okna, rozwiń węzeł **klientów** w węźle **NorthwindEntities** źródła danych projektu.  
  
2.  Kliknij przycisk **CustomerID** element, wybierz opcję **ComboBox** z listy, a następnie przeciągnij **CustomerID** elementu z **klientów** węzła Projektant.  
  
     Spowoduje to utworzenie następujących kontrolek w formularzu:  
  
    -   Wystąpienie <xref:System.Windows.Forms.BindingSource> o nazwie `customersBindingSource`.  
  
    -   Wystąpienie <xref:System.Windows.Forms.BindingNavigator> o nazwie `customersBindingNavigator`. Można usunąć tego formantu, ponieważ nie będą potrzebne.  
  
    -   Z danymi <xref:System.Windows.Forms.ComboBox> o nazwie `CustomerID`.  
  
    -   A <xref:System.Windows.Forms.Label>.  
  
3.  Przeciągnij **zamówień** właściwości nawigacji do formularza.  
  
4.  Spowoduje to utworzenie `ordersBindingSource` sterować za pomocą <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości formantu ustawioną `customersBindingSource` i <xref:System.Windows.Forms.BindingSource.DataMember%2A> ustawioną właściwość `Customers`. Tworzy również `ordersDataGridView` formantu powiązanego z danymi w formularzu, wraz z odpowiednio zatytułowana label — formant.  
  
5.  (Opcjonalnie) Przeciągnij dodatkowe elementy z **klientów** węzła do projektanta.  
  
6.  Otwórz stronę kodu formularza i dodaj następującą `using` instrukcje (`Imports` w języku Visual Basic):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]  
  
7.  W klasie częściowej definiuje formularza, Dodaj następujący kod, który tworzy <xref:System.Data.Objects.ObjectContext> wystąpienia i definiuje `customerID` stałej.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]  
  
8.  Projektant formularzy kliknij dwukrotnie formularza.  
  
     To spowoduje otwarcie strony kodu formularza i tworzy metodę, która obsługuje `Load` zdarzenie dla formularza.  
  
9. W `Load` program obsługi zdarzeń, skopiuj i wklej poniższy kod.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]  
  
10. Ten kod tworzy wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601> dla `Customers` typ oparty na wykonanie <xref:System.Data.Services.Client.DataServiceQuery%601> zwracającą <xref:System.Collections.Generic.IEnumerable%601> z `Customers` z Northwind danych usługi i wiąże go do `customersBindingSource`.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Instrukcje: Wiązanie danych do elementów systemu Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
