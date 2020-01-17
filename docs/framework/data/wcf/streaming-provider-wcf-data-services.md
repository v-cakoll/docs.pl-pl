---
title: Dostawca przesyłania strumieniowego (Usługi danych programu WCF)
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
ms.openlocfilehash: 83f28c50c53281692e1c3c6d55cc55e8d9304ad9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116599"
---
# <a name="streaming-provider-wcf-data-services"></a>Dostawca przesyłania strumieniowego (Usługi danych programu WCF)

Usługa danych może uwidaczniać dane binarne dużych obiektów. Te dane binarne mogą reprezentować strumienie wideo i audio, obrazy, pliki dokumentów lub inne typy multimediów binarnych. Gdy jednostka w modelu danych zawiera jedną lub więcej właściwości binarnych, usługa danych zwraca te dane binarne zakodowane jako Base-64 wewnątrz wpisu w kanale informacyjnym odpowiedzi. Ponieważ ładowanie i Serializowanie dużych danych binarnych w ten sposób może wpłynąć na wydajność, protokół Open Data Protocol (OData) definiuje mechanizm pobierania danych binarnych niezależnie od jednostki, do której należy. Jest to realizowane przez oddzielenie danych binarnych od jednostki do co najmniej jednego strumienia danych.

- Zasób multimedialny — dane binarne należące do jednostki, takie jak wideo, audio, obrazy lub inny typ strumienia zasobów multimediów.

- Wpis multimediów — jednostka, która ma odwołanie do powiązanego strumienia zasobów multimediów.

Za pomocą Usługi danych programu WCF definiujesz strumień zasobów binarnych przez implementację dostawcy danych przesyłania strumieniowego. Implementacja dostawcy przesyłania strumieniowego dostarcza usługę danych za pomocą strumienia zasobów multimediów skojarzonego z konkretną jednostką jako obiektem <xref:System.IO.Stream>. Ta implementacja umożliwia usłudze danych akceptowanie i zwracanie zasobów multimedialnych za pośrednictwem protokołu HTTP jako strumieni danych binarnych określonego typu MIME.

Skonfigurowanie usługi danych do obsługi przesyłania strumieniowego danych binarnych wymaga wykonania następujących czynności:

1. Atrybut co najmniej jednej jednostki w modelu danych jako wpis linku do nośnika. Te jednostki nie powinny uwzględniać danych binarnych, które mają być przesyłane strumieniowo. Wszystkie właściwości binarne jednostki są zawsze zwracane w pozycji jako plik binarny zakodowany w formacie Base-64.

2. Zaimplementuj interfejs T:System.Data.Services.Providers.IDataServiceStreamProvider.

3. Zdefiniuj usługę danych implementującą interfejs <xref:System.IServiceProvider>. Usługa danych używa implementacji <xref:System.IServiceProvider.GetService%2A>, aby uzyskać dostęp do implementacji dostawcy danych przesyłanych strumieniowo. Ta metoda zwraca odpowiednią implementację dostawcy przesyłania strumieniowego.

4. Włącz duże strumienie komunikatów w konfiguracji aplikacji sieci Web.

5. Włącz dostęp do zasobów binarnych na serwerze lub w źródle danych.

Przykłady w tym temacie są oparte na przykładowej usłudze fotografii przesyłania strumieniowego, która została omówiona szczegółowo w [serii Data Services dostawcy przesyłania strumieniowego: implementowanie dostawcy przesyłania strumieniowego (część 1)](https://docs.microsoft.com/archive/blogs/astoriateam/data-services-streaming-provider-series-implementing-a-streaming-provider-part-1). Kod źródłowy przykładowej usługi danych zdjęć strumieniowych jest dostępny w witrynie [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample).

## <a name="defining-a-media-link-entry-in-the-data-model"></a>Definiowanie wpisu multimediów w modelu danych

Dostawca źródła danych określa sposób, w jaki jednostka jest definiowana jako wpis multimediów w modelu danych.

**Dostawca programu Entity Framework**

Aby wskazać, że jednostka jest wpisem linku do nośnika, Dodaj atrybut `HasStream` do definicji typu jednostki w modelu koncepcyjnym, jak w poniższym przykładzie:

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Należy również dodać przestrzeń nazw `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` do jednostki lub do katalogu głównego pliku. edmx lub. csdl, który definiuje model danych.

Przykład usługi danych, która korzysta z dostawcy Entity Framework i uwidacznia zasób multimedialny, znajduje się w temacie Post [Data Services Streaming Provider series: implementowanie dostawcy przesyłania strumieniowego (część 1)](https://docs.microsoft.com/archive/blogs/astoriateam/data-services-streaming-provider-series-implementing-a-streaming-provider-part-1).

**Dostawca odbicia**

Aby wskazać, że jednostka jest wpisem linku do nośnika, Dodaj <xref:System.Data.Services.Common.HasStreamAttribute> do klasy, która definiuje typ jednostki w dostawcy odbicia.

**Niestandardowy dostawca usługi danych**

W przypadku korzystania z niestandardowych dostawców usług należy zaimplementować interfejs <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> w celu zdefiniowania metadanych usługi danych. Aby uzyskać więcej informacji, zobacz [niestandardowe dostawcy usług danych](custom-data-service-providers-wcf-data-services.md). Należy wskazać, że strumień zasobów binarnych należy do <xref:System.Data.Services.Providers.ResourceType> przez ustawienie właściwości <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> na `true` na <xref:System.Data.Services.Providers.ResourceType>, który reprezentuje typ jednostki, który jest wpisem łącza do nośnika.

## <a name="implementing-the-idataservicestreamprovider-interface"></a>Implementowanie interfejsu IDataServiceStreamProvider

Aby utworzyć usługę danych obsługującą strumienie danych binarnych, należy zaimplementować interfejs <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Ta implementacja umożliwia usłudze danych Zwracanie danych binarnych jako strumienia do klienta i używanie danych binarnych jako strumienia wysyłanego z klienta. Usługa danych tworzy wystąpienie tego interfejsu za każdym razem, gdy musi uzyskać dostęp do danych binarnych jako strumień. Interfejs <xref:System.Data.Services.Providers.IDataServiceStreamProvider> określa następujące elementy członkowskie:

|Nazwa elementu członkowskiego|Opis|
|-----------------|-----------------|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Ta metoda jest wywoływana przez usługę danych w celu usunięcia odpowiedniego zasobu multimedialnego po usunięciu jego wpisu. Podczas implementowania <xref:System.Data.Services.Providers.IDataServiceStreamProvider>ta metoda zawiera kod, który usuwa zasób multimedialny skojarzony z podanym wpisem linku do nośnika.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Ta metoda jest wywoływana przez usługę danych w celu zwrócenia zasobu multimedialnego jako strumienia. W przypadku implementowania <xref:System.Data.Services.Providers.IDataServiceStreamProvider>ta metoda zawiera kod, który zapewnia strumień używany przez usługę danych do zasobu nośnika zwrotnego, który jest skojarzony z podanym wpisem nośnika.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Ta metoda jest wywoływana przez usługę danych w celu zwrócenia identyfikatora URI, który jest używany do żądania zasobu multimedialnego dla wpisu multimedia link. Ta wartość jest używana do tworzenia atrybutu `src` w elemencie zawartości wpisu Media link i używanego do żądania strumienia danych. Gdy ta metoda zwraca `null`, usługa danych automatycznie określa identyfikator URI. Tej metody należy użyć, jeśli trzeba zapewnić klientom bezpośredni dostęp do danych binarnych bez użycia dostawcy pary.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Ta metoda jest wywoływana przez usługę danych w celu zwrócenia wartości typu zawartości zasobu multimedialnego, która jest skojarzona z określonym wpisem linku do nośnika.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Ta metoda jest wywoływana przez usługę danych w celu zwrócenia elementu eTag strumienia danych skojarzonego z określoną jednostką. Ta metoda jest używana w przypadku zarządzania współbieżnością danych binarnych. Gdy ta metoda zwraca wartość null, usługa danych nie śledzi współbieżności.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Ta metoda jest wywoływana przez usługę danych w celu uzyskania strumienia, który jest używany podczas otrzymywania strumienia wysyłanego z klienta. Podczas implementowania <xref:System.Data.Services.Providers.IDataServiceStreamProvider>należy zwrócić zapisywalny strumień, do którego usługa danych zapisuje otrzymane dane strumienia.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Zwraca nazwę typu kwalifikowanego przestrzeni nazw reprezentującą typ, który musi zostać utworzony przez środowisko uruchomieniowe usługi danych dla wpisu linku do nośnika skojarzonego ze strumieniem danych w przypadku wstawianego zasobu multimedialnego.|

## <a name="creating-the-streaming-data-service"></a>Tworzenie usługi danych przesyłanych strumieniowo

Aby zapewnić środowisko uruchomieniowe Usługi danych programu WCF z dostępem do implementacji <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, tworzona usługa danych musi również implementować interfejs <xref:System.IServiceProvider>. Poniższy przykład pokazuje, jak zaimplementować metodę <xref:System.IServiceProvider.GetService%2A>, aby zwrócić wystąpienie klasy `PhotoServiceStreamProvider` implementującej <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.

[!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_service/cs/photodata.svc.cs#photoservicestreamingprovider)]
[!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_service/vb/photodata.svc.vb#photoservicestreamingprovider)]

Aby uzyskać ogólne informacje na temat tworzenia usługi danych, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Włączanie dużych strumieni binarnych w środowisku hostingu

Podczas tworzenia usługi danych w aplikacji sieci Web ASP.NET w celu zapewnienia implementacji protokołu HTTP jest używana Windows Communication Foundation (WCF). Domyślnie WCF ogranicza rozmiar komunikatów HTTP tylko do 65 KB. Aby można było przesyłać strumieniowo duże dane binarne do i z usługi danych, należy również skonfigurować aplikację sieci Web do włączania dużych plików binarnych i używania strumieni do transferu. W tym celu Dodaj następujące elementy w `<configuration />` elemencie pliku Web. config aplikacji:

> [!NOTE]
> Musisz użyć trybu transferu <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType>, aby upewnić się, że dane binarne w żądaniach i komunikatach odpowiedzi są przesyłane strumieniowo i nie są buforowane przez WCF.

Aby uzyskać więcej informacji, zobacz [transfer komunikatów przesyłania strumieniowego](../../wcf/feature-details/streaming-message-transfer.md) i [przydziały transportowe](../../wcf/feature-details/transport-quotas.md).

Domyślnie program Internet Information Services (IIS) ogranicza także rozmiar żądań do 4 MB. Aby umożliwić usłudze danych otrzymywanie strumieni o rozmiarze większym niż 4 MB podczas uruchamiania w usługach IIS, należy również ustawić atrybut `maxRequestLength` [elementu httpRuntime (Schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100)) w sekcji Konfiguracja `<system.web />`, jak pokazano w następującym przykładzie:

## <a name="using-data-streams-in-a-client-application"></a>Używanie strumieni danych w aplikacji klienckiej

Biblioteka klienta Usługi danych programu WCF umożliwia zarówno pobieranie, jak i aktualizowanie tych narażonych zasobów jako strumieni binarnych na kliencie. Aby uzyskać więcej informacji, zobacz [Praca z danymi binarnymi](working-with-binary-data-wcf-data-services.md).

## <a name="considerations-for-working-with-a-streaming-provider"></a>Zagadnienia dotyczące pracy z dostawcą przesyłania strumieniowego

Poniżej przedstawiono kwestie, które należy wziąć pod uwagę podczas implementowania dostawcy przesyłania strumieniowego i uzyskiwania dostępu do zasobów multimedialnych z usługi danych.

- Żądania scalania nie są obsługiwane w przypadku zasobów multimedialnych. Użyj żądania PUT, aby zmienić zasób multimedialny istniejącej jednostki.

- Żądania POST nie można użyć do utworzenia nowego wpisu łącza do nośnika. Zamiast tego należy wydać żądanie POST, aby utworzyć nowy zasób multimedialny, a usługa danych utworzy nowy wpis nośnika z wartościami domyślnymi. Ta nowa jednostka może zostać zaktualizowana przez kolejne żądanie scalania lub PUT. Możesz również rozważyć buforowanie jednostki i wprowadzić w niej aktualizacje, takie jak ustawienie wartości właściwości w nagłówku Sluga w żądaniu POST.

- Po odebraniu żądania POST usługa danych wywołuje <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>, aby utworzyć zasób multimedialny przed wywołaniem <xref:System.Data.Services.IUpdatable.SaveChanges%2A> w celu utworzenia wpisu multimediów.

- Implementacja <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> nie powinna zwracać obiektu <xref:System.IO.MemoryStream>. W przypadku użycia tego rodzaju strumienia problemy z zasobami pamięci będą wykonywane, gdy usługa otrzymuje bardzo duże strumienie danych.

- Poniżej przedstawiono kwestie, które należy wziąć pod uwagę podczas przechowywania zasobów multimedialnych w bazie danych programu:

  - Właściwość binarna, która jest zasobem multimedialnym, nie powinna być uwzględniona w modelu danych. Wszystkie właściwości uwidocznione w modelu danych są zwracane w wpisie w kanale informacyjnym odpowiedzi.

  - Aby zwiększyć wydajność przy użyciu dużego strumienia binarnego, zalecamy utworzenie niestandardowej klasy strumienia do przechowywania danych binarnych w bazie danych. Ta klasa jest zwracana przez implementację <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> i wysyła dane binarne do bazy danych w fragmentach. W przypadku bazy danych SQL Server zalecamy użycie obiektu FILESTREAM do przesyłania strumieniowego danych do bazy danych, gdy dane binarne są większe niż 1 MB.

  - Upewnij się, że baza danych została zaprojektowana do przechowywania plików binarnych, które mają być odbierane przez usługę danych.

  - Gdy klient wysyła żądanie POST w celu wstawienia wpisu nośnika z zasobem multimedialnym w pojedynczym żądaniu, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> jest wywoływana w celu uzyskania strumienia, zanim usługa danych umieści nową jednostkę w bazie danych. Implementacja dostawcy przesyłania strumieniowego musi być w stanie obsłużyć to zachowanie usługi danych. Rozważ użycie oddzielnej tabeli danych do przechowywania danych binarnych lub przechowywanie strumienia danych w pliku do momentu wstawienia obiektu do bazy danych.

- Podczas implementowania metod <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>lub <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> należy użyć wartości eTag i typu zawartości, które są dostarczane jako parametry metody. Nie ustawiaj elementów eTag ani Head-Type w implementacji dostawcy <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.

- Domyślnie klient wysyła duże strumienie binarne przy użyciu fragmentarycznego protokołu HTTP transferu. Ponieważ serwer ASP.NET Development nie obsługuje tego rodzaju kodowania, nie można użyć tego serwera sieci Web do hostowania usługi danych przesyłanych strumieniowo, która musi akceptować duże strumienie binarne. Aby uzyskać więcej informacji na temat ASP.NET Development Server, zobacz [serwery sieci Web w programie Visual Studio dla projektów sieci web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

<a name="versioning"></a>

## <a name="versioning-requirements"></a>Wymagania dotyczące wersji

Dostawca przesyłania strumieniowego ma następujące wymagania dotyczące wersji protokołu OData:

- Dostawca przesyłania strumieniowego wymaga, aby usługa danych obsługiwała wersję 2,0 protokołu OData i nowszych wersji.

Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](data-service-versioning-wcf-data-services.md).

## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Niestandardowi dostawcy usługi danych](custom-data-service-providers-wcf-data-services.md)
- [Praca z danymi binarnymi](working-with-binary-data-wcf-data-services.md)
