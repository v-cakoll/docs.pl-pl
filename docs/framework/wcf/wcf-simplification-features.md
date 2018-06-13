---
title: Funkcje upraszczania programu WCF
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: e5a18d721ed05bc064abca88768e393748951a5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508713"
---
# <a name="wcf-simplification-features"></a>Funkcje upraszczania programu WCF
W tym temacie opisano nowe funkcje, które zapisywania WCF aplikacji prostsze.  
  
## <a name="simplified-generated-configuration-files"></a>Uproszczone konfiguracji wygenerowanych plików  
 Podczas dodawania odwołania do usługi w programie Visual Studio lub za pomocą narzędzia SvcUtil.exe jest generowany plik konfiguracji klienta. W poprzednich wersjach programu WCF te pliki konfiguracji zawiera wartość dla każdej właściwości powiązania, nawet jeśli jego wartość jest wartością domyślną. W WCF 4.5 pliki konfiguracji wygenerowanego zawierają tylko te właściwości powiązania, które są ustawione na wartości innych niż domyślne.  
  
 Poniżej przedstawiono przykładowy plik konfiguracji generowany przez WCF 3.0.  
  
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
  
 Oto przykład tego samego pliku konfiguracji wygenerowane przez WCF 4.5.  
  
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
 Usługi WCF ma teraz obsługę tworzenia pierwszej kontraktu. Narzędzie svcutl.exe ma przełącznik /serviceContract, dzięki czemu można wygenerować kontraktów usług i danych z dokumentu WSDL.  
  
## <a name="add-service-reference-from-a-portable-subset-project"></a>Dodaj odwołanie do usługi w projekcie obsługującym podzestaw przenośny  
 Projekty obsługującym podzestaw przenośny umożliwiają programistom zestawu .NET Obsługa drzewa jednego źródła i kompilacji systemu nadal obsługuje wiele implementacji .NET (pulpitu, Silverlight, Windows Phone i XBOX). Projekty obsługującym podzestaw przenośny odwoływać się tylko przenośnych bibliotek .NET, które są zestawem .NET framework, używanym w implementacji .NET. Środowisko dewelopera jest taka sama jak dodawanie odwołania do usługi w ramach innych aplikacji klienta WCF. Aby uzyskać więcej informacji, zobacz [Dodaj odwołanie do usługi w projekcie podzestaw przenośny](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
## <a name="aspnet-compatibility-mode-default-changed"></a>Domyślne tryb zgodności ASP.NET zostało zmienione  
 Usługi WCF zapewnia tryb zgodności ASP.NET, aby przyznać deweloperom pełny dostęp do funkcji w potoku HTTP programu ASP.NET, podczas zapisywania usług WCF. Aby użyć w tym trybie, należy ustawić `aspNetCompatibilityEnabled` atrybut na wartość true w [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) sekcji w pliku Web.config. Ponadto usługi w tej domenie aplikacji musi mieć `RequirementsMode` właściwości na jego <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ustawioną <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Domyślnie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ma teraz wartość <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> i ustawia szablon aplikacji usługi domyślne WCF `aspNetCompatibilityEnabled` atrybutu `true`. Aby uzyskać więcej informacji, zobacz [What's New in Windows Communication Foundation 4.5](../../../docs/framework/wcf/whats-new.md) i [usługi WCF i platformy ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="streaming-improvements"></a>Ulepszenia przesyłania strumieniowego  
  
-   Nowa funkcja obsługi asynchronicznego przesyłania strumieniowego dodano do programu WCF. Aby włączyć, asynchronicznego przesyłania strumieniowego, Dodaj <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> zachowania punktu końcowego usługi hosta i ustaw jej <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> właściwości `true`.  Można korzystać skalowalność, gdy usługa wysyła strumienia wiadomości do wielu klientów, które odczytują powoli. Usługi WCF nie blokuje już jeden wątek na klienta i zwolnić wątku do obsługi innego klienta.  
  
-   Usunięto ograniczenia wokół buforowanie wiadomości, gdy usługa jest hostowane w usługach IIS. W poprzednich wersjach programu WCF podczas odbierania komunikatu używany strumieniowy transfer komunikatów usługi hostowanych przez usługi IIS platformy ASP.NET będzie bufor cały komunikat przed wysłaniem ich do usługi WCF. To spowodowałoby zużycie pamięci. To buforowanie został usunięty w programie .NET 4.5 i teraz usług WCF hostowanych przez usługi IIS start przetwarzania przychodzących strumienia przed odebraniem cały komunikat, umożliwiając w ten sposób przesyłania strumieniowego wartość true. Umożliwia WCF natychmiast odpowiadać na komunikaty i umożliwia lepszą wydajność. Ponadto nie należy określić wartość dla `maxRequestLength`, limit rozmiaru platformy ASP.NET na żądań przychodzących. Jeśli ta właściwość jest ustawiona, zostanie zignorowany. Aby uzyskać więcej informacji na temat `maxRequestLength` zobacz [ \<httpRuntime > element konfiguracji](http://go.microsoft.com/fwlink/?LinkId=223344). Należy także skonfigurować maxAllowedContentLength, aby uzyskać więcej informacji, zobacz [limity żądań usług IIS](http://go.microsoft.com/fwlink/?LinkId=225908).  
  
## <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu  
 W poniższej tabeli opisano ustawienia, które zostały zmienione i gdzie można znaleźć dodatkowe informacje.  
  
|Właściwość|On|Nowy domyślny|Więcej informacji|  
|--------------|--------|-----------------|----------------------|  
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|Ta właściwość określa, jak długo połączenie TCP może trwać do uwierzytelniania przy użyciu programu .Net Framing protokołu. Gdy klient musi wysłać niektórych początkowe dane, zanim serwer ma za mało informacji do uwierzytelniania. Tego limitu czasu jest celowo zapewnić mniejszy niż ReceiveTimeout (10 minut) złośliwego nieuwierzytelnionych klientów nie przechowuj połączeń blokowana na serwerze długo. Wartość domyślna to 30 sekund. Aby uzyskać więcej informacji o <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|ListenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * liczba procesorów|Ta właściwość poziomie gniazda określa liczbę "Akceptuj oczekujących" można umieścić w kolejce żądań. Jeśli czasochłonną kolejki zaległości nasłuchiwania nowych żądań gniazda zostanie odrzucone. Aby uzyskać więcej informacji o <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * liczba procesorów dla transportu<br /><br /> 4 \* liczba procesorów dla SMSvcHost.exe|Ta właściwość ogranicza liczbę kanałów, które na serwerze może być oczekiwanie na odbiornik. Po MaxPendingAccepts ma zbyt niską wartość, będą małe interwał czasu, w którym wszystkie kanały oczekiwania rozpoczęły obsługi połączeń, ale nowych kanałów rozpoczęto nasłuchiwania. Połączenie można odbierane w danym przedziale czasu i zakończy się niepowodzeniem, ponieważ nic nie oczekuje ona na serwerze. Tej właściwości można skonfigurować przez ustawienie <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> właściwości na większą liczbę. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> i [Konfigurowanie usługi udostępniania portów Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * liczba procesorów|Ta właściwość określa, ile połączenia transportu zaakceptowane, ale nie zostały pobrana przez dyspozytora ServiceModel. Aby ustawić tę wartość, użyj `MaxConnections` w powiązaniu lub `maxOutboundConnectionsPerEndpoint` w elemencie wiązania. Aby uzyskać więcej informacji o <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 sekund|Ta właściwość określa limit czasu dla odczytu danych z ramek TCP i wykonania przekazania połączenia z podstawowym połączeń. To istnieje cap zawiesić ilość czasu, usługa SMSvcHost.exe jest przechowywane zaangażowani można odczytać danych preambuły z połączenia przychodzącego. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi udostępniania portów Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).|  
  
> [!NOTE]
>  Te nowe ustawienia domyślne są używane tylko w przypadku wdrażania usługi WCF na komputerze z programem .NET Framework 4.5. W przypadku wdrożenia tej samej usługi na komputerze z programem .NET Framework 4.0, są używane wartości domyślne programu .NET Framework 4.0. W takich przypadkach zaleca się konfigurowania tych ustawień jawnie.  
  
## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> zawiera wartości zasobów można skonfigurować dla czytników słownika XML, które ograniczają ilość pamięci wykorzystywany przez koder podczas tworzenia komunikatu. Mimo że te przydziały jest konfigurowalne, wartości domyślne zostały zmienione na zmniejszanie możliwości, który trzeba jawnie ustaw dewelopera. `MaxReceivedMessageSize` limit przydziału nie zostało zmienione tak, aby go nadal można ograniczyć zużycie pamięci, trzeba uwzględniać złożoność uniemożliwia <xref:System.Xml.XmlDictionaryReaderQuotas>. W poniższej tabeli przedstawiono przydziały, nowe wartości domyślnych i krótki opis przeznaczenia każdego przydziału.  
  
|Nazwa przydziału|Wartość domyślna|Opis|  
|----------------|-------------------|-----------------|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Wartość Int32.MaxValue|Pobiera i ustawia maksymalną dozwoloną długość tablicy. Ten limit przydziału ogranicza maksymalny rozmiar to tablica wartości pierwotnych, które zwraca modułu odczytującego XML, łącznie z tablic bajtowych. Ten limit przydziału nie ogranicza zużycie pamięci w samej modułu odczytującego XML, ale niezależnie od składnika korzystający z czytnika. Na przykład, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczone przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, nie wykonać deserializacji tablice typu byte przekracza ten limit przydziału.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Wartość Int32.MaxValue|Pobiera i ustawia maksymalny dozwolony bajtów zwracana przy każdym odczycie. Ten limit przydziału ogranicza liczbę bajtów, które są do odczytu w ramach jednej operacji odczytu podczas odczytywania elementu start tagu i jego atrybuty. (W przypadku strumieniowo, nazwa elementu jest pomijany względem limitu przydziału). O zbyt wiele atrybutów XML posłużyć nieproporcjonalnie czasu przetwarzania ponieważ nazwy atrybutów muszą być sprawdzane pod kątem unikatowości. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> zmniejsza zagrożenie tego typu.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|głębokie 128 węzłów|Ten limit przydziału ogranicza maksymalną głębokość zagnieżdżenia elementów XML.  <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> współdziała z <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>: czytnik zawsze przechowuje dane w pamięci dla bieżącego elementu i wszystkich jego obiektów nadrzędnych, więc zużycie pamięci maksymalnej czytnika danych jest proporcjonalny do wyniku te dwa ustawienia. Podczas deserializacji wykresu obiektu głęboko zagnieżdżone, Deserializator wymusza na dostęp do całego stosu i zgłosić nieodwracalny <xref:System.StackOverflowException>. Bezpośrednie korelacji istnieje między zagnieżdżenia XML i zagnieżdżenia obiektu dla obu <xref:System.Runtime.Serialization.DataContractSerializer> i <!--zz <xref:System.Runtime.Serialization.XmlSerializer>--> `System.Runtime.Serialization.XmlSerializer`. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> Umożliwia uniknięcie tego zagrożenia.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Wartość Int32.MaxValue|Ten limit przydziału ogranicza maksymalną liczbę znaków dozwolonych w tabeli nazw. Niepowtarzającymi zawiera niektóre ciągi (takie jak obszary nazw i prefiksy) napotkanych podczas przetwarzania dokumentu XML. Te ciągi są buforowane w pamięci, aby uniknąć nadmiernego buforowania, gdy przesyłania strumieniowego jest używane ten limit przydziału.|  
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Wartość Int32.MaxValue|Ten limit przydziału ogranicza maksymalny rozmiar ciągu zwracające modułu odczytującego XML. Ten limit przydziału nie ogranicza zużycie pamięci w samej modułu odczytującego XML, ale w składniku korzystający z czytnika. Na przykład, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczone przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, nie wykonać deserializacji ciągów przekracza ten limit przydziału.|  
  
> [!IMPORTANT]
>  Zapoznaj się "Przy użyciu bezpiecznie XML" w obszarze [zagadnienia dotyczące zabezpieczeń dla danych](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md) Aby uzyskać więcej informacji na temat zabezpieczania danych.  
  
> [!NOTE]
>  Te nowe ustawienia domyślne są używane tylko w przypadku wdrażania usługi WCF na komputerze z programem .NET Framework 4.5. W przypadku wdrożenia tej samej usługi na komputerze z programem .NET Framework 4.0, są używane wartości domyślne programu .NET Framework 4.0. W takich przypadkach zaleca się konfigurowania tych ustawień jawnie.  
  
## <a name="wcf-configuration-validation"></a>Sprawdzanie poprawności konfiguracji usługi WCF  
 Jako część procesu kompilacji w programie Visual Studio teraz są weryfikowane pliki konfiguracji usługi WCF. Lista błędy lub ostrzeżenia walidacji są wyświetlane w programie Visual Studio, w przypadku niepowodzenia weryfikacji.  
  
## <a name="xml-editor-tooltips"></a>Etykietki narzędzi edytora XML  
 Aby ułatwić nowych i istniejących WCF usługi deweloperom konfigurowanie w swoich usług, Edytor XML usługi Visual Studio teraz udostępnia etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które jest częścią pliku konfiguracji usługi.  
  
## <a name="basichttpbinding-improvements"></a>Ulepszenia BasicHttpBinding  
  
1.  Zapewnia jeden punkt końcowy usługi WCF na odpowiadanie na tryby uwierzytelniania inny.  
  
2.  Włącza ustawienia zabezpieczeń usługi WCF kontrolowany przez usługi IIS
