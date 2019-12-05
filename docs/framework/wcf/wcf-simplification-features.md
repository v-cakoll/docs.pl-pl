---
title: Funkcje upraszczania programu WCF
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: dd944ad2963e29fd3aa9254f3a37f2c2b98ce70d
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802391"
---
# <a name="wcf-simplification-features"></a>Funkcje upraszczania programu WCF

W tym temacie omówiono nowe funkcje, które ułatwiają zapisywanie aplikacji WCF.

## <a name="simplified-generated-configuration-files"></a>Uproszczone wygenerowane pliki konfiguracji

Dodanie odwołania do usługi w programie Visual Studio lub użycie narzędzia SvcUtil. exe powoduje wygenerowanie pliku konfiguracji klienta. W poprzednich wersjach programu WCF te pliki konfiguracji zawierały wartość każdej właściwości powiązania, nawet jeśli jej wartość jest wartością domyślną. W programie WCF 4,5 wygenerowane pliki konfiguracji zawierają tylko te właściwości powiązań, które mają ustawioną wartość różną od wartości domyślnej.

Poniżej znajduje się przykładowy plik konfiguracyjny generowany przez program WCF 3,0.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"
                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"
                    allowCookies="false" bypassProxyOnLocal="false"
                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536"
                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"
                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"
                    useDefaultWebProxy="true">
                    <readerQuotas maxDepth="32" maxStringContentLength="8192"
                        maxArrayLength="16384" maxBytesPerRead="4096"
                        maxNameTableCharCount="16384" />
                    <security mode="None">
                        <transport clientCredentialType="None" proxyCredentialType="None"
                            realm="" />
                        <message clientCredentialType="UserName" algorithmSuite="Default" />
                    </security>
                </binding>
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

Poniżej znajduje się przykład tego samego pliku konfiguracji, który został wygenerowany przez program WCF 4,5.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" />
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

## <a name="contract-first-development"></a>Kontrakt — pierwsze programowanie

Usługa WCF obsługuje teraz programowanie w pierwszej kolejności. Narzędzie Svcutil. exe ma przełącznik/serviceContract, który umożliwia generowanie kontraktów usługi i danych z dokumentu WSDL.

## <a name="add-service-reference-from-a-portable-subset-project"></a>Dodaj odwołanie do usługi z projektu podzestawu przenośnego

Przenośne projekty podzestawów umożliwiają programistom zestawu .NET utrzymywanie jednego drzewa źródłowego i systemu kompilacji przy zachowaniu obsługi wielu implementacji platformy .NET (Desktop, Silverlight, Windows Phone i XBOX). Przenośne projekty podzestawów odwołują się tylko do przenośnych bibliotek platformy .NET, które są zestawami programu .NET Framework, które mogą być używane w dowolnej implementacji platformy .NET. Środowisko programistyczne jest takie samo jak dodanie odwołania do usługi w ramach dowolnej innej aplikacji klienckiej WCF. Aby uzyskać więcej informacji, zobacz [Dodaj odwołanie do usługi w projekcie podzestawu przenośnego](add-service-reference-in-a-portable-subset-project.md).

## <a name="aspnet-compatibility-mode-default-changed"></a>Domyślne zmiany trybu zgodności ASP.NET

Funkcja WCF oferuje tryb zgodności ASP.NET, który umożliwia deweloperom pełen dostęp do funkcji w potoku HTTP ASP.NET podczas pisania usług WCF. Aby użyć tego trybu, należy ustawić atrybut `aspNetCompatibilityEnabled` na true w sekcji [\<serviceHostingEnvironment >](../configure-apps/file-schema/wcf/servicehostingenvironment.md) pliku Web. config. Ponadto wszystkie usługi w tej domenie appDomain muszą mieć Właściwość `RequirementsMode` na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ustawione na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Domyślnie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> jest teraz ustawiona na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, a domyślny szablon aplikacji usługi WCF ustawia atrybut `aspNetCompatibilityEnabled` na `true`. Aby uzyskać więcej informacji, zobacz [co nowego w Windows Communication Foundation 4,5](whats-new.md) oraz [usługach WCF i ASP.NET](./feature-details/wcf-services-and-aspnet.md).

## <a name="streaming-improvements"></a>Udoskonalenia przesyłania strumieniowego

- Dodano nową obsługę przesyłania strumieniowego asynchronicznego do programu WCF. Aby włączyć asynchroniczne przesyłanie strumieniowe, Dodaj zachowanie punktu końcowego <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> do hosta usługi i ustaw jego właściwość <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> na `true`. Pozwala to na skalowalność, gdy usługa wysyła przesyłane strumieniowo komunikaty do wielu klientów. Funkcja WCF nie blokuje już jednego wątku na klienta i zwalnia wątek, aby obsłużyć inny klient.

- Usunięto ograniczenia dotyczące buforowania komunikatów, gdy usługa jest hostowana w usługach IIS. W poprzednich wersjach programu WCF podczas otrzymywania komunikatu dla usługi hostowanej przez usługi IIS, która używa transferu komunikatów przesyłania strumieniowego, ASP.NET buforuje cały komunikat przed wysłaniem go do programu WCF. Mogłoby to spowodować duże użycie pamięci. To buforowanie zostało usunięte w programie .NET 4,5, a teraz usługi WCF hostowane przez usługi IIS mogą rozpocząć przetwarzanie strumienia przychodzącego przed odebraniem całego komunikatu, co pozwoli na prawdziwe przesyłanie strumieniowe. Dzięki temu Funkcja WCF może natychmiast reagować na komunikaty i zapewnia lepszą wydajność. Ponadto nie trzeba już określać wartości `maxRequestLength`ASP.NET limit rozmiaru żądań przychodzących. Jeśli ta właściwość jest ustawiona, zostanie zignorowana. Aby uzyskać więcej informacji na temat `maxRequestLength` zobacz [\<httpRuntime > Configuration](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/e1f13641(v=vs.71)). Nadal musisz skonfigurować maxAllowedContentLength, aby uzyskać więcej informacji, zobacz [limity żądań usług IIS](https://docs.microsoft.com/previous-versions/iis/settings-schema/ms689462(v=vs.90)).

## <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu

W poniższej tabeli opisano ustawienia, które zostały zmienione i gdzie można znaleźć dodatkowe informacje.

|Właściwość|On|Nowe domyślne|Więcej informacji|
|--------------|--------|-----------------|----------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|Ta właściwość określa, jak długo może upłynąć połączenie TCP w celu samodzielnego uwierzytelnienia przy użyciu protokołu szkieletowego platformy .NET. Klient musi wysłać pewne dane początkowe, zanim serwer będzie miał wystarczającą ilość informacji do przeprowadzenia uwierzytelniania. Ten limit czasu jest celowo mniejszy niż ReceiveTimeout (10 min), dzięki czemu złośliwi klienci nieuwierzytelniony nie zachowują połączeń na serwerze przez długi czas. Wartość domyślna to 30 sekund. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * liczba procesorów|Ta właściwość na poziomie gniazda opisuje liczbę żądań oczekujących na przyłączenie do kolejki. Jeśli kolejka zaległości nasłuchiwania zostanie wypełniania, nowe żądania gniazda zostaną odrzucone. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * Liczba procesorów do transportu<br /><br /> 4 \* liczba procesorów dla programu SMSvcHost. exe|Ta właściwość ogranicza liczbę kanałów, które serwer może oczekiwać na odbiornik. Gdy MaxPendingAccepts jest zbyt niska, będzie to niewielki przedział czasu, w którym wszystkie kanały oczekujące rozpoczęły obsługę połączeń, ale żadne nowe kanały nie rozpoczęły nasłuchiwania. Połączenie może zostać odebrane w tym interwale i zakończy się niepowodzeniem, ponieważ nic nie czeka na serwer. Tę właściwość można skonfigurować przez ustawienie właściwości <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> na większą liczbę. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> i [Konfigurowanie usługi udostępniania portów Net. TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * liczba procesorów|Ta właściwość określa, ile połączeń zaakceptowanych przez transport, ale nie zostało pobranych przez dyspozytora ServiceModel. Aby ustawić tę wartość, użyj `MaxConnections` na powiązanie lub `maxOutboundConnectionsPerEndpoint` elementu Binding. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 sekund|Ta właściwość określa limit czasu odczytywania danych z ramek TCP i przeprowadzania wysyłania połączeń z podstawowych połączeń. Istnieje możliwość przekroczenia limitu czasu, w którym usługa SMSvcHost. exe jest utrzymywana do odczytywania danych preambuły z połączenia przychodzącego. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi udostępniania portów Net. TCP](./feature-details/configuring-the-net-tcp-port-sharing-service.md).|

> [!NOTE]
> Te nowe wartości domyślne są używane tylko w przypadku wdrożenia usługi WCF na komputerze z .NET Framework 4,5. Jeśli ta sama usługa zostanie wdrożona na komputerze z .NET Framework 4,0, zostaną użyte wartości domyślne .NET Framework 4,0. W takich przypadkach zaleca się skonfigurowanie tych ustawień jawnie.

## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas> zawiera konfigurowalne wartości przydziału dla czytników słownika XML, które ograniczają ilość pamięci używaną przez koder podczas tworzenia komunikatu. Podczas konfigurowania tych przydziałów wartości domyślne uległy zmianie, aby zmniejszyć prawdopodobieństwo, że deweloper będzie musiał je jawnie ustawić. przydział `MaxReceivedMessageSize` nie został zmieniony, dzięki czemu może nadal ograniczyć zużycie pamięci, uniemożliwiając konieczność poradzenia sobie z złożonością <xref:System.Xml.XmlDictionaryReaderQuotas>. W poniższej tabeli przedstawiono przydziały, ich nowe wartości domyślne oraz krótkie objaśnienie użycia poszczególnych przydziałów.

|Nazwa przydziału|Wartość domyślna|Opis|
|----------------|-------------------|-----------------|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32. MaxValue|Pobiera i ustawia maksymalną dozwoloną długość tablicy. Ten limit przydziału ogranicza maksymalny rozmiar tablicy elementów podstawowych, które zwraca czytnik XML, w tym tablic bajtowych. Ten limit przydziału nie ogranicza zużycia pamięci w samym czytniku XML, ale w dowolnym składniku, który korzysta z czytnika. Na przykład gdy <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczonego przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, nie deserializacji tablic bajtowych większych niż ten przydział.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32. MaxValue|Pobiera i ustawia maksymalną dozwoloną liczbę bajtów zwracanych dla każdej operacji odczytu. Ten limit przydziału ogranicza liczbę bajtów odczytywanych w pojedynczej operacji odczytu podczas odczytywania znacznika początkowego elementu i jego atrybutów. (W przypadku niestrumieniowych przypadków sama sama nazwa elementu nie jest naliczana względem limitu przydziału). Zbyt wiele atrybutów XML może korzystać z nieproporcjonalnego czasu przetwarzania, ponieważ nazwy atrybutów muszą być sprawdzane pod kątem unikatowości. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> ograniczenie tego zagrożenia.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|głębokie węzły 128|Ten limit przydziału ogranicza maksymalną głębokość zagnieżdżenia elementów XML. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> współdziała z <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: czytnik zawsze przechowuje dane w pamięci dla bieżącego elementu i wszystkich jego elementów nadrzędnych, więc maksymalne użycie pamięci przez czytnik jest proporcjonalne do iloczynu tych dwóch ustawień. Podczas deserializacji wykresu obiektów głęboko zagnieżdżonych, Deserializator jest zmuszony do uzyskania dostępu do całego stosu i wyrzuca nieodwracalne <xref:System.StackOverflowException>. Istnieje bezpośrednia korelacja między zagnieżdżeniem XML a zagnieżdżeniem obiektów dla <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer>. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> służy do ograniczania tego zagrożenia.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32. MaxValue|Ten limit przydziału ogranicza maksymalną liczbę znaków dozwoloną w NameTable. NameTable zawiera pewne ciągi (takie jak przestrzenie nazw i prefiksy), które są napotkane podczas przetwarzania dokumentu XML. Ponieważ te ciągi są buforowane w pamięci, ten przydział jest używany do zapobiegania nadmiernemu buforowaniu, gdy jest oczekiwany strumień strumieniowy.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32. MaxValue|Ten limit przydziału ogranicza maksymalny rozmiar ciągu zwracanego przez czytnik XML. Ten limit przydziału nie ogranicza zużycia pamięci w samym czytniku XML, ale w składniku, który korzysta z czytnika. Na przykład gdy <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczonego przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, nie powoduje deserializacji ciągów większych niż ten przydział.|

> [!IMPORTANT]
> Aby uzyskać więcej informacji na temat zabezpieczania danych, zobacz sekcję "używanie bezpiecznego kodu XML" w obszarze [zagadnienia dotyczące zabezpieczeń](./feature-details/security-considerations-for-data.md) .

> [!NOTE]
> Te nowe wartości domyślne są używane tylko w przypadku wdrożenia usługi WCF na komputerze z .NET Framework 4,5. Jeśli ta sama usługa zostanie wdrożona na komputerze z .NET Framework 4,0, zostaną użyte wartości domyślne .NET Framework 4,0. W takich przypadkach zaleca się skonfigurowanie tych ustawień jawnie.

## <a name="wcf-configuration-validation"></a>Sprawdzanie poprawności konfiguracji WCF

W ramach procesu kompilacji w programie Visual Studio pliki konfiguracji WCF są teraz weryfikowane. Lista błędów lub ostrzeżeń dotyczących sprawdzania poprawności jest wyświetlana w programie Visual Studio, jeśli sprawdzanie poprawności zakończy się niepowodzeniem.

## <a name="xml-editor-tooltips"></a>Etykietki narzędzi edytora XML

Aby ułatwić nowym i istniejącym deweloperom usług WCF Konfigurowanie swoich usług, Edytor XML programu Visual Studio udostępnia teraz etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które są częścią pliku konfiguracji usługi.

## <a name="basichttpbinding-improvements"></a>Udoskonalenia BasicHttpBinding

1. Umożliwia pojedynczemu punktowi końcowemu programu WCF reagowanie na inne tryby uwierzytelniania.

2. Włącza ustawienia zabezpieczeń usługi WCF, które mają być kontrolowane przez usługi IIS.
