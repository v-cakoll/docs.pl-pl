---
title: Aktualizowanie usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
ms.openlocfilehash: 02bcb8f12cd7f230d60c3b3c58174a54405ff955
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975110"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Aktualizowanie usługi danych (Usługi danych programu WCF)
W przypadku korzystania z biblioteki klienta [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do korzystania z kanału informacyjnego protokołu OData (Open Data Protocol), biblioteka tłumaczy wpisy w strumieniu na wystąpienia klas usługi danych klienta. Te klasy usługi danych są śledzone przy użyciu <xref:System.Data.Services.Client.DataServiceContext>, do którego należy <xref:System.Data.Services.Client.DataServiceQuery%601>. Klient śledzi zmiany w jednostkach, które są zgłaszane przy użyciu metod w <xref:System.Data.Services.Client.DataServiceContext>. Te metody umożliwiają klientowi śledzenie dodanych i usuniętych jednostek, a także zmiany wartości właściwości lub relacje między wystąpieniami jednostek. Te śledzone zmiany są wysyłane z powrotem do usługi danych jako operacje oparte na interfejsie REST po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
> [!NOTE]
> W przypadku używania wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> w celu powiązania danych z kontrolkami, zmiany wprowadzone do danych w formancie powiązanym są automatycznie zgłaszane do <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [Powiązywanie danych z kontrolkami](binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Dodawanie, modyfikowanie i zmiana jednostek  
 W przypadku użycia okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio w celu dodania odwołania do źródła danych OData, wytworzone klasy usługi dane klienta mają metodę static *Create* , która przyjmuje jeden parametr dla każdej właściwości jednostki, która nie dopuszcza wartości null. Tej metody można użyć do tworzenia wystąpień klas typu jednostki, jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 Aby dodać wystąpienie jednostki, wywołaj odpowiednią metodę *AddTo* na klasy <xref:System.Data.Services.Client.DataServiceContext> wygenerowanej przez okno dialogowe **Dodaj odwołanie do usługi** , jak w poniższym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 Spowoduje to dodanie obiektu do kontekstu i do poprawnego zestawu jednostek. Można również wywołać <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ale zamiast tego należy podać nazwę zestawu jednostek. Jeśli dodana jednostka ma jedną lub więcej relacji z innymi jednostkami, można użyć metody <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> lub użyć jednej z powyższych metod, a także jawnie zdefiniować te linki. Te operacje zostały omówione w dalszej części tego tematu.  
  
 Aby zmodyfikować istniejące wystąpienie jednostki, pierwsze zapytanie dla tej jednostki, wprowadź odpowiednie zmiany w jego właściwościach, a następnie Wywołaj metodę <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, aby wskazać bibliotekę klienta, która musi wysyłać aktualizację dla tego obiektu, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 Aby usunąć wystąpienie jednostki, wywołaj metodę <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie, modyfikowanie i usuwanie jednostek](how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Dołączanie jednostek  
 Biblioteka klienta umożliwia zapisywanie aktualizacji dokonanych w jednostce bez uprzedniego wykonania zapytania w celu załadowania jednostki do <xref:System.Data.Services.Client.DataServiceContext>. Użyj metody <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A>, aby dołączyć istniejący obiekt do określonego zestawu jednostek w <xref:System.Data.Services.Client.DataServiceContext>. Następnie można zmodyfikować obiekt i zapisać zmiany w usłudze danych. W poniższym przykładzie obiekt klienta, który został zmieniony, jest dołączony do kontekstu, a następnie <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> jest wywoływana, aby oznaczyć dołączony obiekt jako <xref:System.Data.Services.Client.EntityStates.Modified> przed wywołaniem <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 Podczas dołączania obiektów stosowane są następujące zagadnienia:  
  
- Obiekt jest podłączony w stanie <xref:System.Data.Services.Client.EntityStates.Unchanged>.  
  
- Po dołączeniu obiektu obiekty powiązane z dołączonym obiektem nie są także dołączone.  
  
- Nie można dołączyć obiektu, jeśli jednostka jest już śledzona przez kontekst.  
  
- Przeciążenie metody <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29>, które pobiera parametr `etag`, jest używany podczas dołączania obiektu jednostki, który został odebrany wraz z wartością eTag. Ta wartość eTag jest następnie używana do sprawdzania współbieżności po zapisaniu zmian w dołączonym obiekcie.  
  
 Aby uzyskać więcej informacji, zobacz [How to: dołączanie istniejącej jednostki do obiekcie DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Tworzenie i modyfikowanie linków relacji  
 Po dodaniu nowej jednostki przy użyciu metody <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> lub odpowiedniej metody *AddTo* klasy <xref:System.Data.Services.Client.DataServiceContext>, która generuje okno dialogowe **Dodaj odwołanie do usługi** , wszelkie relacje między nową jednostką i powiązanymi jednostkami nie są definiowane automatycznie.  
  
 Można tworzyć i zmieniać relacje między wystąpieniami jednostek, a ich Biblioteka kliencka odzwierciedla te zmiany w usłudze danych. Relacje między jednostkami są zdefiniowane jako skojarzenia w modelu, a <xref:System.Data.Services.Client.DataServiceContext> śledzi każdą relację jako obiekt łącza w kontekście. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] udostępnia następujące metody klasy <xref:System.Data.Services.Client.DataServiceContext> do tworzenia, modyfikowania i usuwania tych linków:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|Tworzy nowy link między dwoma powiązanymi obiektami jednostek. Wywołanie tej metody jest równoznaczne z wywołaniem <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> i <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> do tworzenia nowego obiektu i definiowania relacji z istniejącym obiektem.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|Tworzy nowy link między dwoma powiązanymi obiektami jednostek.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Aktualizuje istniejące łącze między dwoma powiązanymi obiektami jednostek. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> jest również używany do usuwania linków z kardynalnością zero-lub-jeden-do-jednego (`0..1:1`) i jeden-do-jednego (`1:1`). Można to zrobić przez ustawienie powiązanego obiektu na `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Oznacza link, który jest śledzony przez kontekst do usunięcia, gdy wywoływana jest metoda <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>. Tej metody należy użyć w przypadku usunięcia powiązanego obiektu lub zmiany relacji przez usunięcie łącza do istniejącego obiektu, a następnie dodanie linku do nowego powiązanego obiektu.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|Powiadamia kontekst istniejącego łącza między dwoma obiektami jednostek. W kontekście przyjęto założenie, że ta relacja już istnieje w usłudze danych i nie próbuje utworzyć łącza po wywołaniu metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>. Użyj tej metody, gdy dołączysz obiekty do kontekstu i chcesz również dołączyć łącze między nimi. W przypadku definiowania nowej relacji należy zamiast niej używać <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Wyłącza śledzenie określonego linku w kontekście. Ta metoda służy do usuwania relacji jeden-do-wielu (`*:*`). W przypadku linków relacji z kardynalnością jednego należy zamiast tego użyć <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Poniższy przykład pokazuje, jak za pomocą metody <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> dodać nowy `Order_Detail`, który jest powiązany z istniejącą jednostką `Orders`. Ponieważ nowy obiekt `Order_Details` jest teraz śledzony przez <xref:System.Data.Services.Client.DataServiceContext>, relacja dodanego obiektu `Order_Details` do istniejącej jednostki `Products` jest definiowana przez wywołanie metody <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Chociaż metoda <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> definiuje linki, które muszą zostać utworzone w usłudze danych, aby te linki zostały odzwierciedlone w obiektach, które znajdują się w kontekście, należy również ustawić właściwości nawigacji dla obiektów. W poprzednim przykładzie należy ustawić właściwości nawigacji w następujący sposób:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 Aby uzyskać więcej informacji, zobacz [How to: define Entity Relationships](how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Zapisywanie zmian  
 Zmiany są śledzone w wystąpieniu <xref:System.Data.Services.Client.DataServiceContext>, ale nie są natychmiast wysyłane do serwera. Po zakończeniu wymaganych zmian dla określonego działania Wywołaj <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>, aby przesłać wszystkie zmiany do usługi danych. Aby uzyskać więcej informacji, zobacz [zarządzanie kontekstem usługi danych](managing-the-data-service-context-wcf-data-services.md). Można także zapisywać zmiany asynchronicznie przy użyciu metod <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> i <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>. Aby uzyskać więcej informacji, zobacz [operacje asynchroniczne](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
- [Operacje asynchroniczne](asynchronous-operations-wcf-data-services.md)
- [Operacje przetwarzania wsadowego](batching-operations-wcf-data-services.md)
- [Materializacja obiektu](object-materialization-wcf-data-services.md)
- [Zarządzanie kontekstem usługi danych](managing-the-data-service-context-wcf-data-services.md)
