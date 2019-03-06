---
title: Co nowego w wersji 4.5 programu WCF (Windows Communication Foundation)?
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
ms.openlocfilehash: 8d079613d1970d2a50ddb3449c2a3072010b2c55
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358322"
---
# <a name="whats-new-in-windows-communication-foundation-45"></a>Co nowego w wersji 4.5 programu WCF (Windows Communication Foundation)?

W tym temacie omówiono funkcje nowych do Windows Communication Foundation (WCF) w wersji 4.5.

## <a name="wcf-simplification-features"></a>Funkcje upraszczania programu WCF
 Aby ułatwić rozwijania i utrzymywania aplikacji WCF 4.5 zostało zrobione dużo pracy. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="task-based-async-support"></a>Oparta na zadaniach asynchroniczna pomoc techniczna
 Domyślnie Dodaj odwołanie do usługi generuje metody operację zwracającą zadanie usługi async. Jest to wykonywane synchroniczne i asynchroniczne metody. Umożliwia wywoływanie operacji usługi asynchronicznie przy użyciu nowego modelu programowania async oparte na zadaniach. Po wywołaniu metody wygenerowany serwer proxy, WCF konstruuje obiekt zadanie reprezentujące operację asynchroniczną i zwraca wartość, które zadania do Ciebie. Zadanie kończy się po zakończeniu operacji.  Podczas wykonywania operacji asynchronicznej można wdrożyć go jako operacja opartego na zadaniach asynchronicznej. Aby uzyskać więcej informacji, zobacz [synchroniczne i asynchroniczne operacje](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).

### <a name="simplified-generated-configuration-files"></a>Uproszczony wygenerowanych plików konfiguracyjnych
 Podczas dodawania odwołania do usługi w programie Visual Studio lub za pomocą narzędzia SvcUtil.exe, generowany jest plik konfiguracji klienta. W poprzednich wersjach programu WCF te pliki konfiguracji zawarte wartości dla każdej właściwości powiązania, nawet wtedy, gdy jego wartość jest wartością domyślną. W programie WCF 4.5 wygenerowanych plików konfiguracyjnych zawiera tylko te właściwości powiązania, które są ustawione na wartości innych niż domyślne.

 Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md)

### <a name="contract-first-development"></a>Programowanie Contract-First
 Usługi WCF dodano wsparcie dla programowania z wymogiem wcześniejszego zawarcia kontraktu. Svcutl.exe ma przełącznik /serviceContract, który umożliwia generowanie kontraktów usług i danych z dokumentu WSDL.

### <a name="add-service-reference-from-a-portable-subset-project"></a>Dodaj odwołanie do usługi w projekcie obsługującym podzestaw przenośny
 Projekty obsługującym podzestaw przenośny umożliwiają deweloperom zestawu .NET do utrzymywania drzewa pojedyncze źródło i systemu kompilacji, nadal obsługując wiele platform .NET (pulpitu, Silverlight, Windows Phone i XBOX). Projekty obsługującym podzestaw przenośny tylko odwołania do bibliotek przenośnych platformy .NET, będące zestawu .NET framework używany na dowolnej platformie .NET. Środowisko programistyczne jest taka sama jak dodawanie odwołania do usługi w ramach innej aplikacji klienckich programu WCF. Aby uzyskać więcej informacji, zobacz [Dodaj odwołanie do usługi w przenośnych projekcie obsługującym podzestaw](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).

### <a name="aspnet-compatibility-mode-default-changed"></a>Domyślne tryb zgodności ASP.NET zostało zmienione
 Usługi WCF zapewnia tryb zgodności ASP.NET do udzielania deweloperów pełny dostęp do funkcji w potoku HTTP programu ASP.NET, podczas zapisywania usług WCF. Aby użyć tego trybu, należy ustawić `aspNetCompatibilityEnabled` atrybut na wartość true w [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) sekcja pliku Web.config. Ponadto każda usługa, w tym elemencie appDomain musi mieć `RequirementsMode` właściwość jego <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> równa <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Domyślnie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> są teraz ustawione na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. Aby uzyskać więcej informacji, zobacz [What's New in Windows Communication Foundation](../../../docs/framework/wcf/whats-new.md) i [usługi WCF i platforma ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).

### <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu
 Aby uprościć konfigurację, które uległy zmianie wartości domyślnej właściwości transportu. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
 <xref:System.Xml.XmlDictionaryReaderQuotas> zawiera wartości zasobów można skonfigurować dla czytelników słownika XML, które ograniczają ilość pamięci wykorzystywany przez koder podczas tworzenia komunikatu. Mimo że tych limitów przydziału można skonfigurować, wartości domyślne zostały zmienione na zmniejszenie prawdopodobieństwa, że projektant będzie musiał ustawiony w sposób jawny. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

### <a name="wcf-configuration-validation"></a>Sprawdzanie poprawności konfiguracji programu WCF
 Jako część procesu kompilacji w programie Visual Studio WCF, pliki konfiguracyjne są teraz sprawdzane dla atrybuty zdefiniowane w projekcie. Lista ostrzeżeń ani błędów sprawdzania poprawności jest wyświetlany w programie Visual Studio, jeśli weryfikacja zakończy się niepowodzeniem.

### <a name="xml-editor-tooltips"></a>XML Editor Tooltips
 W celu ułatwić nowych i istniejących deweloperzy usług WCF do konfigurowania swoich usług, edytorze XML Visual Studio teraz udostępnia etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które jest częścią pliku konfiguracji usługi.

## <a name="streaming-improvements"></a>Ulepszenia przesyłania strumieniowego
 Dodano obsługę true asynchronicznego przesyłania strumieniowego gdzie stronie wysyłania teraz nie blokuje wątków, jeśli nie odczytuje po stronie odbierania lub wolno podczas odczytu, co powoduje zwiększenie skalowalności. Usunąć ograniczenie komunikat buforowania, gdy klient wysyła, że usługi WCF hostowanej strumieniowej wiadomości usług IIS. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).

## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>Upraszczanie udostępnianie punktu końcowego za pośrednictwem protokołu HTTPS za pomocą programu IIS
 Mapowanie protokołu HTTPS, dodano ułatwiają udostępnianie punktu końcowego za pośrednictwem protokołu HTTPS. Aby włączyć punkt końcowy HTTPS, upewnij się, że powiązanie HTTPS i certyfikatu SSL skonfigurowanego witryny sieci Web, a następnie po prostu włączyć protokół HTTPS dla katalogu wirtualnego, który jest hostem usługi. Jeśli metadane są włączone dla usługi, będzie go udostępniane za pośrednictwem protokołu HTTPS także.

## <a name="generating-a-single-wsdl-document"></a>Generuje dokument WSDL pojedynczego
 Niektóre stosów przetwarzania WSDL innych firm nie są przetworzyć dokumenty WSDL, które mają zależności w innych dokumentów za pośrednictwem: import.  Usługi WCF umożliwia teraz określić, że wszystkie informacje o WSDL zwrócone w jednym dokumencie. Żądanie dołączenia pojedynczym dokumencie WSDL "? singleWSDL" do identyfikatora URI, gdy żąda metadanych usługi.

## <a name="websocket-support"></a>Obsługa protokołu WebSocket
 Funkcja WebSockets jest to technologia, która zapewnia komunikację dwukierunkową przez porty 80 i 443 charakterystyki wydajności podobny do protokołu TCP. Dodano dwa nowe powiązania na potrzeby obsługi komunikacji za pośrednictwem protokołu WebSocket transportu. <xref:System.ServiceModel.NetHttpBinding> i <xref:System.ServiceModel.NetHttpsBinding>. Aby uzyskać więcej informacji, zobacz: [Powiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu
 W poniższej tabeli opisano ustawienia, które zostały zmienione i gdzie można znaleźć dodatkowe informacje.

|Właściwość|On|Nowe rozwiązanie domyślne|Aby uzyskać więcej informacji, zobacz|
|--------------|--------|-----------------|------------------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * liczba procesorów|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * liczba procesorów dla transportu<br /><br /> 4 \* liczby procesorów dla SMSvcHost.exe|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Konfigurowanie usługi współużytkowania portów Net.TCP](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * liczba procesorów|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 sekund|[Konfigurowanie usługi współużytkowania portów Net.TCP](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)|

## <a name="xml-editor-tooltips"></a>XML Editor Tooltips
 W celu ułatwić nowych i istniejących deweloperzy usług WCF do konfigurowania swoich usług, edytorze XML Visual Studio teraz udostępnia etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które jest częścią pliku konfiguracji usługi.

## <a name="configuring-wcf-services-in-code"></a>Konfigurowanie usług WCF w kodzie
 Windows Communication Foundation (WCF) umożliwia deweloperom konfigurowanie usług za pomocą plików konfiguracji lub kodu.  Pliki konfiguracyjne są przydatne, gdy usługa musi zostać skonfigurowane po wdrożeniu. Korzystając z plików konfiguracji, specjalistów IT wystarczy zaktualizować plik konfiguracji, nie ponownej kompilacji jest wymagana. Pliki konfiguracyjne, może jednak być złożone i trudne w utrzymaniu. Brak obsługi debugowania plików konfiguracji i elementy konfiguracji odwołują się nazwy, co sprawia, że pliki konfiguracji tworzenia podatne na błędy i trudne. WCF umożliwia również skonfigurowanie usługi w kodzie. We wcześniejszych wersjach, konfigurowanie usług WCF (4.0 i starszych) w kodzie jest łatwe w scenariuszach Self-Hosted <xref:System.ServiceModel.ServiceHost> klasa dozwolona można skonfigurować punkty końcowe i zachowania przed wywołaniem ServiceHost.Open. W scenariuszach hostowanych w sieci web, jednak nie masz dostępu do <xref:System.ServiceModel.ServiceHost> klasy. Aby skonfigurować sieci web hostowanych usług, które są wymagane do utworzenia `System.ServiceModel.ServiceHostFactory` utworzonego <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać wszelkie wymagane konfiguracji. Począwszy od .NET 4.5 programu WCF zapewnia łatwiejszy sposób skonfigurować zarówno może być samodzielnie hostowane i sieci web hostowanej usługi w kodzie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług WCF w kodzie](../../../docs/framework/wcf/configuring-wcf-services-in-code.md).

## <a name="channelfactory-caching"></a>Buforowanie elementu ChannelFactory
 Aplikacje klienta WCF <xref:System.ServiceModel.ChannelFactory%601> klasy, aby utworzyć kanał komunikacji z usługą WCF.  Tworzenie <xref:System.ServiceModel.ChannelFactory%601> wystąpień powoduje pewne nadmiarowe obciążenie, ponieważ obejmuje ona następujące operacje:

1.  Konstruowanie <xref:System.ServiceModel.Description.ContractDescription> drzewa

2.  Odzwierciedlenie wszystkich wymaganych typów CLR

3.  Konstruowanie stosu kanału

4.  Usuwanie zasobów

 Aby zminimalizować ten narzut, WCF może buforować fabryki kanałów, korzystając z serwera proxy klienta WCF. Aby uzyskać więcej informacji, zobacz [fabryki kanałów i buforowanie](../../../docs/framework/wcf/feature-details/channel-factory-and-caching.md).

## <a name="compression-and-the-binary-encoder"></a>Kompresja i kodera binarnego
 Począwszy od programu WCF 4.5 kodera binarnego WCF dodaje obsługę kompresji. Typ kompresji jest skonfigurowany przy użyciu <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> właściwości. Należy skonfigurować zarówno klient, jak i usługa <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> właściwości. Kompresja będzie działać w przypadku protokołów HTTP, HTTPS i TCP. Jeśli klient określa, aby skorzystać z kompresji, ale usługa nie obsługuje protokołu wyjątku wskazująca niezgodności protokołu. Aby uzyskać więcej informacji, zobacz [Wybieranie kodera komunikatów](../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)

## <a name="udp"></a>UDP
 Dodano obsługę dla transportu UDP, która umożliwia programistom pisanie usług korzystających z "fire and forget" wiadomości. Klient wysyła komunikat do usługi i oczekuje odpowiedzi z usługi.

## <a name="multiple-authentication-support"></a>Obsługa wielu uwierzytelniania
 Dodano obsługę do obsługi wielu trybów uwierzytelniania jako obsługiwane przez usługi IIS, w jednym punkcie końcowym WCF podczas korzystania z transportu HTTP i zabezpieczeń transportu. Usługi IIS umożliwia wielu trybów uwierzytelniania w katalogu wirtualnym, ta funkcja pozwala jednym punkcie końcowym WCF do obsługi wielu trybów uwierzytelniania włączane dla katalogu wirtualnego, w którym jest hostowana usługa WCF.

## <a name="idn-support"></a>Obsługa IDN
 Dodano obsługę do obsługi usług WCF za pomocą międzynarodowych nazw domen. Aby uzyskać więcej informacji, zobacz [WCF i międzynarodowe nazwy domen](../../../docs/framework/wcf/feature-details/wcf-and-internationalized-domain-names.md).

## <a name="httpclient"></a>Klasy HttpClient
 Nową klasę o nazwie <xref:System.Net.Http.HttpClient> została dodana do znacznie ułatwić pracę z żądania HTTP. Aby uzyskać więcej informacji, zobacz [społecznościowych i połączony z usług HTTP, dzięki czemu aplikacje](https://go.microsoft.com/fwlink/?LinkId=231886) i [przykładem klienta HTTP](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).

## <a name="configuration-intellisense"></a>Konfiguracja funkcji Intellisense
 Wartości atrybutów w plikach konfiguracyjnych dla atrybuty niestandardowe zdefiniowane w projekcie teraz obsługi technologii intellisense w celu ułatwienia pracy z konfiguracjami, szybko i dokładnie.

## <a name="configuration-tooltips"></a>Etykietki narzędzi konfiguracji
 Atrybuty i elementy programu WCF teraz łatwiej trzeba etykietki narzędzi w edytorze XML i precyzyjne określenie przeznaczenia elementu lub atrybutu.

## <a name="paste-data-as-classes"></a>Wklej dane jako klasy
 W projekcie usługi WCF typów danych zdefiniowanych w pliku XML (takie jak są widoczne w usłudze) można wkleić bezpośrednio do strony kodowej. Typ XML zostaną wklejone jako typu CLR. Zobacz [Generowanie klas typów danych z pliku XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md) Aby uzyskać więcej informacji.

## <a name="webservicehost-and-default-endpoints"></a>Typ WebServiceHost i domyślne punkty końcowe
 W programie Visual Studio 2010 Typ WebServiceHost automatycznie tworzone domyślny punkt końcowy, czy jawnie określono punktu końcowego lub nie. W programie Visual Studio 2012 i nowszych Typ WebServiceHost tylko tworzy domyślny punkt końcowy, jeśli punkty końcowe nie są jawnie dodawane. Jeśli Twój klient oczekuje domyślnego punktu końcowego można jawnie dodać punkt końcowy i wskaż klienta. Alternatywnie można stwierdzić, WCF, aby przywrócić poprzednie zachowanie, dodając następujące ustawienie do pliku konfiguracji aplikacji

```xml
<appSettings>
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>
  </appSettings>
```

## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager
 Ten interfejs udostępnianych przez <xref:System.ServiceModel.Channels.IChannelFactory%601>, sprawia, że praca z plików cookie po stronie klienta znacznie łatwiejsze. Gdy AllowCookies jest ustawiona na wartość true w powiązaniu, możesz uzyskać dostęp plików cookie przy użyciu następującego kodu:

```csharp
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();
System.Net.CookieContainer container = cookieManager.CookieContainer;
```

 Możesz pobierać lub ustawiać pliki cookie z <xref:System.Net.CookieContainer>. AllowCookies jest ustawiony na wartość false, można ręcznie pobrać, plikami cookie przy użyciu <xref:System.ServiceModel.OperationContext> i wysłać je w innych żądaniach przy użyciu innego <xref:System.ServiceModel.OperationContext> lub Inspektora wiadomości. Interfejs IHttpCookieContainerManager umożliwia uwierzytelnianie użytkowników za pomocą usługi i używaj plików cookie uwierzytelniania, zwracany przez tę usługę do uwierzytelniania za pomocą innych usług.
