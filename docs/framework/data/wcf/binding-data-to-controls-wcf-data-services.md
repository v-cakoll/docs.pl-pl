---
title: Powiązywanie danych z kontrolkami (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
ms.openlocfilehash: 99ad0db9f0adc54d57c5e9a7ed9a5aef3f0a3131
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652256"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Powiązywanie danych z kontrolkami (WCF Data Services)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można powiązać formanty, takie jak `ComboBox` i `ListView` formanty do wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> klasy. Ta kolekcja, która dziedziczy z <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy, zawiera dane z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych. Ta klasa reprezentuje kolekcję danych dynamicznych, która zapewnia powiadomienia, gdy elementy Pobierz dodane lub usunięte. Jeśli używasz wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> dla powiązania danych [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienckie obsługę następujących zdarzeń, aby upewnić się, że obiekty są śledzone przez <xref:System.Data.Services.Client.DataServiceContext> pozostają zsynchronizowane z danymi w powiązanej elementu interfejsu użytkownika.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> (Pośrednio) klasy implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejs do kontekstu alertu, gdy obiekty są dodawane do lub usuwane z kolekcji. Obiekty typu usługi danych używana z <xref:System.Data.Services.Client.DataServiceCollection%601> musi implementować też <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu alert <xref:System.Data.Services.Client.DataServiceCollection%601> Jeśli zmieniono właściwości obiektów w kolekcji powiązania.  
  
> [!NOTE]
>  Kiedy używasz **Dodaj odwołanie do usługi** okna dialogowego lub [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzia z `/dataservicecollection` opcji w celu generowania klas usługi danych klienta, klasy wygenerowane dane, implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [jak: Ręczne Generowanie klas usługi danych klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Trwa tworzenie kolekcji powiązania  
 Utwórz nowe wystąpienie klasy <xref:System.Data.Services.Client.DataServiceCollection%601> klasy, wywołując jedną z metod konstruktora klasy przy użyciu podanej <xref:System.Data.Services.Client.DataServiceContext> wystąpienia i opcjonalnie <xref:System.Data.Services.Client.DataServiceQuery%601> lub zapytanie LINQ, które, gdy jest ono wykonywane, zwraca <xref:System.Collections.Generic.IEnumerable%601> wystąpienia. To <xref:System.Collections.Generic.IEnumerable%601> zapewnia źródło obiektów kolekcji powiązania są zmaterializowanego z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [Materializacja obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Domyślnie, zmiany wprowadzone do powiązane obiekty i elementy wstawione do kolekcji są automatycznie śledzone przez <xref:System.Data.Services.Client.DataServiceContext>. Jeśli zachodzi potrzeba ręcznego śledzenia tych zmian, należy wywołać jedną z metod konstruktora, która przyjmuje `trackingMode` parametru i określ wartość <xref:System.Data.Services.Client.TrackingMode.None>.  
  
 Poniższy przykład pokazuje, jak utworzyć wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601> oparte na podany <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601> zwracającego wszystkich klientów z powiązane zamówienia:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Powiązywanie danych z programu Windows Presentation Foundation elementów  
 Ponieważ <xref:System.Data.Services.Client.DataServiceCollection%601> klasa dziedziczy <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy, można powiązać obiekty do elementu, lub kontrolki w aplikacji Windows Presentation Foundation (WPF), tak jak w przypadku korzystania z <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy dla wiązania. Aby uzyskać więcej informacji, zobacz [powiązanie danych (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md). Jednym ze sposobów, aby powiązać dane usługi danych z formantów WPF jest ustaw `DataContext` właściwość elementu do wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> klasę, która zawiera wynik zapytania. W tym przypadku używasz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość umożliwiająca ustawienie obiektu źródła kontrolki. Użyj <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> właściwości w celu określenia, która właściwość powiązany obiekt, do wyświetlenia. Element są wiązane do powiązanego obiektu, który jest zwracany przez właściwość nawigacji, podaj ścieżkę w powiązaniu zdefiniowane dla <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości. Ta ścieżka jest określana względem obiektu głównego ustawione przez <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości kontrolki nadrzędnej. Poniższy przykład ustawia <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> elementu, aby powiązać formant nadrzędny <xref:System.Data.Services.Client.DataServiceCollection%601> obiektów klienta:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 W poniższym przykładzie pokazano definicji XAML powiązania elementu podrzędnego <xref:System.Windows.Controls.DataGrid> i <xref:System.Windows.Controls.ComboBox> kontrolki:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Powiąż dane z programu Windows Presentation Foundation elementy](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Jeśli jednostka uczestniczy w jeden do wielu lub relacji wiele do wielu, właściwość nawigacji relacji zwraca kolekcję obiektów pokrewnych. Kiedy używasz **Dodaj odwołanie do usługi** okno dialogowe lub narzędzie DataSvcUtil.exe w celu wygenerowania klas usługi danych klienta, właściwość nawigacji Zwraca wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601>. Dzięki temu można powiązać obiekty powiązane z kontrolką w celu obsługi typowych WPF powiązanie scenariusze, takie jak wzorzec wiązania wzorzec / szczegół z powiązanymi obiektami. W poprzednim przykładzie XAML kod XAML powiąże wzorzec <xref:System.Data.Services.Client.DataServiceCollection%601> do głównego elementu danych. Kolejność <xref:System.Windows.Controls.DataGrid> następnie jest powiązany z zamówieniami <xref:System.Data.Services.Client.DataServiceCollection%601> zwrócony z wybranego obiektu klientów, który z kolei jest powiązany z głównym elementem danych <xref:System.Windows.Window>.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Powiązywanie danych z Windows formantów formularzy  
 Aby powiązać obiekty z kontrolki formularz Windows, należy ustawić `DataSource` właściwości formantu do wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> klasę, która zawiera wynik zapytania.  
  
> [!NOTE]
>  Wiązanie danych jest obsługiwane tylko w przypadku kontrolek, które nasłuchują zdarzenia zmian przez zaimplementowanie <xref:System.Collections.Specialized.INotifyCollectionChanged> i <xref:System.ComponentModel.INotifyPropertyChanged> interfejsów. Gdy formant nie obsługuje tego rodzaju powiadomienia o zmianie, zmiany wprowadzone do podstawowej <xref:System.Data.Services.Client.DataServiceCollection%601> nie są odzwierciedlane w powiązanej kontrolki.  
  
 Poniższy przykład tworzy powiązanie <xref:System.Data.Services.Client.DataServiceCollection%601> do <xref:System.Windows.Forms.ComboBox> sterowania:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Kiedy używasz **Dodaj odwołanie do usługi** okna dialogowego, można wygenerować klas usługi danych klienta, tworzone jest źródło danych również oznacza to projekt na podstawie wygenerowanej <xref:System.Data.Services.Client.DataServiceContext>. Z tego źródła danych można utworzyć elementy interfejsu użytkownika lub formantów, które wyświetlają dane z usługi danych poprzez przeciąganie elementów z **źródeł danych** okna do projektanta. Te elementy stają się elementów w interfejsie użytkownika aplikacji, które są powiązane ze źródłem danych. Aby uzyskać więcej informacji, zobacz [jak: Wiązanie danych przy użyciu źródła danych projektu](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Powiązanie stronicowanych danych  
 Usługi danych można skonfigurować tak, aby ograniczyć ilość pobranych danych, która jest zwracana w komunikacie pojedynczą odpowiedź. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Gdy usługa danych jest stronicowanie danych odpowiedzi, poszczególne odpowiedzi zawiera łącze, które służy do zwracania następnej strony wyników. Aby uzyskać więcej informacji, zobacz [ładowanie zawartości odroczone](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md). W takim przypadku należy jawnie załadować stron, wywołując <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> metody <xref:System.Data.Services.Client.DataServiceCollection%601> , przekazując uzyskiwane z identyfikator URI <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> właściwości, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 Powiązane obiekty są ładowane w podobny sposób. Aby uzyskać więcej informacji, zobacz [jak: Powiąż dane z programu Windows Presentation Foundation elementy](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Dostosowywanie zachowania powiązania danych  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Klasy pozwala przechwytywać zdarzenia wywoływane, gdy zostaną wprowadzone zmiany w kolekcji, takie jak obiekt dodawany lub usuwany, a gdy zmiany zostaną wprowadzone do właściwości obiektu w kolekcji. Można zmodyfikować zdarzenia powiązania danych, aby zastąpić domyślne zachowanie, które obejmują następujące ograniczenia:  
  
- Nie nastąpi sprawdzanie poprawności jest wykonywane w ramach delegatów.  
  
- Dodawanie jednostki automatycznie dodaje powiązanych jednostek.  
  
- Usunięcie jednostki nie spowoduje usunięcia powiązanych jednostek.  
  
 Podczas tworzenia nowego wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601>, masz opcję, aby określić następujące parametry, które definiują delegaty do metod, które obsługują zdarzenia wywoływane, gdy zostaną zmienione obiektów powiązanych:  
  
- `entityChanged` — Metoda, która jest wywoływana, gdy zostanie zmieniona właściwość obiektu. To <xref:System.Func%602> akceptuje delegata <xref:System.Data.Services.Client.EntityChangedParams> obiektu i zwraca wartość logiczną, wskazującą, czy domyślne zachowanie, aby wywołać <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, nadal powinien wystąpić.  
  
- `entityCollectionChanged` -metodę, która jest wywoływana, gdy obiekt jest dodawany lub usuwany z kolekcji powiązania. To <xref:System.Func%602> akceptuje delegata <xref:System.Data.Services.Client.EntityCollectionChangedParams> obiektu i zwraca wartość logiczną, wskazującą, czy domyślne zachowanie, aby wywołać <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> dla <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> akcji lub <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> dla <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> akcji <xref:System.Data.Services.Client.DataServiceContext>, nadal powinny występować.  
  
> [!NOTE]
>  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] wykonuje nie nastąpi sprawdzanie poprawności niestandardowych zachowań, które implementują w tych delegatów.  
  
 W poniższym przykładzie <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> dostosowanych do wywoływania akcji <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> i <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodę, aby usunąć `Orders_Details` jednostek, które należą do usuniętej `Orders` jednostki. Ta akcja jest wykonywane, ponieważ jednostki zależne nie są automatycznie usuwane po usunięciu obiektu nadrzędnego.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie zachowania powiązania danych](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Domyślne zachowanie, gdy obiekt zostanie usunięty z <xref:System.Data.Services.Client.DataServiceCollection%601> przy użyciu <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> jest metoda obiektu również jest oznaczone jako usunięte z <xref:System.Data.Services.Client.DataServiceContext>. Aby zmienić to zachowanie, należy określić obiekt delegowany do metody w `entityCollectionChanged` parametru, która jest wywoływana, gdy <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> wystąpi zdarzenie.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Powiązanie z klas danych klientów niestandardowych danych  
 Aby można było załadować obiektów do <xref:System.Data.Services.Client.DataServiceCollection%601>, same obiekty muszą implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Usługa danych klasy klienta, które są generowane, gdy używasz **Dodaj odwołanie do usługi** okno dialogowe lub [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzie implementować ten interfejs. Jeśli podasz własnego klienta klas danych, należy użyć innego typu kolekcji dla powiązania danych. Po zmianie obiektów, musi obsługiwać zdarzenia w kontrolkach powiązane z danymi do wywołania z następujących metod <xref:System.Data.Services.Client.DataServiceContext> klasy:  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> — Po dodaniu nowego obiektu w kolekcji.  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> -gdy obiekt zostanie usunięty z kolekcji.  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> -Po zmianie właściwości do obiektu w kolekcji.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> -gdy obiekt jest dodawany do kolekcji powiązanych obiektów.  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> -gdy obiekt jest dodawany do kolekcji powiązanych obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [aktualizacja usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ręczne Generowanie klas usługi danych klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Instrukcje: Dodaj odwołanie do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
