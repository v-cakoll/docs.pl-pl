---
title: "Wiązanie danych do kontrolek (usługi danych WCF)"
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
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e0d7ed9fdae7731fd4b023dcad656ebcdcf280f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Wiązanie danych do kontrolek (usługi danych WCF)
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można powiązać formanty, takie jak `ComboBox` i `ListView` formantów na wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601> klasy. Ta kolekcja, która dziedziczy od <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy, zawiera dane z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych. Ta klasa reprezentuje kolekcję danych dynamicznych, która zapewnia powiadomienia, gdy elementy uzyskać dodane lub usunięte. Jeśli używasz wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> dla powiązania danych [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotek klienta obsługi tych zdarzeń, aby upewnić się, że obiekty są śledzone przez <xref:System.Data.Services.Client.DataServiceContext> pozostają zsynchronizowane z danymi w elemencie powiązania interfejsu użytkownika.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> (Pośrednio) Klasa implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu alertu kontekstu, jeśli obiekty są dodane lub usunięte z kolekcji. Obiekty typu usługi danych używana z <xref:System.Data.Services.Client.DataServiceCollection%601> musi implementować też <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu z alertem <xref:System.Data.Services.Client.DataServiceCollection%601> Jeśli zmieniono właściwości obiektów w kolekcji powiązania.  
  
> [!NOTE]
>  Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego lub[DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzia z `/dataservicecollection` opcji do generowania klasy usługi danych klienta, klasy danych wygenerowanych implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [porady: ręcznie wygenerować klienta usługi klas danych](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Trwa tworzenie kolekcji powiązania  
 Utwórz nowe wystąpienie klasy <xref:System.Data.Services.Client.DataServiceCollection%601> klasy przez wywoływanie jednej z metod konstruktora klasy z dostarczonego <xref:System.Data.Services.Client.DataServiceContext> wystąpienia i opcjonalnie <xref:System.Data.Services.Client.DataServiceQuery%601> lub LINQ zapytanie zwracające, po jego wykonaniu <xref:System.Collections.Generic.IEnumerable%601> wystąpienia. To <xref:System.Collections.Generic.IEnumerable%601> zapewnia źródłowej obiektów kolekcji powiązania, które są zmaterializowany z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [Materialization obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Domyślnie, zmiany wprowadzone w powiązanych obiektów i elementów wstawianych do kolekcji automatycznie są śledzone przez <xref:System.Data.Services.Client.DataServiceContext>. Jeśli musisz ręcznie śledzić zmiany, wywołaj jedną z metod konstruktora, która przyjmuje `trackingMode` parametru i określ wartość <xref:System.Data.Services.Client.TrackingMode.None>.  
  
 Poniższy przykład przedstawia sposób tworzenia wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> oparte na podany <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> zwracającą wszystkich klientów z powiązanych zleceń:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Wiązanie danych do systemu Windows Presentation Foundation elementów  
 Ponieważ <xref:System.Data.Services.Client.DataServiceCollection%601> klasa dziedziczy <xref:System.Collections.ObjectModel.ObservableCollection%601> klas, obiektów można powiązać z elementu lub sterowania w aplikacji Windows Presentation Foundation (WPF), jak w przypadku, gdy przy użyciu <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy dla powiązania. Aby uzyskać więcej informacji, zobacz [powiązania danych (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md). Jednym ze sposobów powiązać dane usługi danych z formantów WPF jest skonfigurowanie `DataContext` właściwość elementu z wystąpieniem <xref:System.Data.Services.Client.DataServiceCollection%601> klasę, która zawiera wynik zapytania. W takim przypadku należy użyć <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości można ustawić źródła obiektu formantu. Użyj <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> właściwości w celu określenia, które właściwości powiązania obiektu do wyświetlenia. Element są wiązane do powiązanego obiektu, który jest zwracany przez właściwość nawigacji, podaj ścieżkę w powiązaniu zdefiniowane dla <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości. Ta ścieżka jest określana względem obiektu głównego ustawione przez <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości kontrolki nadrzędnej. W poniższym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> elementu, aby powiązać formant nadrzędny <xref:System.Data.Services.Client.DataServiceCollection%601> obiektów klienta:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 W poniższym przykładzie przedstawiono definicji XAML powiązania elementu podrzędnego <xref:System.Windows.Controls.DataGrid> i <xref:System.Windows.Controls.ComboBox> kontrolki:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: powiązanie danych do systemu Windows Presentation Foundation elementów](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Jeśli jednostka uczestniczy w jeden do wielu lub relacji wiele do wielu, właściwość nawigacji relacji zwraca kolekcję obiektów pokrewnych. Jeśli używasz **Dodaj odwołanie do usługi** okno dialogowe lub DataSvcUtil.exe narzędzie do generowania klasy usługi danych klienta, właściwość nawigacji Zwraca wystąpienie klasy <xref:System.Data.Services.Client.DataServiceCollection%601>. Dzięki temu można powiązać obiekty powiązane z formantem i obsługi wspólnej WPF powiązanie scenariuszach, takich jak wzorzec główny szczegółowy powiązanie dla powiązanych jednostek. W poprzednim przykładzie XAML kodu XAML wiąże wzorca <xref:System.Data.Services.Client.DataServiceCollection%601> do głównego elementu danych. Kolejność <xref:System.Windows.Controls.DataGrid> następnie jest powiązany z zamówienia <xref:System.Data.Services.Client.DataServiceCollection%601> zwrócony z wybranego obiektu klientów, który z kolei jest powiązany z elementem danych głównym <xref:System.Windows.Window>.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Formanty formularzy wiązanie danych do systemu Windows  
 Aby powiązać obiekty kontrolki formularza systemu Windows, należy ustawić `DataSource` właściwości formantu do wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> klasę, która zawiera wynik zapytania.  
  
> [!NOTE]
>  Powiązanie danych jest obsługiwana tylko formanty, które nasłuchują zmian zdarzeń zaimplementowanie <xref:System.Collections.Specialized.INotifyCollectionChanged> i <xref:System.ComponentModel.INotifyPropertyChanged> interfejsów. Gdy formant nie obsługuje tego rodzaju powiadomienia o zmianie, zmiany wprowadzone do odpowiadającego <xref:System.Data.Services.Client.DataServiceCollection%601> nie zostaną uwzględnione w powiązanej kontrolki.  
  
 Poniższy przykład wiąże <xref:System.Data.Services.Client.DataServiceCollection%601> do <xref:System.Windows.Forms.ComboBox> sterowania:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego, aby wygenerować klasy usługi danych klienta, projekt również utworzone oznacza to źródło danych na podstawie wygenerowanej <xref:System.Data.Services.Client.DataServiceContext>. Z tego źródła danych można tworzyć elementy interfejsu użytkownika lub formantów, które są wyświetlane dane z usługą danych po prostu, przeciągając elementy z **źródeł danych** okna do projektanta. Te elementy stają się elementy w aplikacji interfejsu użytkownika, które są powiązane ze źródłem danych. Aby uzyskać więcej informacji, zobacz [porady: powiązywanie danych przy użyciu źródła danych projektu](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Powiązanie stronicowanej danych  
 Usługi danych można skonfigurować tak, aby ograniczyć ilość danych, którego dotyczy kwerenda, która jest zwracana w komunikacie pojedynczą odpowiedź. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Gdy usługa danych jest stronicowanie danych odpowiedzi, każdy odpowiedzi zawiera łącza, który służy do zwracania następnej strony wyników. Aby uzyskać więcej informacji, zobacz [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md). W takim przypadku należy jawnie załadować stron przez wywołanie metody <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> metoda <xref:System.Data.Services.Client.DataServiceCollection%601> przez przekazanie uzyskany z identyfikatora URI <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> właściwości, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 Obiekty powiązane są ładowane w podobny sposób. Aby uzyskać więcej informacji, zobacz [porady: powiązanie danych do systemu Windows Presentation Foundation elementów](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Dostosowywanie zachowania powiązanie danych  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Klasa umożliwia przechwytywanie zdarzenia wywoływane, gdy zostaną wprowadzone zmiany w kolekcji, takie jak obiekt zostanie dodane lub usunięte, a podczas wprowadzania zmian do właściwości obiektu w kolekcji. Można zmodyfikować zdarzenia powiązania danych, aby zastąpić zachowanie domyślne, która obejmuje następujące ograniczenia:  
  
-   Weryfikacja nie jest przeprowadzana w ramach delegatów.  
  
-   Dodawanie jednostki automatycznie dodaje powiązanych jednostek.  
  
-   Usunięcie jednostki nie powoduje usunięcia powiązanych jednostek.  
  
 Po utworzeniu nowego wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601>, masz opcję, aby określić następujące parametry określające delegatów do metod, które obsługiwać zdarzenia wywoływane, gdy są zmieniane obiektów powiązanych:  
  
-   `entityChanged`-metodę, która jest wywoływana, gdy zostanie zmieniona właściwość obiektu. To <xref:System.Func%602> akceptuje delegata <xref:System.Data.Services.Client.EntityChangedParams> obiektu i zwraca wartość logiczną wskazującą, czy zachowanie domyślne, aby wywołać <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, nadal powinien wystąpić.  
  
-   `entityCollectionChanged`-metodę, która jest wywoływana, gdy obiekt jest dodany lub usunięty z kolekcji powiązania. To <xref:System.Func%602> akceptuje delegata <xref:System.Data.Services.Client.EntityCollectionChangedParams> obiektu i zwraca wartość logiczną wskazującą, czy zachowanie domyślne, aby wywołać <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> dla <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> akcji lub <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> dla <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> akcji <xref:System.Data.Services.Client.DataServiceContext>, nadal powinien wystąpić.  
  
> [!NOTE]
>  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nie poprawności niestandardowe zachowania, które implementuje w tych obiektów delegowanych.  
  
 W poniższym przykładzie <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> akcji jest dostosowana do wywołania <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> i <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodę, aby usunąć `Orders_Details` jednostek, które należą do usuniętej `Orders` jednostki. Ta akcja jest wykonywane, ponieważ jednostki zależne nie są automatycznie usuwane po usunięciu obiektu nadrzędnego.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie zachowania wiązania danych](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Domyślne zachowanie, gdy obiekt zostanie usunięty z <xref:System.Data.Services.Client.DataServiceCollection%601> za pomocą <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> metoda jest obiekt również jest oznaczone jako usunięte z <xref:System.Data.Services.Client.DataServiceContext>. Aby zmienić to zachowanie, należy określić delegowany do metody w `entityCollectionChanged` parametr, który jest wywoływane, gdy <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> zdarzenie.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Powiązanie z klas danych klientów niestandardowych danych  
 Aby można było załadować obiektów w <xref:System.Data.Services.Client.DataServiceCollection%601>, same obiekty musi implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Usługi danych klasy klienta, które są generowane, gdy używasz **Dodaj odwołanie do usługi** okno dialogowe lub [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzie implementuje ten interfejs. Jeśli podasz własnego klienta klas danych, należy użyć innego typu kolekcji dla powiązania danych. Po zmianie obiektów, musi obsługiwać zdarzenia w formantach powiązane z danymi do wywołania z następujących metod <xref:System.Data.Services.Client.DataServiceContext> klasy:  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>— Po dodaniu nowego obiektu do kolekcji.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A>— Po usunięciu obiektu z kolekcji.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>-zmiany właściwości obiektu w kolekcji.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>— Po dodaniu obiektu do kolekcji obiektu pokrewnego.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>— Po dodaniu obiektu do kolekcji obiektów pokrewnych.  
  
 Aby uzyskać więcej informacji, zobacz [aktualizacji usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: ręcznie wygenerować klasy usługi danych klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)  
 [Porady: Dodawanie odwołania do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
