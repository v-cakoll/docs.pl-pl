---
title: 'Instrukcje: Powiązywanie danych przy użyciu źródła danych projektu (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 85d5974f43349d91d56a1ab41b314521a6ee7348
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780162"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Instrukcje: Powiązywanie danych przy użyciu źródła danych projektu (Usługi danych programu WCF)

Możesz tworzyć źródła danych, które są oparte na wygenerowanych obiektach danych w aplikacji klienckiej Usługi danych programu WCF. Po dodaniu odwołania do usługi danych przy użyciu okna dialogowego **Dodaj odwołanie do usługi** , tworzone jest źródło danych projektu wraz z wygenerowanymi klasami danych klienta. Jedno źródło danych jest tworzone dla każdego zestawu jednostek, który jest udostępniany przez usługę danych. Można tworzyć formularze, które wyświetlają dane z usługi, przeciągając te elementy źródła danych z okna **źródła danych** do projektanta. Elementy te stają się kontrolkami, które są powiązane ze źródłem danych. Podczas wykonywania to źródło danych jest powiązane z wystąpieniem <xref:System.Data.Services.Client.DataServiceCollection%601> klasy, która jest wypełniana obiektami, które są zwracane przez zapytanie do usługi danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie danych z kontrolkami](binding-data-to-controls-wcf-data-services.md).

 Przykłady w tym temacie wykorzystują przykładową usługę danych Northwind i automatycznie wygenerowaną klasę usługi danych klienta. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).

## <a name="use-a-project-data-source-in-a-wpf-window"></a>Używanie źródła danych projektu w oknie WPF

1. W programie Visual Studio, w projekcie WPF, Dodaj odwołanie do usługi danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie](how-to-add-a-data-service-reference-wcf-data-services.md)do usługi danych.

2. W oknie **źródła danych** rozwiń `Customers` węzeł w źródle danych projektu **NorthwindEntities** .

3. Kliknij element **CustomerID** , wybierz z listy pole **kombi** i przeciągnij element **IDKlienta** z węzła **Customers** do projektanta.

     Spowoduje to utworzenie następujących elementów obiektów w pliku XAML dla okna:

    - Element o nazwie `customersViewSource`. <xref:System.Windows.Data.CollectionViewSource> Właściwość elementu najwyższego poziomu <xref:System.Windows.Controls.Grid> jest ustawiona na ten nowy <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.FrameworkElement.DataContext%2A>

    - Powiązane <xref:System.Windows.Controls.ComboBox> z danymi nazwy `CustomerID`.

    - A <xref:System.Windows.Controls.Label>.

4. Przeciągnij właściwość nawigacji **Orders** do projektanta.

     Spowoduje to utworzenie następujących elementów dodatkowych obiektów w pliku XAML dla okna:

    - Drugi <xref:System.Windows.Data.CollectionViewSource> element o nazwie `customersOrdersViewSource`, którego `customerViewSource`źródłem jest.

    - Formant powiązany <xref:System.Windows.Controls.DataGrid> z danymi o nazwie `ordersDataGrid`.

5. Obowiązkowe Przeciągnij dodatkowe elementy z węzła **Customers** do projektanta.

6. Otwórz stronę kodową formularza i Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. W klasie częściowej, która definiuje formularz, Dodaj następujący kod, który tworzy <xref:System.Data.Objects.ObjectContext> wystąpienie i `customerID` definiuje stałą.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. W Projektancie wybierz okno.

    > [!NOTE]
    > Upewnij się, że wybierasz samo okno, a nie zaznaczasz zawartość znajdującą się w oknie. Jeśli okno jest zaznaczone, pole tekstowe **Nazwa** znajdujące się w górnej części okna **Właściwości** powinno zawierać nazwę okna.

9. W oknie **Właściwości** wybierz przycisk **zdarzenia** .

10. Znajdź **załadowane** zdarzenie, a następnie kliknij dwukrotnie listę rozwijaną obok tego zdarzenia.

     Program Visual Studio otwiera plik związany z kodem dla okna i generuje <xref:System.Windows.FrameworkElement.Loaded> procedurę obsługi zdarzeń.

11. W nowo utworzonym <xref:System.Windows.FrameworkElement.Loaded> programie obsługi zdarzeń skopiuj i wklej poniższy kod.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Ten kod <xref:System.Data.Services.Client.DataServiceCollection%601> tworzy wystąpienie `Customers` dla typu na podstawie wykonywania `Customers` zapytania LINQ, które zwraca obiekt <xref:System.Collections.Generic.IEnumerable%601> z pokrewnymi `Orders` obiektami z usługi danych Northwind i wiąże go z `customersViewSource`.

## <a name="use-a-project-data-source-in-a-windows-form"></a>Używanie źródła danych projektu w formularzu systemu Windows

1. W oknie **źródła danych** rozwiń węzeł **klienci** w źródle danych projektu **NorthwindEntities** .

2. Kliknij element **CustomerID** , wybierz z listy pole **kombi** i przeciągnij element **IDKlienta** z węzła **Customers** do projektanta.

     Spowoduje to utworzenie następujących kontrolek w formularzu:

    - Wystąpienie <xref:System.Windows.Forms.BindingSource> o nazwie `customersBindingSource`.

    - Wystąpienie <xref:System.Windows.Forms.BindingNavigator> o nazwie `customersBindingNavigator`. Tę kontrolkę można usunąć, ponieważ nie będzie to konieczne.

    - Powiązane <xref:System.Windows.Forms.ComboBox> z danymi nazwy `CustomerID`.

    - A <xref:System.Windows.Forms.Label>.

3. Przeciągnij właściwość nawigacji **Orders** do formularza.

4. Spowoduje to utworzenie `ordersBindingSource` <xref:System.Windows.Forms.BindingSource.DataSource%2A> kontrolki z właściwością <xref:System.Windows.Forms.BindingSource.DataMember%2A> zestawu `customersBindingSource` kontrolki i właściwością ustawioną na `Customers`. Tworzy również kontrolkę `ordersDataGridView` powiązaną z danymi w formularzu wraz z odpowiednio zatytułowaną kontrolką etykieta.

5. Obowiązkowe Przeciągnij dodatkowe elementy z węzła **Customers** do projektanta.

6. Otwórz stronę kodową formularza i Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. W klasie częściowej, która definiuje formularz, Dodaj następujący kod, który tworzy <xref:System.Data.Objects.ObjectContext> wystąpienie i `customerID` definiuje stałą.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. W projektancie formularzy kliknij dwukrotnie formularz.

     Spowoduje to otwarcie strony kodowej dla formularza i utworzenie metody, która obsługuje `Load` zdarzenie dla formularza.

9. W programie obsługi zdarzeń skopiuj i wklej poniższy kod. `Load`

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. Ten kod <xref:System.Data.Services.Client.DataServiceCollection%601> tworzy wystąpienie `Customers` dla typu na podstawie wykonania <xref:System.Data.Services.Client.DataServiceQuery%601> , które zwraca wartość <xref:System.Collections.Generic.IEnumerable%601> `Customers` z z usługi danych Northwind i wiąże ją `customersBindingSource`z.

## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Instrukcje: Powiąż dane z Windows Presentation Foundation elementami](bind-data-to-wpf-elements-wcf-data-services.md)
