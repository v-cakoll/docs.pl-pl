---
title: Funkcje upraszczania programu WCF
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: 54255e07df5a46cc975ffd4db5c18dc828a1de44
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845281"
---
# <a name="wcf-simplification-features"></a>Funkcje upraszczania programu WCF

W tym temacie omówiono nowe funkcje, które upewnij się, zapisywanie WCF aplikacje prostsze.

## <a name="simplified-generated-configuration-files"></a>Uproszczony wygenerowanych plików konfiguracyjnych

Podczas dodawania odwołania do usługi w programie Visual Studio lub za pomocą narzędzia SvcUtil.exe pliku konfiguracji klienta jest generowany. W poprzednich wersjach programu WCF te pliki konfiguracji zawarte wartości dla każdej właściwości powiązania, nawet wtedy, gdy jego wartość jest wartością domyślną. W programie WCF 4.5 wygenerowanych plików konfiguracyjnych zawiera tylko te właściwości powiązania, które są ustawione na wartości innych niż domyślne.

Oto przykładowy plik konfiguracji, generowane przez WCF 3.0.

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

Oto przykład tego samego pliku konfiguracji, generowane przez 4.5 usługi WCF.

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

## <a name="contract-first-development"></a>Programowanie Contract-First

Usługi WCF dodano wsparcie dla programowania z wymogiem wcześniejszego zawarcia kontraktu. Narzędzia svcutil.exe ma przełącznik /serviceContract, który umożliwia generowanie kontraktów usług i danych z dokumentu WSDL.

## <a name="add-service-reference-from-a-portable-subset-project"></a>Dodaj odwołanie do usługi w projekcie obsługującym podzestaw przenośny

Projekty obsługującym podzestaw przenośny umożliwiają deweloperom zestawu .NET do utrzymywania drzewa pojedyncze źródło i systemu kompilacji, nadal obsługując wiele implementacji .NET (pulpitu, Silverlight, Windows Phone i XBOX). Projekty obsługującym podzestaw przenośny tylko odwołania do bibliotek przenośnych platformy .NET, będące zestaw .NET framework, używanym w implementacji .NET. Środowisko programistyczne jest taka sama jak dodawanie odwołania do usługi w ramach innej aplikacji klienckich programu WCF. Aby uzyskać więcej informacji, zobacz [Dodaj odwołanie do usługi w przenośnych projekcie obsługującym podzestaw](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).

## <a name="aspnet-compatibility-mode-default-changed"></a>Domyślne tryb zgodności ASP.NET zostało zmienione

Usługi WCF zapewnia tryb zgodności ASP.NET do udzielania deweloperów pełny dostęp do funkcji w potoku HTTP programu ASP.NET, podczas zapisywania usług WCF. Aby użyć tego trybu, należy ustawić `aspNetCompatibilityEnabled` atrybut na wartość true w [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) sekcja pliku Web.config. Ponadto każda usługa, w tym elemencie appDomain musi mieć `RequirementsMode` właściwość jego <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> równa <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Domyślnie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> są teraz ustawione na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> i domyślne WCF usługi zestawy szablonów aplikacji `aspNetCompatibilityEnabled` atrybutu `true`. Aby uzyskać więcej informacji, zobacz [What's New in Windows Communication Foundation 4.5](../../../docs/framework/wcf/whats-new.md) i [usługi WCF i platforma ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).

## <a name="streaming-improvements"></a>Ulepszenia przesyłania strumieniowego

- Nowa funkcja obsługi asynchronicznego przesyłania strumieniowego dołączonym do programu WCF. Aby włączyć, asynchronicznego przesyłania strumieniowego, Dodaj <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> zachowanie punktu końcowego usługi hosta i ustaw jego <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> właściwość `true`. Mogą zyskać skalowalność, gdy usługa wysyła komunikaty przesyłane strumieniowo do wielu klientów, które odczytują powoli. Usługi WCF nie blokuje już jeden wątek na każdym klienta i dysku można zwolnić wątek do obsługi innego klienta.

- Usunięto ograniczenia dotyczące buforowania wiadomości, gdy usługa jest hostowana w usługach IIS. W poprzednich wersjach programu WCF podczas odbierania komunikatu dla używanej strumieniowy transfer komunikatów usługi hostowanych przez usługi IIS ASP.NET będzie buforować cały komunikat przed wysłaniem ich do programu WCF. To spowoduje, że zużycie pamięci. Tej buforowanie zostało usunięte w .NET 4.5, a teraz usługi WCF hostowanej przez usługi IIS można uruchomić, przetwarzanie strumienia przychodzącego przed odebraniem cały komunikat, umożliwiając w ten sposób true przesyłania strumieniowego. Zezwala na WCF do natychmiastowe odpowiadanie na wiadomości i umożliwia lepszą wydajność. Ponadto nie należy określić wartość dla `maxRequestLength`, limit rozmiaru platformy ASP.NET na żądań przychodzących. Jeśli ta właściwość jest ustawiona, zostanie zignorowany. Aby uzyskać więcej informacji na temat `maxRequestLength` zobacz [ \<httpRuntime > element konfiguracji](https://go.microsoft.com/fwlink/?LinkId=223344). Należy także skonfigurować maxAllowedContentLength, aby uzyskać więcej informacji, zobacz [limity żądań usług IIS](https://go.microsoft.com/fwlink/?LinkId=225908).

## <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu

W poniższej tabeli opisano ustawienia, które zostały zmienione i gdzie można znaleźć dodatkowe informacje.

|Właściwość|On|Nowe rozwiązanie domyślne|Więcej informacji|
|--------------|--------|-----------------|----------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|Ta właściwość określa, jak długo połączenia protokołu TCP można wykonać w celu uwierzytelniać przy użyciu protokołu .NET Framing. Klient musi wysyłać niektórych danych początkowych, zanim serwer ma za mało informacji w celu przeprowadzenia uwierzytelniania. Limit czasu jest celowo zapewnić mniejszy niż ReceiveTimeout (10 min) złośliwego nieuwierzytelnionych klientów nie przechowuj połączeń blokowana serwerowi długo. Wartość domyślna to 30 sekund. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * liczba procesorów|Ta właściwość poziomie gniazd opisuje liczbę "oczekujące Akceptuj" żądań w kolejce. Jeśli kolejka zaległości nasłuchiwania się zapełni, nowe żądania gniazda zostanie odrzucone. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * liczba procesorów dla transportu<br /><br /> 4 \* liczby procesorów dla SMSvcHost.exe|Ta właściwość ogranicza liczbę kanałów, które serwer może mieć oczekiwanie na odbiornik. Gdy MaxPendingAccepts jest zbyt niska, nastąpi małych przedział czasu, w którym wszystkie kanały oczekiwania rozpoczęły obsługi połączeń, ale nie nowe kanały rozpoczęto nasłuchiwania. Połączenie, mogą pojawić się w danym przedziale czasu i zakończy się niepowodzeniem, ponieważ nic nie czeka on na serwerze. Tej właściwości można skonfigurować, ustawiając <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> właściwości na większą liczbę. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> i [konfigurowania usługi udostępniania portów Net.TCP](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * liczba procesorów|Ta właściwość określa, ile połączenia transportu zaakceptował, ale nie zostały jeszcze odebrane przez dyspozytora elementu ServiceModel. Aby ustawić tę wartość, użyj `MaxConnections` w powiązaniu lub `maxOutboundConnectionsPerEndpoint` w elemencie powiązania. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30 sekund|Ta właściwość określa limit czasu dla odczytu danych z ramek TCP i wykonania przekazania połączenia z podstawowym połączeń. Istnieje to umieszczenie limit ilości czasu, przez który SMSvcHost.exe usługi są przechowywane zaangażowani odczytać dane preambuły z połączenia przychodzącego. Aby uzyskać więcej informacji, zobacz [konfigurowania usługi udostępniania portów Net.TCP](../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).|

> [!NOTE]
> Te nowe ustawienia domyślne są używane tylko wtedy, gdy wdrażanie usługi WCF na maszynie z .NET Framework 4.5. Jeśli możesz wdrożyć tę samą usługę na komputerze przy użyciu programu .NET Framework 4.0, używane są ustawienia domyślne programu .NET Framework 4.0. W takich przypadkach zalecane jest aby skonfigurować te ustawienia jawnie.

## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas> zawiera wartości zasobów można skonfigurować dla czytelników słownika XML, które ograniczają ilość pamięci wykorzystywany przez koder podczas tworzenia komunikatu. Mimo że tych limitów przydziału można skonfigurować, wartości domyślne zostały zmienione na zmniejszanie możliwości, które deweloper będzie ustawiony w sposób jawny. `MaxReceivedMessageSize` przydział nie został zmieniony tak, aby nadal może ograniczyć zużycie pamięci, zapobiegając potrzebę radzenia sobie z złożoność <xref:System.Xml.XmlDictionaryReaderQuotas>. W poniższej tabeli przedstawiono limity przydziału, nowe wartości domyślnych i krótki opis dotyczący przeznaczenia każdego przydziału.

|Nazwa limitu przydziału|Wartość domyślna|Opis|
|----------------|-------------------|-----------------|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|Pobiera lub ustawia maksymalną dozwoloną długość tablicy. Ten limit przydziału ogranicza maksymalny rozmiar tablicy elementów podstawowych, które zwraca odczytującego XML, w tym tablice typu byte. Ten limit przydziału nie ogranicza użycie pamięci przez czytnik XML, sam, ale w składniku niezależnie od korzystający z czytnika. Na przykład, gdy <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnik zabezpieczony za pomocą <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, nie wykonać deserializacji tablice bajtów przekracza ten limit przydziału.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|Pobiera i ustawia maksymalna liczba bajtów dozwoloną dla każdego odczytu. Ten limit przydziału ogranicza liczbę bajtów, które są odczytywane w ramach jednej operacji odczytu podczas odczytywania elementu start tag i jego atrybuty. (W przypadkach,-strumieniowo, sama nazwa elementu jest nie przeliczane względem limitu przydziału). Masz zbyt wiele atrybutów XML może używać nieproporcjonalne czas przetwarzania, ponieważ nazwy atrybutu muszą być sprawdzane pod kątem unikatowości. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> zmniejsza zagrożenie tego typu.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|głębokie 128 węzłów|Ten limit przydziału ogranicza maksymalną głębokość zagnieżdżenia elementów XML. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> wchodzi w interakcję z <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: czytnik zawsze zachowuje dane w pamięci dla bieżącego elementu i wszystkie jego elementy nadrzędne, zmniejszenie zużycia pamięci maksymalnej czytnika jest proporcjonalna do produktu te dwa ustawienia. Podczas deserializacji grafu obiektów głęboko zagnieżdżone, dostęp do całego stosu i zgłosić nieodwracalny wymuszono Deserializator <xref:System.StackOverflowException>. Między zagnieżdżanie XML i zagnieżdżanie obiektu dla obu istnieje bezpośrednia korelacja <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer>. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> Umożliwia uniknięcie tego zagrożenia.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|Ten limit przydziału ogranicza maksymalną liczbę znaków dozwolonych w tabeli nazw. Tabela nazw zawiera niektóre ciągi (na przykład obszary nazw i prefiksy), napotkanych podczas przetwarzania dokumentu XML. Jak te ciągi są buforowane w pamięci, ten limit przydziału jest używana Aby uniknąć nadmiernego buforowanie podczas przesyłania strumieniowego jest oczekiwany.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|Ten limit przydziału ogranicza rozmiar maksymalny ciągu, która zwraca odczytującego XML. Ten limit przydziału nie ogranicza użycie pamięci przez czytnik XML, sam, ale w składniku korzystający z czytnika. Na przykład, gdy <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnik zabezpieczony za pomocą <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, nie wykonać deserializacji ciągi przekracza ten limit przydziału.|

> [!IMPORTANT]
> Zobacz "Przy użyciu bezpiecznego XML" w obszarze [zagadnienia dotyczące zabezpieczeń dla danych](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md) Aby uzyskać więcej informacji na temat zabezpieczania danych.

> [!NOTE]
> Te nowe ustawienia domyślne są używane tylko wtedy, gdy wdrażanie usługi WCF na maszynie z .NET Framework 4.5. Jeśli możesz wdrożyć tę samą usługę na komputerze przy użyciu programu .NET Framework 4.0, używane są ustawienia domyślne programu .NET Framework 4.0. W takich przypadkach zalecane jest aby skonfigurować te ustawienia jawnie.

## <a name="wcf-configuration-validation"></a>Sprawdzanie poprawności konfiguracji programu WCF

Jako część procesu kompilacji w programie Visual Studio są teraz sprawdzane plików konfiguracyjnych WCF. Lista ostrzeżeń ani błędów sprawdzania poprawności są wyświetlane w programie Visual Studio, jeśli weryfikacja zakończy się niepowodzeniem.

## <a name="xml-editor-tooltips"></a>XML Editor Tooltips

W celu ułatwić nowych i istniejących deweloperzy usług WCF do konfigurowania swoich usług, edytorze XML Visual Studio teraz udostępnia etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które jest częścią pliku konfiguracji usługi.

## <a name="basichttpbinding-improvements"></a>Ulepszenia BasicHttpBinding

1. Umożliwia jednym punkcie końcowym WCF odpowiedzieć na tryby uwierzytelniania innego.

2. Włącza usługi WCF ustawienia zabezpieczeń będą kontrolowane przez usługi IIS
