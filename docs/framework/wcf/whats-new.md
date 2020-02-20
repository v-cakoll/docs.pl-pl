---
title: Co nowego w wersji 4.5 programu WCF (Windows Communication Foundation)?
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
ms.openlocfilehash: b22266efe2e775acd04c400cf9da50bffab28183
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449507"
---
# <a name="whats-new-in-windows-communication-foundation-45"></a>Co nowego w wersji 4.5 programu WCF (Windows Communication Foundation)?

W tym temacie omówiono funkcje nowe do Windows Communication Foundation (WCF) w wersji 4,5.

## <a name="wcf-simplification-features"></a>Funkcje upraszczania programu WCF

Wiele pracy zostało wykonane, aby ułatwić tworzenie i konserwowanie aplikacji WCF 4,5. Aby uzyskać więcej informacji, zobacz [funkcje uproszczenia WCF](wcf-simplification-features.md).

### <a name="task-based-async-support"></a>Obsługa asynchroniczna oparta na zadaniach

Domyślnie usługa Dodaj odwołanie do usługi generuje metody asynchroniczne zwracające zadanie. Odbywa się to w przypadku metod synchronicznych i asynchronicznych. Pozwala to na asynchroniczne wywoływanie operacji usługi przy użyciu nowego modelu programowania asynchronicznego opartego na zadaniach. Po wywołaniu metody wygenerowanego serwera proxy WCF tworzy obiekt zadania do reprezentowania operacji asynchronicznej i zwraca to zadanie do użytkownika. Zadanie kończy się po zakończeniu operacji. Podczas implementowania operacji asynchronicznej można zaimplementować ją jako operację asynchroniczną opartą na zadaniach. Aby uzyskać więcej informacji, zobacz [Operacje synchroniczne i asynchroniczne](synchronous-and-asynchronous-operations.md).

### <a name="simplified-generated-configuration-files"></a>Uproszczone wygenerowane pliki konfiguracji

Dodanie odwołania do usługi w programie Visual Studio lub użycie narzędzia SvcUtil. exe powoduje wygenerowanie pliku konfiguracji klienta. W poprzednich wersjach programu WCF te pliki konfiguracji zawierały wartość każdej właściwości powiązania, nawet jeśli jej wartość jest wartością domyślną. W programie WCF 4,5 wygenerowane pliki konfiguracji zawierają tylko te właściwości powiązań, które mają ustawioną wartość różną od wartości domyślnej.

Aby uzyskać więcej informacji, zobacz [funkcje uproszczenia WCF](wcf-simplification-features.md).

### <a name="contract-first-development"></a>Kontrakt — pierwsze programowanie

Usługa WCF obsługuje teraz programowanie w pierwszej kolejności. Svcutil. exe ma przełącznik/serviceContract, który umożliwia generowanie kontraktów usługi i danych z dokumentu WSDL.

### <a name="add-service-reference-from-a-portable-subset-project"></a>Dodaj odwołanie do usługi z projektu podzestawu przenośnego

Przenośne projekty podzestawów umożliwiają programistom zestawu .NET utrzymywanie jednego drzewa źródłowego i systemu kompilacji przy zachowaniu obsługi wielu platform .NET (klasycznych, Silverlight, Windows Phone i Xbox). Przenośne projekty podzestawów odwołują się tylko do przenośnych bibliotek .NET, które są zestawami, których można używać na dowolnej platformie .NET. Środowisko programistyczne jest takie samo jak dodanie odwołania do usługi w ramach dowolnej innej aplikacji klienckiej WCF. Aby uzyskać więcej informacji, zobacz [Dodaj odwołanie do usługi w projekcie podzestawu przenośnego](add-service-reference-in-a-portable-subset-project.md).

### <a name="aspnet-compatibility-mode-default-changed"></a>Domyślne zmiany trybu zgodności ASP.NET

Funkcja WCF oferuje tryb zgodności ASP.NET, który umożliwia deweloperom pełen dostęp do funkcji w potoku HTTP ASP.NET podczas pisania usług WCF. Aby użyć tego trybu, należy ustawić atrybut `aspNetCompatibilityEnabled` na true w sekcji [\<serviceHostingEnvironment >](../configure-apps/file-schema/wcf/servicehostingenvironment.md) pliku Web. config. Ponadto wszystkie usługi w tej domenie appDomain muszą mieć Właściwość `RequirementsMode` na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ustawione na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Domyślnie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> jest teraz ustawiona na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. Aby uzyskać więcej informacji, zobacz [usługi WCF i ASP.NET](./feature-details/wcf-services-and-aspnet.md).

### <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu

W celu uproszczenia konfiguracji zmieniono wiele wartości domyślnych właściwości transportu. Aby uzyskać więcej informacji, zobacz [funkcje uproszczenia WCF](wcf-simplification-features.md).

### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas> zawiera konfigurowalne wartości przydziału dla czytników słownika XML, które ograniczają ilość pamięci używaną przez koder podczas tworzenia komunikatu. Podczas konfigurowania tych przydziałów wartości domyślne uległy zmianie, aby zmniejszyć prawdopodobieństwo, że deweloper będzie musiał je jawnie ustawić. Aby uzyskać więcej informacji, zobacz [funkcje uproszczenia WCF](wcf-simplification-features.md).

### <a name="wcf-configuration-validation"></a>Sprawdzanie poprawności konfiguracji WCF

W ramach procesu kompilacji w programie Visual Studio pliki konfiguracji WCF są teraz weryfikowane pod kątem atrybutów zdefiniowanych w ramach projektu. Lista błędów lub ostrzeżeń dotyczących sprawdzania poprawności jest wyświetlana w programie Visual Studio, jeśli sprawdzanie poprawności zakończy się niepowodzeniem.

### <a name="xml-editor-tooltips"></a>Etykietki narzędzi edytora XML

Aby ułatwić nowym i istniejącym deweloperom usług WCF Konfigurowanie swoich usług, Edytor XML programu Visual Studio udostępnia teraz etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które są częścią pliku konfiguracji usługi.

## <a name="streaming-improvements"></a>Udoskonalenia przesyłania strumieniowego

Dodano obsługę asynchronicznego przesyłania strumieniowego, w którym strona wysyłania nie blokuje wątków, jeśli po stronie odbierającej nie jest odczytywany lub wolniejszy odczyt, co zwiększa skalowalność. Usunięto ograniczenie buforowania komunikatów, gdy klient wysyła strumieniowo komunikat do hostowanej usługi WCF usług IIS. Aby uzyskać więcej informacji, zobacz [funkcje uproszczenia WCF](wcf-simplification-features.md).

## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>Uproszczenie ujawniania punktu końcowego za pośrednictwem protokołu HTTPS za pomocą usług IIS

Zostało dodane Mapowanie protokołu HTTPS w celu uproszczenia ujawniania punktu końcowego za pośrednictwem protokołu HTTPS. Aby włączyć punkt końcowy HTTPS, upewnij się, że witryna sieci Web ma skonfigurowane powiązanie HTTPS i certyfikat SSL, a następnie po prostu Włącz protokół HTTPS dla katalogu wirtualnego, który obsługuje tę usługę. Jeśli dla usługi włączono obsługę metadanych, zostanie ona również udostępniona za pośrednictwem protokołu HTTPS.

## <a name="generating-a-single-wsdl-document"></a>Generowanie pojedynczego dokumentu WSDL

Niektóre stosy przetwarzania WSDL innych firm nie mogą przetwarzać dokumentów WSDL, które mają zależności od innych dokumentów za pomocą pliku XSD: import. Funkcja WCF umożliwia teraz określenie, że wszystkie informacje WSDL mają być zwracane w pojedynczym dokumencie. Aby zażądać jednego dokumentu WSDL, Dołącz "? singleWSDL" do identyfikatora URI podczas żądania metadanych z usługi.

## <a name="websocket-support"></a>Obsługa protokołu WebSocket

WebSockets to technologia, która zapewnia prawdziwą komunikację dwukierunkową za pośrednictwem portów 80 i 443 z charakterystykami wydajności podobnymi do protokołu TCP. Dodano dwa nowe powiązania do obsługi komunikacji za pośrednictwem transportu protokołu WebSocket. <xref:System.ServiceModel.NetHttpBinding> i <xref:System.ServiceModel.NetHttpsBinding>. Aby uzyskać więcej informacji, zobacz: [powiązania dostarczone przez system](system-provided-bindings.md).

## <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu

W poniższej tabeli opisano ustawienia, które zostały zmienione i gdzie można znaleźć dodatkowe informacje.

|Właściwość|Włączone|Nowe domyślne|Aby uzyskać więcej informacji, zobacz|
|--------------|--------|-----------------|------------------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * liczba procesorów|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * Liczba procesorów do transportu<br /><br /> 4 \* liczba procesorów dla programu SMSvcHost. exe|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [konfigurowania usługi udostępniania portów Net. TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * liczba procesorów|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 sekund|[Konfigurowanie usługi współużytkowania portów Net.TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|

## <a name="xml-editor-tooltips"></a>Etykietki narzędzi edytora XML

Aby ułatwić nowym i istniejącym deweloperom usług WCF Konfigurowanie swoich usług, Edytor XML programu Visual Studio udostępnia teraz etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które są częścią pliku konfiguracji usługi.

## <a name="configuring-wcf-services-in-code"></a>Konfigurowanie usług WCF w kodzie

Windows Communication Foundation (WCF) umożliwia deweloperom Konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu. Pliki konfiguracji są przydatne, gdy usługa musi zostać skonfigurowana po wdrożeniu. W przypadku korzystania z plików konfiguracji Specjalista IT musi tylko zaktualizować plik konfiguracji, nie jest wymagana ponowna kompilacja. Pliki konfiguracji mogą jednak być skomplikowane i trudne do utrzymania. Nie ma obsługi debugowania plików konfiguracji i elementów konfiguracji, do których odwołują się nazwy, co sprawia, że pliki konfiguracji tworzenia są podatne na błędy i trudne. Funkcja WCF umożliwia również Konfigurowanie usług w kodzie. We wcześniejszych wersjach programu WCF (4,0 i starszych) Konfigurowanie usług w kodzie było łatwe w scenariuszach samodzielnej obsługi, ale Klasa <xref:System.ServiceModel.ServiceHost> może skonfigurować punkty końcowe i zachowania przed wywołaniem ServiceHost. Open. Nie ma jednak dostępu do klasy <xref:System.ServiceModel.ServiceHost> w scenariuszach hostowanych w sieci Web. Aby skonfigurować usługę hostowaną w sieci Web, należy utworzyć `System.ServiceModel.ServiceHostFactory`, które utworzyły <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać dowolną potrzebną konfigurację. Począwszy od platformy .NET 4,5, WCF oferuje łatwiejszy sposób konfigurowania usług samodzielnych i hostowanych w sieci Web w kodzie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług WCF w kodzie](configuring-wcf-services-in-code.md).

## <a name="channelfactory-caching"></a>Buforowanie elementu ChannelFactory

Aplikacje klienckie WCF używają klasy <xref:System.ServiceModel.ChannelFactory%601> do tworzenia kanału komunikacyjnego z usługą WCF. Tworzenie wystąpień <xref:System.ServiceModel.ChannelFactory%601> wiąże się z pewnym obciążeniem, ponieważ obejmuje następujące operacje:

1. Konstruowanie drzewa <xref:System.ServiceModel.Description.ContractDescription>

2. Odzwierciedlanie wszystkich wymaganych typów CLR

3. Konstruowanie stosu kanału

4. Usuwanie zasobów

Aby zminimalizować obciążenie, usługa WCF może buforować fabryki kanałów w przypadku korzystania z serwera proxy klienta WCF. Aby uzyskać więcej informacji, zobacz [Fabryka kanałów i buforowanie](./feature-details/channel-factory-and-caching.md).

## <a name="compression-and-the-binary-encoder"></a>Kompresja i koder binarny

Począwszy od programu WCF 4,5 koder binarny WCF dodaje obsługę kompresji. Typ kompresji jest konfigurowany przy użyciu właściwości <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A>. Zarówno klient, jak i usługa, muszą skonfigurować właściwość <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A>. Kompresja będzie działała dla protokołów HTTP, HTTPS i TCP. Jeśli klient określi, aby używać kompresji, ale usługa nie obsługuje tej funkcji, zgłaszany jest wyjątek protokołu wskazujący niezgodność protokołu. Aby uzyskać więcej informacji, zobacz [Wybieranie kodera komunikatów](./feature-details/choosing-a-message-encoder.md).

## <a name="udp"></a>UDP

Dodano obsługę transportu UDP, która pozwala deweloperom pisać usługi korzystające z komunikatów "Fire i zapomnij". Klient wysyła komunikat do usługi i oczekuje braku odpowiedzi z usługi.

## <a name="multiple-authentication-support"></a>Obsługa wielu uwierzytelnień

Dodano obsługę obsługi wielu trybów uwierzytelniania, które są obsługiwane przez usługi IIS, w jednym punkcie końcowym WCF w przypadku korzystania z transportu HTTP i zabezpieczeń transportu. Usługi IIS umożliwiają włączenie wielu trybów uwierzytelniania w katalogu wirtualnym. Ta funkcja umożliwia pojedynczemu punktowi końcowemu WCF obsługę wielu trybów uwierzytelniania włączonych dla katalogu wirtualnego, w którym jest hostowana usługa WCF.

## <a name="idn-support"></a>Obsługa IDN

Dodano obsługę, która umożliwia obsługę usług WCF przy użyciu międzynarodowych nazw domen. Aby uzyskać więcej informacji [, zobacz WCF i międzynarodowe nazwy domen](./feature-details/wcf-and-internationalized-domain-names.md).

## <a name="httpclient"></a>Klasy HttpClient

Dodano nową klasę o nazwie <xref:System.Net.Http.HttpClient>, która znacznie ułatwia pracę z żądaniami HTTP. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji społecznościowych i połączonych z usługami http](https://channel9.msdn.com/Events/BUILD/BUILD2011/PLAT-581T) oraz [przykładem klienta http](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).

## <a name="configuration-intellisense"></a>Konfiguracja IntelliSense

Wartości atrybutów w plikach konfiguracji dla atrybutów niestandardowych zdefiniowanych w projekcie obsługują teraz technologię IntelliSense, która ułatwia szybkie i precyzyjne pracę z konfiguracjami.

## <a name="configuration-tooltips"></a>Etykietki narzędzi konfiguracji

Elementy i atrybuty programu WCF mają teraz etykietki narzędzi w edytorze XML, aby łatwiej i precyzyjnie identyfikować przeznaczenie elementu lub atrybutu.

## <a name="paste-data-as-classes"></a>Wklej dane jako klasy

W projekcie WCF typy danych zdefiniowane w kodzie XML (takie jak są uwidocznione w usłudze) można wkleić bezpośrednio do strony kodowej. Typ XML zostanie wklejony jako typ CLR. Aby uzyskać więcej informacji, zobacz [generowanie klas typu danych z pliku XML](generating-data-type-classes-from-xml.md) .

## <a name="webservicehost-and-default-endpoints"></a>WebServiceHost i domyślne punkty końcowe

W programie Visual Studio 2010 WebServiceHost automatycznie utworzył domyślny punkt końcowy, niezależnie od tego, czy jawnie określono punkt końcowy. W programie Visual Studio 2012 i nowszych WebServiceHost tylko domyślny punkt końcowy, jeśli nie dodano żadnych punktów końcowych. Jeśli klient oczekuje domyślnego punktu końcowego, można jawnie dodać punkt końcowy i wskazać go klientowi. Alternatywnie możesz poinstruować funkcję WCF, aby przywrócić poprzednie zachowanie, dodając następujące ustawienie do pliku konfiguracji aplikacji

```xml
<appSettings>
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>
  </appSettings>
```

## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager

Ten interfejs, uwidoczniony przez <xref:System.ServiceModel.Channels.IChannelFactory%601>, ułatwia pracę z plikami cookie po stronie klienta. Gdy AllowCookies jest ustawiona na wartość true dla powiązania, można uzyskać dostęp do plików cookie przy użyciu następującego kodu:

```csharp
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();
System.Net.CookieContainer container = cookieManager.CookieContainer;
```

Następnie można pobrać lub ustawić pliki cookie z <xref:System.Net.CookieContainer>. Gdy AllowCookies jest ustawiona na false, można ręcznie pobrać pliki cookie przy użyciu <xref:System.ServiceModel.OperationContext> i wysłać je w innych żądaniach przy użyciu innego <xref:System.ServiceModel.OperationContext> lub Inspektora komunikatów. Interfejs IHttpCookieContainerManager umożliwia uwierzytelnienie użytkownika za pomocą usługi i używanie pliku cookie uwierzytelniania zwróconego przez tę usługę do uwierzytelniania z innymi usługami.
