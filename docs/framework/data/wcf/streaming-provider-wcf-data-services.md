---
title: Dostawca przesyłania strumieniowego (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, binary data
- streaming data provider [WCF Data Services]
- WCF Data Services, streams
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
ms.openlocfilehash: 543d095c88670024a53fad7c865883ecaab1c6e0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43662031"
---
# <a name="streaming-provider-wcf-data-services"></a>Dostawca przesyłania strumieniowego (WCF Data Services)
Usługa danych mogą uwidocznić dane binarne dużego obiektu. Te dane binarne może reprezentować strumieni wideo i audio, obrazy, pliki dokumentów lub inne typy nośników binarnego. Gdy jednostki w modelu danych zawiera jedną lub więcej właściwości binarnych, Usługa danych zwraca te dane binarne zakodowanymi w formacie base-64, wewnątrz wpisu w źródle danych odpowiedzi. Ponieważ ładowania i serializacja dużych danych binarnych w ten sposób może wpłynąć na wydajność, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] definiuje mechanizm służący do pobierania danych binarnych, które są niezależne od jednostki, do której należy. Jest to realizowane przez oddzielenie danych binarnych z jednostki w co najmniej jeden strumień danych.  
  
-   Zasób — dane binarne, które należy do jednostki, takie jak wideo, audio, obrazu lub inny rodzaj strumień zasobu multimediów.  
  
-   Wprowadzanie - jednostki, która ma odwołanie do strumienia zasobu powiązane z linkiem multimediów.  
  
 Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], należy zdefiniować strumienia binarnego, implementując dostawcę danych przesyłania strumieniowego. Przesyłania strumieniowego implementacja dostawcy dostarcza usługi danych za pomocą usługi stream zasób nośnika, które zostały skojarzone z określonej jednostki jako <xref:System.IO.Stream> obiektu. Ta implementacja umożliwia usłudze danych akceptują i zwracają zasoby multimediów za pośrednictwem protokołu HTTP jako dane binarne strumieni określonego typu MIME.  
  
 Konfigurowanie usługi danych, aby obsługiwać przesyłanie strumieniowe danych binarnych wymaga wykonania następujących czynności:  
  
1.  Atrybut co najmniej jednej jednostki w modelu danych, zgodnie z nośnika wpisu łącza nośnika. Te jednostki nie może zawierać dane binarne do celów przesyłania strumieniowego. Wszystkie właściwości binarnych jednostki są zawsze zwracane we wpisie jako kodowanie base-64 binarnego.  
  
2.  Implementuj interfejs T:System.Data.Services.Providers.IDataServiceStreamProvider.  
  
3.  W celu zdefiniowania usługi danych, który implementuje <xref:System.IServiceProvider> interfejsu. Zastosowań usługi danych <xref:System.IServiceProvider.GetService%2A> implementacji dostęp do przesyłania strumieniowego implementacja dostawcy danych. Ta metoda zwraca odpowiednie implementacja dostawcy przesyłania strumieniowego.  
  
4.  Włącz strumieni dużych bloków komunikatów w konfiguracji aplikacji sieci Web.  
  
5.  Zapewnianie dostępu do zasobów binarnych na serwerze lub w źródle danych.  
  
 Przykłady w tym temacie są oparte na próbkę, przesyłanie strumieniowe zdjęć usługi, która została omówiona szczegółowo we wpisie [serii dostawca przesyłania strumieniowego usługi danych: Implementowanie dostawcy przesyłania strumieniowego (część 1)](https://go.microsoft.com/fwlink/?LinkID=198989). Kod źródłowy dla tej usługi próbka jest dostępna w [przesyłanie strumieniowe zdjęć danych usługi przykładową stronę](https://go.microsoft.com/fwlink/?LinkID=198988) w galerii kodów MSDN.  
  
## <a name="defining-a-media-link-entry-in-the-data-model"></a>Definiowanie wpisu łącza nośnika w modelu danych  
 Dostawca źródła danych określa sposób, że jednostka jest zdefiniowany jako wpisu łącza nośnika w modelu danych.  
  
 **Dostawca programu Entity Framework**  
 Aby wskazać, że jednostka jest nośnika wpisu łącza nośnika, należy dodać `HasStream` atrybutu do definicji typu jednostki w modelu koncepcyjnym, jak w poniższym przykładzie:  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Musisz również dodać przestrzeń nazw `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` do jednostki lub w katalogu głównym pliku edmx lub .csdl, który definiuje model danych.  
  
 Na przykład usługi danych, która używa [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy i udostępnia zasobu multimediów, zobacz wpis [przesyłania strumieniowego serii dostawcy danych usług: Implementowanie dostawcy przesyłania strumieniowego (część 1)](https://go.microsoft.com/fwlink/?LinkID=198989).  
  
 **Dostawca odbicia**  
 Aby wskazać, że jednostka jest nośnika wpisu łącza nośnika, należy dodać <xref:System.Data.Services.Common.HasStreamAttribute> do klasy, która definiuje typ jednostki w dostawcy odbicia.  
  
 **Dostawcy usług dane niestandardowe**  
 Korzystając z niestandardowego usługodawcy, należy zaimplementować <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejs zdefiniowanie metadanych dla usługi danych. Aby uzyskać więcej informacji, zobacz [dostawcy usługi danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md). Wskazuje, że strumień binarny zasobów należy do <xref:System.Data.Services.Providers.ResourceType> , ustawiając <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> właściwości `true` na <xref:System.Data.Services.Providers.ResourceType> który reprezentuje typ jednostki, który jest wpisu łącza nośnika.  
  
## <a name="implementing-the-idataservicestreamprovider-interface"></a>Implementowanie interfejsu IDataServiceStreamProvider  
 Aby utworzyć usługę danych, która obsługuje strumienie danych binarnych, należy zaimplementować <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu. Ta implementacja umożliwia usłudze danych zwracać danych binarnych jako strumień do klienta i używanie danych binarnych jako strumień wysłanych z klienta. Usługa danych tworzy instancję tego interfejsu, zawsze wtedy, gdy potrzebny jest dostęp do danych binarnych jako strumień. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Interfejs określa następujące elementy członkowskie:  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Ta metoda jest wywoływana przez usługę danych, aby usunąć odpowiadający jej zasób nośnika, po usunięciu jego wpisu łącza nośnika. Podczas implementacji <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, ta metoda zawiera kod, który usuwa zasób nośnika skojarzony z wpisu łącza nośnika podane.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Ta metoda jest wywoływana przez usługę danych do zwrócenia z zasobem multimediów jako strumień. Podczas implementacji <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, ta metoda zawiera kod, który zawiera strumień, który jest używany przez usługę danych zasobem Zwróć nośniki, który jest skojarzony z wpisu łącza nośnika podana.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Ta metoda jest wywoływana przez usługę danych, aby zwrócić identyfikator URI, który jest używany do zażądania zasób nośnika wpisu łącza nośnika. Ta wartość jest używana do tworzenia `src` atrybutu w elemencie content wpisu łącza nośnika, oraz że jest używany do zażądania strumienia danych. Ta metoda zwraca `null`, Usługa danych automatycznie określa identyfikator URI. Użyj tej metody, gdy trzeba zapewnić klientom bez użycia dostawcy pary bezpośredni dostęp do danych binarnych.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Ta metoda jest wywoływana przez usługę danych, aby zwrócić wartość Content-Type zasobu multimediów, który jest skojarzony z określonym nośnika wpisu łącza.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Ta metoda jest wywoływana przez usługę danych, aby zwrócić element eTag strumienia danych, który jest skojarzony z określonej jednostki. Ta metoda jest używana, jeśli zarządzasz współbieżności dla danych binarnych. Gdy ta metoda zwróci wartość null, Usługa danych nie śledzi współbieżności.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Ta metoda jest wywoływana przez usługę danych, aby uzyskać strumień, który jest używany podczas odbierania strumienia wysłanych z klienta. Podczas implementacji <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, musi zwrócić strumień możliwy do zapisania, która zapisuje odebrane dane strumienia usługi danych.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Zwraca nazwę kwalifikowaną przestrzeń nazw typu, który reprezentuje typ, który środowiska uruchomieniowego usługi danych należy utworzyć dla wpisu łącza nośnika, skojarzony ze strumieniem danych dla zasobu multimediów, który jest wstawiany.|  
  
## <a name="creating-the-streaming-data-service"></a>Tworzenie usługi danych przesyłania strumieniowego  
 Aby zapewnić [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostęp do aparatu plików wykonywalnych <xref:System.Data.Services.Providers.IDataServiceStreamProvider> implementacji usługi danych, którą tworzysz musi implementować też <xref:System.IServiceProvider> interfejsu. Poniższy przykład pokazuje, jak zaimplementować <xref:System.IServiceProvider.GetService%2A> metodę, aby zwrócić wystąpienia `PhotoServiceStreamProvider` klasę, która implementuje <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 Aby uzyskać ogólne informacje o sposobie tworzenia usługi danych, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Włączanie dużych strumieni binarnych w środowisku macierzystym  
 Podczas tworzenia usługi danych w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web Windows Communication Foundation (WCF) służy do zapewnienia implementacji protokołu HTTP. Domyślnie program WCF ogranicza rozmiar wiadomości HTTP do tylko 65 KB. Aby można było do strumienia dużych danych binarnych do i z usługi danych, należy również skonfigurować aplikację sieci Web, aby umożliwić duże pliki binarne i strumieni na użytek transferu. Aby to zrobić, Dodaj następujące elementy w `<configuration />` element pliku Web.config aplikacji:  
  
  
  
> [!NOTE]
>  Należy użyć <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> tryb transferu, aby upewnić się, że dane binarne w komunikatach żądania i odpowiedzi są przesyłane strumieniowo i nie jest buforowana przez architekturę WCF.  
  
 Aby uzyskać więcej informacji, zobacz [przesyłanie strumieniowe przesyłanie komunikatów](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) i [przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Domyślnie program Internet Information Services (IIS) ogranicza rozmiar żądania do 4MB. Aby włączyć usługi danych otrzymać strumieni większy niż 4MB, podczas uruchamiania w usługach IIS, należy także ustawić `maxRequestLength` atrybutu [httpRuntime — Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369) w `<system.web />` sekcji konfiguracji jako pokazano w poniższym przykładzie:  
  
  
  
## <a name="using-data-streams-in-a-client-application"></a>Za pomocą strumieni danych w aplikacji klienckiej  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta umożliwia pobrania i aktualizacji tych narażonych zasobów jako strumieni binarnych na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [Praca z danymi binarnymi](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="considerations-for-working-with-a-streaming-provider"></a>Zagadnienia dotyczące pracy z dostawca przesyłania strumieniowego  
 Dostępne są następujące rzeczy, które należy wziąć pod uwagę podczas implementacji dostawca przesyłania strumieniowego i jeśli uzyskujesz dostęp do zasobów nośników z usługi danych.  
  
-   Żądania scalania nie są obsługiwane dla zasobów nośników. Użyj żądania PUT, aby zmienić zasób nośnika istniejącej jednostki.  
  
-   Żądanie POST nie może służyć do tworzenia nowego nośnika wpisu łącza. Zamiast tego należy wygenerować żądanie POST, aby utworzyć nowy zasób nośnika, a usługa danych tworzy nowego nośnika wpisu łącza z wartościami domyślnymi. Ta nowa jednostka może być aktualizowana przez kolejne żądanie scalania lub PUT. Może również należy wziąć pod uwagę buforowanie jednostki i przeprowadzić aktualizacje w usuwającego, takie jak ustawianie wartości właściwości do wartości nagłówek sluga w żądaniu POST.  
  
-   Po odebraniu żądania POST danych analizującą <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> do utworzenia zasobu multimediów przed nią wywołuje <xref:System.Data.Services.IUpdatable.SaveChanges%2A> do utworzenia nośnika wpisu łącza.  
  
-   Implementacja <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> nie powinny zwracać <xref:System.IO.MemoryStream> obiektu. Korzystając z tego rodzaju strumienia, problemy z pamięcią zasobu ma miejsce, gdy usługa odbiera strumieni bardzo dużej ilości danych.  
  
-   Oto co należy wziąć pod uwagę podczas zapisywania zasoby multimediów w bazie danych:  
  
    -   Właściwość binarną będącego zasobem multimediów nie powinny znajdować się w modelu danych. Wszystkie właściwości w modelu danych są zwracane w wpis w źródle danych odpowiedzi.  
  
    -   Aby zwiększyć wydajność przy użyciu dużych strumienia binarnego, zaleca się tworzenia klasy niestandardowej strumienia do przechowywania danych binarnych w bazie danych. Ta klasa jest zwracana przez Twoje <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> implementacji i wysyła dane binarne do bazy danych we fragmentach. Dla bazy danych programu SQL Server zaleca się używać FILESTREAM przesyłanie strumieniowe danych do bazy danych, gdy dane binarne, jest większa niż 1MB.  
  
    -   Upewnij się, że bazy danych jest przeznaczony do przechowywania dużych strumieni binarnych, które mają być odbierane przez usługę danych.  
  
    -   Gdy klient wysyła żądanie POST, aby wstawić wpisu łącza nośnika z zasobem multimediów w pojedynczym żądaniu <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> jest wywoływana w celu uzyskania strumienia przed usługi danych Wstawia nową jednostkę w bazie danych. Przesyłania strumieniowego implementacja dostawcy musi mieć możliwość obsługi to zachowanie usługi danych. Należy rozważyć użycie tabelę oddzielnych danych do przechowywania danych binarnych lub magazynu strumień danych w pliku aż po jednostki został wstawiony do bazy danych.  
  
-   Podczas implementacji <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>, lub <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> metody, należy użyć elementu eTag i wartości Content-Type, które są dostarczane jako parametry metody. Nie należy ustawiać tagu eTag lub nagłówki typu zawartości w Twojej <xref:System.Data.Services.Providers.IDataServiceStreamProvider> implementacja dostawcy.  
  
-   Domyślnie klient wysyła dużych strumieni binarnych za pomocą pakietowego HTTP Transfer-Encoding. Ponieważ [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server nie obsługuje tego rodzaju kodowania, nie można używać tego serwera sieci Web do obsługi przesyłania strumieniowego usługi danych, które muszą zaakceptować dużych strumieni binarnych. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server, zobacz [serwerów sieci Web w programie Visual Studio dla projektów sieci Web platformy ASP.NET](https://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Wymagania dotyczące przechowywania wersji  
 Dostawca przesyłania strumieniowego ma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu wymagań dotyczących przechowywania wersji:  
  
-   Dostawca przesyłania strumieniowego wymaga, że usługa danych obsługuje wersję 2.0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu i nowszych wersjach.  
  
 Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Niestandardowi dostawcy usługi danych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)  
 [Praca z danymi binarnymi](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
