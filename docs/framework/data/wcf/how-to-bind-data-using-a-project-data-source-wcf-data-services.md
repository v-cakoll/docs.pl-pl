---
title: 'Instrukcje: Wiązanie danych przy użyciu źródła danych projektu (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: e1111077a407dc32475976b15ff71170978e3184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765508"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Instrukcje: Wiązanie danych przy użyciu źródła danych projektu (WCF Data Services)

Można utworzyć źródła danych, które są oparte na obiektach wygenerowane dane w aplikacji klienta usługi danych WCF. Po dodaniu odwołania do usługi danych przy użyciu **Dodaj odwołanie do usługi** okno dialogowe, tworzone jest źródło danych projektu wraz z klas danych wygenerowanego klienta. Jedno źródło danych jest tworzony dla każdego zestawu jednostek usługi ujawnia w danych. Możesz tworzyć formularze, które wyświetlają dane z usługi, przeciągając elementy w tych źródeł danych, z **źródeł danych** okna do projektanta. Te elementy stają się formantów, które są powiązane ze źródłem danych. W czasie wykonywania tego źródła danych jest powiązany do wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> klasy, która jest zajęta przez obiekty, które są zwracane przez zapytanie do usługi danych. Aby uzyskać więcej informacji, zobacz [powiązanie danych z kontrolkami](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).

 Przykłady w tym temacie usługi Northwind przykładowych danych i dane klienta automatycznie wygenerowany usługi klas. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="use-a-project-data-source-in-a-wpf-window"></a>Korzystanie ze źródła danych projektu w oknie WPF

1. W programie Visual Studio w projekcie WPF, Dodaj odwołanie do usługi danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).

2. W **źródeł danych** okna, rozwiń węzeł `Customers` w węźle **NorthwindEntities** źródła danych projektu.

3. Kliknij przycisk **CustomerID** element i wybierz pozycję **ComboBox** z listy, a następnie przeciągnij **CustomerID** elementu z **klientów** węzła Projektant.

     Spowoduje to utworzenie następujących elementów obiektu w pliku XAML dla okna:

    - A <xref:System.Windows.Data.CollectionViewSource> elementu o nazwie `customersViewSource`. <xref:System.Windows.FrameworkElement.DataContext%2A> Właściwości najwyższego poziomu <xref:System.Windows.Controls.Grid> element obiektu jest ustawiona na tym nowy <xref:System.Windows.Data.CollectionViewSource>.

    - Powiązane z danymi <xref:System.Windows.Controls.ComboBox> o nazwie `CustomerID`.

    - A <xref:System.Windows.Controls.Label>.

4. Przeciągnij **zamówienia** właściwość nawigacji do projektanta.

     Spowoduje to utworzenie następujących elementów dodatkowych obiektu w pliku XAML dla okna:

    - Sekundy <xref:System.Windows.Data.CollectionViewSource> elementu o nazwie `customersOrdersViewSource`, której źródłem jest `customerViewSource`.

    - Powiązane z danymi <xref:System.Windows.Controls.DataGrid> formantu o nazwie `ordersDataGrid`.

5. (Opcjonalnie) Przeciągnij dodatkowe elementy z **klientów** węzła do projektanta.

6. Otwórz stronę kodową dla formularza i Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. W klasie częściowej, który definiuje formularza, Dodaj następujący kod, który tworzy <xref:System.Data.Objects.ObjectContext> wystąpień i umożliwia zdefiniowanie `customerID` stałej.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. W Projektancie wybierz okno.

    > [!NOTE]
    > Upewnij się, wybierz okno, a nie wybierania zawartości, który znajduje się w oknie. Jeśli okno jest zaznaczone, **nazwa** polu tekstowym w górnej części **właściwości** okna powinien zawierać nazwę okna.

9. W **właściwości** wybierz **zdarzenia** przycisku.

10. Znajdź **Loaded** zdarzeń, a następnie kliknij dwukrotnie pozycję z listy rozwijanej liście obok tego zdarzenia.

     Visual Studio otwiera plik CodeBehind dla okna i generuje <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.

11. W nowo utworzonej <xref:System.Windows.FrameworkElement.Loaded> procedura obsługi zdarzeń, skopiuj i wklej następujący kod.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Ten kod tworzy wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601> dla `Customers` oparty na wykonanie zapytania LINQ, która zwraca typ <xref:System.Collections.Generic.IEnumerable%601> z `Customers` wraz z powiązanych `Orders` obiektów z usługi danych Northwind i wiąże go `customersViewSource`.

## <a name="use-a-project-data-source-in-a-windows-form"></a>Korzystanie ze źródła danych projektu w formularzu Windows

1. W **źródeł danych** okna, rozwiń węzeł **klientów** w węźle **NorthwindEntities** źródła danych projektu.

2. Kliknij przycisk **CustomerID** element i wybierz pozycję **ComboBox** z listy, a następnie przeciągnij **CustomerID** elementu z **klientów** węzła Projektant.

     Spowoduje to utworzenie następujących formantów na formularzu:

    - Wystąpienie <xref:System.Windows.Forms.BindingSource> o nazwie `customersBindingSource`.

    - Wystąpienie <xref:System.Windows.Forms.BindingNavigator> o nazwie `customersBindingNavigator`. Można usunąć tej kontrolki, ponieważ nie będą potrzebne.

    - Powiązane z danymi <xref:System.Windows.Forms.ComboBox> o nazwie `CustomerID`.

    - A <xref:System.Windows.Forms.Label>.

3. Przeciągnij **zamówienia** właściwość nawigacji do formularza.

4. Spowoduje to utworzenie `ordersBindingSource` kontrolką <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości formantu równa `customersBindingSource` i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwością `Customers`. Tworzy również `ordersDataGridView` kontrolki powiązania danych w formularzu, wraz z kontrolkę etykiety odpowiednio nazwanych.

5. (Opcjonalnie) Przeciągnij dodatkowe elementy z **klientów** węzła do projektanta.

6. Otwórz stronę kodową dla formularza i Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. W klasie częściowej, który definiuje formularza, Dodaj następujący kod, który tworzy <xref:System.Data.Objects.ObjectContext> wystąpień i umożliwia zdefiniowanie `customerID` stałej.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. W Projektancie formularza kliknij dwukrotnie formularz.

     To otwiera stronę kodową dla formularza i tworzy metodę, która obsługuje `Load` zdarzenie dla formularza.

9. W `Load` procedura obsługi zdarzeń, skopiuj i wklej następujący kod.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. Ten kod tworzy wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601> dla `Customers` typ oparty na wykonanie <xref:System.Data.Services.Client.DataServiceQuery%601> zwracającego <xref:System.Collections.Generic.IEnumerable%601> z `Customers` z Northwind danych usługi i wiąże go do `customersBindingSource`.

## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Instrukcje: Powiąż dane z programu Windows Presentation Foundation elementów](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
