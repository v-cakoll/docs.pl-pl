---
title: "Dostawca przesyłania strumieniowego (usługi danych WCF)"
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
- WCF Data Services, providers
- WCF Data Services, binary data
- streaming data provider [WCF Data Services]
- WCF Data Services, streams
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc3e7d545a502c040e7e3ee5140d385b60e82d5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="streaming-provider-wcf-data-services"></a>Dostawca przesyłania strumieniowego (usługi danych WCF)
Usługi danych mogą uwidaczniać dużego obiektu binarnego danych. Te dane binarne może reprezentować strumienie audio i wideo, obrazów, plików dokumentów lub binarne nośników innych typów. Kiedy jednostki w modelu danych obejmuje co najmniej jednej właściwości binarnych, Usługa danych zwraca to dane binarne zakodowane jako base-64 wewnątrz wpis w odpowiedzi źródła danych. Ponieważ ładowanie i serializacji dużych danych binarnych w ten sposób może wpłynąć na wydajność, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] definiuje mechanizm służący do pobierania danych binarnych, niezależnie od podmiotu, do którego należy. Jest to osiągane przez rozdzielić danych binarnych z jednostki jeden lub więcej strumieni danych.  
  
-   Zasób Media - danych binarnych, który należy do jednostki, takich jak wideo, audio, obrazu lub inny typ nośnika strumienia zasobów.  
  
-   Wpis - jednostki, która odwołuje się do strumienia zasobu powiązane z łącza nośnika.  
  
 Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zdefiniuj strumienia zasobów binarnych zaimplementowanie przesyłania strumieniowego dostawcy danych. Przesyłania strumieniowego implementacja dostawcy udostępnia usługę danych ze strumienia zasobów nośnika skojarzony z wybraną jednostką jako <xref:System.IO.Stream> obiektu. Ta implementacja umożliwia usłudze danych Zaakceptuj i zwracać zasobów multimedialnych za pośrednictwem protokołu HTTP jako strumieni danych binarnych określonego typu MIME.  
  
 Konfigurowanie usługi danych do obsługi przesyłanie strumieniowe danych binarnych wymaga wykonania następujących czynności:  
  
1.  Atrybut co najmniej jedna jednostka w modelu danych, zgodnie z wpisem łącza nośnika. Te jednostki nie może zawierać danych binarnych w przesyłane strumieniowo. Wszystkie właściwości binarnych jednostki są zawsze zwracane we wpisie jako algorytmem base-64 binarnego.  
  
2.  Zaimplementuj interfejs T:System.Data.Services.Providers.IDataServiceStreamProvider.  
  
3.  Zdefiniuj Usługa danych, która implementuje <xref:System.IServiceProvider> interfejsu. Dane usługi używa <xref:System.IServiceProvider.GetService%2A> implementacji do przesyłania strumieniowego implementacja dostawcy danych. Ta metoda zwraca odpowiedniej implementacji dostawcy przesyłania strumieniowego.  
  
4.  Włącz strumieni dużych komunikatów w konfiguracji aplikacji sieci Web.  
  
5.  Zapewnianie dostępu do zasobów binarnych na serwerze lub w źródle danych.  
  
 Przykłady w tym temacie są oparte na próbkę przesyłanie strumieniowe zdjęć usługi, która została omówiona szczegółowo w ciągu [przesyłania strumieniowego serii dostawcy danych usług: Implementowanie dostawcy przesyłania strumieniowego (część 1)](http://go.microsoft.com/fwlink/?LinkID=198989). Dla tej usługi przykładowy kod źródłowy jest dostępny na [przesyłanie strumieniowe zdjęć danych usługi przykładową stronę](http://go.microsoft.com/fwlink/?LinkID=198988) w galerii kodu MSDN.  
  
## <a name="defining-a-media-link-entry-in-the-data-model"></a>Definiowanie wpisu łącza nośnika w modelu danych  
 Dostawca źródła danych określa sposób, że jednostka jest zdefiniowany jako wpisu media link entry w modelu danych.  
  
 **Dostawca programu Entity Framework**  
 Aby wskazać, że jednostka jest wpisem łącza nośnika, należy dodać `HasStream` atrybutu do definicji typu jednostki w modelu koncepcyjnym, jak w poniższym przykładzie:  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Musisz również dodać przestrzeń nazw `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` do jednostki lub w katalogu głównym pliku edmx lub .csdl, który definiuje modelu danych.  
  
 [!INCLUDE[crexample](../../../../includes/crexample-md.md)]usługi danych, który używa [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy i udostępnia zasobu multimedialnego, zobacz wpis [przesyłania strumieniowego serii dostawcy danych usług: Implementowanie dostawcy przesyłania strumieniowego (część 1)](http://go.microsoft.com/fwlink/?LinkID=198989).  
  
 **Dostawca odbicia**  
 Aby wskazać, że jednostka jest wpisem łącza nośnika, należy dodać <xref:System.Data.Services.Common.HasStreamAttribute> do klasy, który definiuje typ jednostki w dostawcy odbicia.  
  
 **Dostawcy usług danych niestandardowych**  
 Podczas korzystania z usług niestandardowych dostawców należy zaimplementować <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejs do definiowania metadanych dla usługi danych. Aby uzyskać więcej informacji, zobacz [dostawców usług danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md). Wskazuje, że strumień zasobów binarnych należy do <xref:System.Data.Services.Providers.ResourceType> przez ustawienie <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> właściwości `true` na <xref:System.Data.Services.Providers.ResourceType> reprezentujący typ jednostki wpisu łącza nośnika.  
  
## <a name="implementing-the-idataservicestreamprovider-interface"></a>Implementacja interfejsu interfejsu IDataServiceStreamProvider  
 Aby utworzyć usługę danych, która obsługuje strumienie danych binarnych, musisz zaimplementować <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu. Ta implementacja umożliwia usłudze danych do zwrócenia danych binarnych jako strumień klientowi i korzystania z danych binarnych jako strumień wysłanych z klienta. Usługi danych tworzy wystąpienie tego interfejsu zawsze, gdy musi mieć dostęp do danych binarnych jako strumień. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Interfejsu określa następujące elementy:  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Ta metoda jest wywoływana przez usługę danych można usunąć odpowiadający jej zasób nośnik, po usunięciu jego wpisu media link entry. Po zaimplementowaniu <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, ta metoda zawiera kod, który usuwa skojarzone z wpisu łącza nośnika dostarczony zasobu multimediów.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Ta metoda jest wywoływana przez usługę danych do zwrócenia z zasobem multimediów jako strumień. Po zaimplementowaniu <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, ta metoda zawiera kod, który zapewnia strumienia, który jest używany przez usługę danych zasobem Zwróć nośniki, który jest skojarzony z podanych nośnika wpisu łącza.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Ta metoda jest wywoływana przez usługę danych do zwrócenia identyfikator URI, który jest używany do żądania zasób nośnika wpisu łącza nośnika. Ta wartość jest używana do tworzenia `src` atrybutu w elemencie zawartości wpisu łącza nośnika, oraz że jest używany do żądania strumienia danych. Ta metoda zwraca `null`, Usługa danych automatycznie określa identyfikator URI. Użyj tej metody, gdy chcesz zapewnić klientom bezpośredni dostęp do danych binarnych bez przy użyciu dostawcy pary.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Ta metoda jest wywoływana przez usługę danych ma zostać zwrócona wartość Content-Type zasobu nośnika, który jest skojarzony z określonym nośnika wpisu łącza.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Ta metoda jest wywoływana przez usługę danych do zwrócenia eTag strumienia danych skojarzonego z określonej jednostki. Ta metoda jest używana w przypadku zarządzania współbieżności dla danych binarnych. Gdy ta metoda zwraca wartość null, usługi danych nie śledzi współbieżności.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Ta metoda jest wywoływana przez usługę danych można uzyskać strumienia, który jest używany podczas odbierania strumienia wysłanych z klienta. Po zaimplementowaniu <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, musi zwracać strumień zapisywalny, do którego dane usługi zapisy otrzymał strumienia danych.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Zwraca nazwę typu kwalifikowanego przestrzeni nazw, który reprezentuje typ środowiska uruchomieniowego usługi danych należy utworzyć dla wpisu łącza nośnika skojarzony z strumienia danych dla zasobu multimediów wstawianego.|  
  
## <a name="creating-the-streaming-data-service"></a>Tworzenie przesyłania strumieniowego usługi danych  
 Aby zapewnić [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] środowiska wykonawczego z dostępem do <xref:System.Data.Services.Providers.IDataServiceStreamProvider> implementacji utworzonego usługi danych musi implementować też <xref:System.IServiceProvider> interfejsu. Poniższy przykład przedstawia sposób wykonania <xref:System.IServiceProvider.GetService%2A> sposób zwrócenia wystąpienia klasy `PhotoServiceStreamProvider` klasa implementująca <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 Aby uzyskać ogólne informacje o sposobie tworzenia usługi danych, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Włączanie dużych strumienie binarne w środowisku macierzystym  
 Podczas tworzenia usługi danych w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, sieci Web [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] służy do implementacji protokołu HTTP. Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ogranicza rozmiar wiadomości HTTP do tylko 65 KB. Aby można było do strumienia dużych danych binarnych do i z usług danych, należy również skonfigurować aplikacji sieci Web, aby włączyć duże pliki binarne i użyć strumieni transferu. W tym celu należy dodać następujące opcje w `<configuration />` elementu plik Web.config:  
  
  
  
> [!NOTE]
>  Należy użyć <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> tryb transferu, aby upewnić się, że dane binarne w komunikatów żądań i odpowiedzi są przesyłane strumieniowo i nie jest buforowana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego transferu wiadomości](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) i [przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Domyślnie program Internet Information Services (IIS) ogranicza rozmiar żądania do 4MB. Aby włączyć usługi danych do odbierania strumieni większych niż 4MB uruchomionej na serwerze IIS, należy także ustawić `maxRequestLength` atrybutu [httpRuntime — Element (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/en-us/e9b81350-8aaf-47cc-9843-5f7d0c59f369) w `<system.web />` sekcji konfiguracji jako pokazano w poniższym przykładzie:  
  
  
  
## <a name="using-data-streams-in-a-client-application"></a>Za pomocą strumieni danych w aplikacji klienta  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteki klienta umożliwia zarówno pobierania i aktualizowania te uwidocznione zasoby jako strumienie binarne na kliencie. Aby uzyskać więcej informacji, zobacz [Praca z danymi binarnymi](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="considerations-for-working-with-a-streaming-provider"></a>Informacje dotyczące pracy z dostawcą przesyłania strumieniowego  
 Oto co należy wziąć pod uwagę podczas implementacji dostawcy przesyłania strumieniowego i jeśli dostęp do zasobów multimedialnych z usługi danych.  
  
-   SCALANIE żądania nie są obsługiwane dla zasobów multimedialnych. Umożliwia zmianę zasobu multimediów istniejącej jednostki żądania PUT.  
  
-   Żądanie POST nie może służyć do tworzenia nowego nośnika wpisu łącza. Zamiast tego należy wygenerować żądanie POST, aby utworzyć nowy zasób nośnika, a usługi danych powoduje utworzenie nowego nośnika wpisu łącza z wartościami domyślnymi. Ten nowy obiekt może być aktualizowany przez kolejne żądanie scalania lub PUT. Może również należy wziąć pod uwagę buforowanie jednostki i przeprowadzić aktualizacje w usuwającego, takie jak ustawienie wartości właściwości na wartość nagłówek sluga w żądaniu POST.  
  
-   Po odebraniu żądania POST, dane usługi wywołania <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> można utworzyć zasobu multimediów przed nią wywołuje <xref:System.Data.Services.IUpdatable.SaveChanges%2A> do utworzenia nośnika wpisu łącza.  
  
-   Implementacja interfejsu <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> nie może zwracać <xref:System.IO.MemoryStream> obiektu. Korzystając z tego rodzaju strumienia, problemy z pamięcią zasobów wystąpią, gdy usługa odbierze strumieni bardzo dużej ilości danych.  
  
-   Co należy wziąć pod uwagę podczas przechowywania nośników zasobów w bazie danych są następujące:  
  
    -   Właściwość binarną, która jest zasobem multimediów nie powinny znajdować się w modelu danych. Wszystkie właściwości w modelu danych są zwracane w wpis w odpowiedzi na źródła danych.  
  
    -   Aby zwiększyć wydajność za duża strumienia binarnego, zaleca się utworzenie klasy niestandardowej strumienia do przechowywania danych binarnych w bazie danych. Ta klasa jest zwracany przez użytkownika <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> implementacji i wysyła dane binarne do bazy danych w fragmentów. Aby uzyskać [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] bazy danych, zaleca się użycie FILESTREAM do transmisji danych do bazy danych podczas danych binarnych jest większy niż 1 MB.  
  
    -   Upewnij się, że baza danych jest przeznaczony do przechowywania dużych strumienie binarne, które mają być odbierany przez usługi danych.  
  
    -   Gdy klient wysyła żądanie POST, aby wstawić wpisu media link entry z zasobem multimediów w ramach pojedynczego żądania <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> jest wywoływana w celu uzyskania strumienia, zanim usługa danych Wstawia nową jednostkę w bazie danych. Przesyłania strumieniowego implementacji dostawcy musi mieć możliwość obsługi tego zachowania usługi danych. Należy rozważyć użycie tabeli oddzielnego danych do przechowywania danych binarnych lub strumień danych w pliku dopiero po jednostki został wstawiony do bazy danych magazynu.  
  
-   Po zaimplementowaniu <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>, lub <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> metod, musisz użyć eTag i wartości typu zawartości, które są określane jako parametry metody. Nie ustawiaj eTag lub nagłówki typu zawartości w Twojej <xref:System.Data.Services.Providers.IDataServiceStreamProvider> implementacji dostawcy.  
  
-   Domyślnie klient wysyła dużych strumienie binarne przy użyciu fragmentarycznego HTTP Transfer-Encoding. Ponieważ [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server nie obsługuje tego typu kodowania, nie można użyć tego serwera sieci Web do obsługi przesyłania strumieniowego Usługa danych, musisz zaakceptować dużych strumienie binarne. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server, zobacz [serwerów sieci Web w programie Visual Studio dla projektów sieci Web ASP.NET](http://msdn.microsoft.com/en-us/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Wymagania dotyczące kontroli wersji  
 Dostawca przesyłania strumieniowego ma następujące [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu wymagań dotyczących przechowywania wersji:  
  
-   Dostawca przesyłania strumieniowego wymaga, że usługa danych obsługuje wersja 2.0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu i nowszych wersjach.  
  
 Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Niestandardowi dostawcy usługi danych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)  
 [Praca z danymi binarnymi](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
