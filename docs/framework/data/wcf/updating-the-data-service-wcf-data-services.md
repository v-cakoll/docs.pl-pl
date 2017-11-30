---
title: "Aktualizowanie usługi danych (usługi danych WCF)"
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
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c86e755d35a57090941551de43aedd07c8f1f0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="updating-the-data-service-wcf-data-services"></a>Aktualizowanie usługi danych (usługi danych WCF)
Jeśli używasz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta użycie [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych, biblioteki tłumaczy wpisy w źródle danych do wystąpienia klasy usługi danych klienta. Klasy usługi te dane są śledzone za pomocą <xref:System.Data.Services.Client.DataServiceContext> do którego <xref:System.Data.Services.Client.DataServiceQuery%601> należy. Klient śledzi zmiany do jednostki, które raportu za pomocą metod na <xref:System.Data.Services.Client.DataServiceContext>. Te metody włączyć klienta do śledzenia jednostek dodany i usunięty, a także zmiany wprowadzone do wartości właściwości lub relacje między wystąpieniami jednostki. Rejestrowane są wysyłane do usługi data jako opartego na interfejsie REST operacje podczas wywoływania <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody.  
  
> [!NOTE]
>  Jeśli używasz wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> wiązanie danych do kontrolek, zmiany wprowadzone w danych w formancie powiązane są automatycznie zgłaszane <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Dodawanie, modyfikowanie i zmiana jednostek  
 Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio można dodać odwołania do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, wynikowy klienta usługi klas danych poszczególnych mieć statycznego *Utwórz* metodę, która przyjmuje jeden parametr dla każdej właściwości jednostki o wartości null. Ta metoda umożliwia utworzenie wystąpienia obiektu typu klasy, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#createnewproduct)]  
  
 Aby dodać wystąpienia jednostki, należy wywołać odpowiednie *AddTo* metoda <xref:System.Data.Services.Client.DataServiceContext> klasy generowane przez **Dodaj odwołanie do usługi** okno dialogowe, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproductspecific)]  
  
 Spowoduje to dodanie obiektu do kontekstu i do zestawu jednostek poprawne. Możesz także wywołać <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ale zamiast tego należy podać nazwę zestawu jednostek. Jeśli dodano jednostka ma co najmniej jedną relację z innymi obiektami, można użyć <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metody lub użyj jednej z metod poprzedniej i również jawnie definiować tych łączy. Te operacje zostały omówione w dalszej części tego tematu.  
  
 Aby zmodyfikować istniejące wystąpienie jednostki, pierwszego zapytania dla tej jednostki, wprowadź żądane zmiany do jego właściwości, a następnie wywołaj <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metoda <xref:System.Data.Services.Client.DataServiceContext> do wskazania biblioteki klienckiej, która wymaga wysłania aktualizacji dla tego obiektu, jak pokazano w Poniższy przykład:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomerspecific)]  
  
 Aby usunąć wystąpienia jednostki, wywołaj <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metoda <xref:System.Data.Services.Client.DataServiceContext>, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproductspecific)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie, modyfikowanie i usuwanie jednostek](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Dołączanie jednostki  
 Biblioteka klienta umożliwia zapisanie aktualizacje wprowadzone w jednostki bez pierwszy wykonywanie zapytania do załadowania jednostki do <xref:System.Data.Services.Client.DataServiceContext>. Użyj <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> metody można dołączyć istniejącego obiektu do określonego zestawu jednostek w <xref:System.Data.Services.Client.DataServiceContext>. Można zmodyfikować obiektu i zapisać zmiany do usługi danych. W poniższym przykładzie obiekt klienta, który został zmieniony jest dołączony do kontekstu, a następnie <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> jest wywoływana, aby oznaczyć przyłączonego obiektu jako <xref:System.Data.Services.Client.EntityStates.Modified> przed <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> nosi nazwę:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobjectspecific)]  
  
 Następujące kwestie podczas podłączania obiektów:  
  
-   Obiekt jest dołączony w <xref:System.Data.Services.Client.EntityStates.Unchanged> stanu.  
  
-   Gdy obiekt jest dołączony, obiekty, które są związane z przyłączonego obiektu nie są dołączone również.  
  
-   Nie można dołączyć obiektu, jeśli obiekt jest już śledzony przez kontekst.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Przeciążenie metody, która przyjmuje `etag` parametr jest używany podczas dołączania do obiektu jednostki, odebrany wraz z wartość eTag. Ta wartość eTag jest następnie użytych do sprawdzenia współbieżności podczas zmiany przyłączonego obiektu są zapisywane.  
  
 Aby uzyskać więcej informacji, zobacz [porady: dołączanie istniejącego obiektu do obiekcie DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Tworzenie i modyfikowanie łącza relacji  
 Podczas dodawania nowego obiektu przy użyciu <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metody lub odpowiednie *AddTo* metody <xref:System.Data.Services.Client.DataServiceContext> klasy, która **Dodaj odwołanie do usługi** okna dialogowego generuje żadnych relacji między nimi i powiązanych jednostek nie są automatycznie zdefiniowane.  
  
 Można utworzyć i zmienić relacje między wystąpieniami jednostki i biblioteki klienta odzwierciedlenia tych zmian w usłudze danych. Relacje między obiektami są zdefiniowane jako skojarzenia w modelu i <xref:System.Data.Services.Client.DataServiceContext> śledzi każdej relacji w postaci obiektu łącza w tym kontekście. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]udostępnia następujące metody na <xref:System.Data.Services.Client.DataServiceContext> klasa do tworzenia, modyfikowania i usuwania tych łączy:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Tworzy nowy link między dwoma obiektami powiązanej jednostki. Wywołanie tej metody jest odpowiednikiem wywołania <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> i <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> do utworzenia nowego obiektu i definiowanie relacji do istniejącego obiektu.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Tworzy nowy link między dwoma obiektami powiązanej jednostki.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Aktualizuje istniejące łącze między dwoma obiektami powiązanej jednostki. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>Umożliwia również usunąć łącza z Kardynalność zero lub jeden do jeden (`0..1:1`) i jeden do jednego (`1:1`). Można to zrobić, ustawiając dla obiekt pokrewny `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Oznacza łącze kontekst śledzi do usunięcia podczas <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda jest wywoływana. Użyj tej metody, podczas usuwania obiektu pokrewnego lub zmienić relacji, najpierw usunięcie łącza do istniejącego obiektu, a następnie dodanie łącza do nowego obiektu pokrewnego.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Powiadamia o kontekście istniejące łącze między dwoma obiektami jednostki. Kontekst przyjęto założenie, że ta relacja już istnieje w usłudze danych i nie będzie próbował utworzyć łącze podczas wywoływania <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody. Użyj tej metody, gdy dołączyć do kontekstu obiektów, musisz również dołączyć łącze między nimi. Jeśli definiujesz nową relację, należy zamiast tego użyć <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Zatrzymuje śledzenia określone łącze w kontekście. Ta metoda służy do usuwania jeden do wielu (`*:*`) relacji. Łączy relacji o wartości cardinality jednego, zamiast niej należy użyć <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Poniższy przykład przedstawia użycie <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodę, aby dodać nowy `Order_Detail` który jest powiązany z istniejącej `Orders` jednostki. Ponieważ nowe `Order_Details` obiektu jest teraz śledzony przez <xref:System.Data.Services.Client.DataServiceContext>, relacji dodany `Order_Details` obiektu do istniejącej `Products` jednostki jest zdefiniowany przez wywołanie metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> — metoda:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Gdy <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> linki, które należy utworzyć w usłudze danych, aby te linki zostaną uwzględnione w obiektach, które znajdują się w kontekście definiuje metodę, należy także ustawić właściwości nawigacji na same obiekty. W poprzednim przykładzie należy ustawić właściwości nawigacji w następujący sposób:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#setnavprops)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: Definiowanie relacji między obiektami](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Trwa zapisywanie zmian  
 Zmiany są śledzone w <xref:System.Data.Services.Client.DataServiceContext> wystąpienia, ale nie natychmiast wysyłane do serwera. Po zakończeniu zmiany wymagane dla określonego działania wywołać <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> do Prześlij wszystkie zmiany do usługi danych. Aby uzyskać więcej informacji, zobacz [Zarządzanie kontekstu danych usługi](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Można także zapisać zmiany asynchronicznie za pomocą <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> i <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> metody. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Operacje asynchroniczne](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 [Przetwarzanie wsadowe operacji](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 [Obiekt Materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [Zarządzanie kontekstu usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
