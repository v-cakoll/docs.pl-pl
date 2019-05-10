---
title: Aktualizacja usługi danych (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
ms.openlocfilehash: 4b351b2a69d2829b67c80839f3257fa8e218b55d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660635"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Aktualizacja usługi danych (WCF Data Services)
Kiedy używasz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienckiej z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych, biblioteka tłumaczy wpisy w źródle danych do wystąpień klas usługi danych klienta. Tych klas usługi danych są śledzone za pomocą <xref:System.Data.Services.Client.DataServiceContext> do której <xref:System.Data.Services.Client.DataServiceQuery%601> należy. Klient śledzi zmiany jednostki, które możesz zgłaszać za pomocą metod na <xref:System.Data.Services.Client.DataServiceContext>. Te metody umożliwiają klienta śledzić dodanych i usuniętych jednostek, a także zmiany wprowadzone do wartości właściwości lub relacji między wystąpieniami jednostki. Zmiany śledzone są wysyłane do usługi danych jako operacje oparte na protokole REST, po wywołaniu <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody.  
  
> [!NOTE]
>  Jeśli używasz wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> danych można powiązać formanty, zmiany wprowadzone do danych z powiązanej kontrolki są automatycznie zgłaszane <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [powiązanie danych z kontrolkami](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Dodawanie, modyfikowanie i zmianę jednostki  
 Zastosowania **Dodaj odwołanie do usługi** w programie Visual Studio można dodać odwołania do okna dialogowego [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, ma wynikowy klas usługi danych klienta każdego statycznego *Utwórz* metodę przyjmującą jeden parametr dla każdej właściwości niedopuszczającej jednostki. Ta metoda służy do tworzenia wystąpienia obiektu typu klasy, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 Aby dodać wystąpienia jednostki, należy wywołać odpowiednie *AddTo* metody <xref:System.Data.Services.Client.DataServiceContext> klasy generowanej przez **Dodaj odwołanie do usługi** okno dialogowe, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 Spowoduje to dodanie obiektu do kontekstu i do zestawu jednostek poprawne. Można również wywołać <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ale zamiast tego musisz podać nazwę zestawu jednostek. Jeśli dodano określona jednostka ma jeden lub więcej relacje z innymi obiektami, można użyć <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metody lub użyj jednego z poprzednich metod, a także jawne zdefiniowanie tych łączy. Te operacje są omówione w dalszej części tego tematu.  
  
 Aby zmodyfikować istniejące wystąpienie jednostki, pierwsze zapytanie dla danej jednostki, wprowadź żądane zmiany do jego właściwości, a następnie wywołaj <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metody <xref:System.Data.Services.Client.DataServiceContext> do wskazania biblioteki klienckiej, która wymaga wysłania aktualizacji dla tego obiektu, jak pokazano w Poniższy przykład:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 Aby usunąć wystąpienie jednostki, wywołaj <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metody <xref:System.Data.Services.Client.DataServiceContext>, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie, modyfikowanie i usuwanie jednostek](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Dołączanie jednostek  
 Biblioteka klienta umożliwia zapisanie aktualizacje wprowadzone do jednostki bez wykonywanie zapytania Załaduj jednostkę do <xref:System.Data.Services.Client.DataServiceContext>. Użyj <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> metodę, aby dołączyć istniejący obiekt do określonego zestawu jednostek w <xref:System.Data.Services.Client.DataServiceContext>. Następnie można zmodyfikować obiekt i zapisać zmiany do usługi danych. W poniższym przykładzie obiekt klienta, który został zmieniony jest dołączony do kontekstu i następnie <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> jest wywoływana, aby oznaczyć przyłączonego obiektu jako <xref:System.Data.Services.Client.EntityStates.Modified> przed <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> nosi nazwę:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 Podczas podłączania obiektów obowiązują następujące zastrzeżenia:  
  
- Obiekt jest dołączony w <xref:System.Data.Services.Client.EntityStates.Unchanged> stanu.  
  
- Gdy obiekt jest dołączony, obiekty, które są powiązane z przyłączonego obiektu nie są również dołączone.  
  
- Nie można dołączyć obiektu, jeśli jednostka jest już śledzony przez kontekst.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Przeciążenia metody, która przyjmuje `etag` parametr jest używany podczas dołączania do obiektu jednostki, przedstawiający otrzymany wraz z wartością tagu eTag. Ta wartość elementu eTag jest następnie użytych do sprawdzenia współbieżności po zapisaniu zmian przyłączonego obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dołączanie istniejącej jednostki do obiektu DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Tworzenie i modyfikowanie relacji łączy  
 Po dodaniu nowej jednostki przy użyciu <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metody lub odpowiednie *AddTo* metody <xref:System.Data.Services.Client.DataServiceContext> klasy, która **Dodaj odwołanie do usługi** okna dialogowego generuje żadnych relacji między nimi i powiązanych jednostek nie są automatycznie definiowane.  
  
 Można tworzyć i zmieniać relacje między wystąpieniami jednostki i biblioteki klienta odzwierciedlenia tych zmian w usłudze data service. Relacje między jednostkami są definiowane jako skojarzeń w modelu i <xref:System.Data.Services.Client.DataServiceContext> śledzi każdej relacji jako obiekt łącza w kontekście. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] udostępnia następujące metody w <xref:System.Data.Services.Client.DataServiceContext> klasy w celu tworzenia, modyfikowania i usuwania tych linków:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Tworzy nowe łącze między dwoma obiektami powiązanej jednostki. Wywołanie tej metody jest równoważne z wywoływaniem <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> i <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> Aby utworzyć nowy obiekt i zdefiniować relację do istniejącego obiektu.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Tworzy nowe łącze między dwoma obiektami powiązanej jednostki.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Aktualizuje istniejące łącze między dwoma obiektami powiązanej jednostki. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> Umożliwia również usuwać łącza z kardynalnością zero lub jeden do jeden (`0..1:1`) i jeden do jednego (`1:1`). Można to zrobić, ustawiając powiązany obiekt `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Oznacza łącze, które służy do śledzenia kontekstu do usunięcia podczas <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana. Metoda ta jest używana, gdy usuniesz powiązanego obiektu lub zmienić relację, najpierw usuwania łącze do istniejącego obiektu, a następnie dodając łącze do nowego obiektu pokrewnego.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Powiadamia o kontekście istniejącego łącza między dwa obiekty jednostki. Kontekst założono, że ta relacja już istnieje w usłudze data i nie podejmuje próby utworzenia linku po wywołaniu <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody. Użyj tej metody, gdy dołączanie obiektów do kontekstu i musisz również dołączyć łącza między tymi dwoma. Jeśli definiujesz nowe relacje, należy w zamian użyć <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Zatrzymuje śledzenia określonego linku w kontekście. Ta metoda służy do usuwania jeden do wielu (`*:*`) relacji. W przypadku relacji powiązania z kardynalnością jednego, zamiast tego należy użyć <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodę, aby dodać nowy `Order_Detail` , jest powiązany z istniejącego `Orders` jednostki. Ponieważ nowe `Order_Details` obiektu jest teraz śledzone przez <xref:System.Data.Services.Client.DataServiceContext>, relacji dodanego `Order_Details` obiektu do istniejących `Products` jednostka została zdefiniowana przez wywołanie metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> metody:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Gdy <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> Metoda określa łącza, które muszą zostać utworzone w usługi danych, aby te łącza, które zostaną uwzględnione w obiektach, które znajdują się w kontekście, należy również ustawić właściwości nawigacji na samych obiektach. W poprzednim przykładzie należy ustawić właściwości nawigacji w następujący sposób:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Definiowanie relacji jednostek](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Zapisywanie zmian  
 Zmiany są śledzone w <xref:System.Data.Services.Client.DataServiceContext> wystąpienia, ale nie natychmiast wysyłane do serwera. Po zakończeniu wymagane zmiany dla określonego działania wywołać <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> przesłać wszystkie zmiany do usługi danych. Aby uzyskać więcej informacji, zobacz [zarządzanie kontekstem usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Można również zapisać zmiany asynchronicznie przy użyciu <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> i <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> metody. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Operacje asynchroniczne](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)
- [Operacje przetwarzania wsadowego](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
- [Materializacja obiektu](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)
- [Zarządzanie kontekstem usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
