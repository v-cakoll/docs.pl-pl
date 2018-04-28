---
title: Co&#39;s Nowość w systemie Windows Communication Foundation 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], what's new
- Windows Communication Foundation [WCF], what's new
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ca03c4529588964abe2d0d434bfd47b005e8d26
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="what39s-new-in-windows-communication-foundation-45"></a>Co&#39;s Nowość w systemie Windows Communication Foundation 4.5
W tym temacie omówiono zaczynasz korzystać z funkcji [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="wcf-simplification-features"></a>Funkcje upraszczania programu WCF  
 Aby ułatwić tworzenie i obsługa aplikacji WCF 4.5 zostało wykonane dużo pracy. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="task-based-async-support"></a>Obsługa opartego na zadaniach asynchronicznej  
 Domyślnie Dodaj odwołanie do usługi generuje umożliwiające zwracanie zadań metody operacji usługi asynchroniczne. Jest to realizowane dla metod synchroniczne i asynchroniczne. Dzięki temu można wywołać operacji usługi asynchronicznie za pomocą nowego asynchroniczne zadanie na podstawie modelu programowania. Po wywołaniu metody wygenerowany serwer proxy WCF tworzy obiekt zadanie reprezentujące operację asynchroniczną i zwraca, dla których zadań do Ciebie. Zadanie działanie jest kończone po zakończeniu operacji.  Podczas wdrażania można wdrożyć go jako operacja opartego na zadaniach asynchronicznej operacji asynchronicznej. Aby uzyskać więcej informacji, zobacz [synchroniczne i asynchroniczne operacje](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
### <a name="simplified-generated-configuration-files"></a>Uproszczone konfiguracji wygenerowanych plików  
 Podczas dodawania odwołania do usługi w programie Visual Studio lub za pomocą narzędzia SvcUtil.exe, jest generowany plik konfiguracji klienta. W poprzednich wersjach programu WCF te pliki konfiguracji zawiera wartość dla każdej właściwości powiązania, nawet jeśli jego wartość jest wartością domyślną. W WCF 4.5 pliki konfiguracji wygenerowanego zawierają tylko te właściwości powiązania, które są ustawione na wartości innych niż domyślne.  
  
 Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md)  
  
### <a name="contract-first-development"></a>Programowanie Contract-First  
 Usługi WCF ma teraz obsługę tworzenia pierwszej kontraktu. Svcutl.exe ma przełącznik /serviceContract, dzięki czemu można wygenerować kontraktów usług i danych z dokumentu WSDL.  
  
### <a name="add-service-reference-from-a-portable-subset-project"></a>Dodaj odwołanie do usługi w projekcie obsługującym podzestaw przenośny  
 Projekty obsługującym podzestaw przenośny umożliwiają programistom zestawu .NET Obsługa drzewa jednego źródła i kompilacji systemu przerywania obsługi wielu platform .NET (pulpitu, Silverlight, Windows Phone i XBOX). Projekty obsługującym podzestaw przenośny odwoływać się tylko przenośnych bibliotek .NET, które są zestawem .NET framework, używany na dowolnej platformie .NET. Środowisko dewelopera jest taka sama jak dodawanie odwołania do usługi w ramach innych aplikacji klienta WCF. Aby uzyskać więcej informacji, zobacz [Dodaj odwołanie do usługi w projekcie podzestaw przenośny](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
### <a name="aspnet-compatibility-mode-default-changed"></a>Domyślne tryb zgodności ASP.NET zostało zmienione  
 Usługi WCF zapewnia tryb zgodności ASP.NET, aby przyznać deweloperom pełny dostęp do funkcji w potoku HTTP programu ASP.NET, podczas zapisywania usług WCF. Aby użyć w tym trybie, należy ustawić `aspNetCompatibilityEnabled` atrybut na wartość true w [ \<serviceHostingEnvironment >](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) sekcji w pliku Web.config. Ponadto usługi w tej domenie aplikacji musi mieć `RequirementsMode` właściwości na jego <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ustawioną <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>. Domyślnie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ma teraz wartość <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>. Aby uzyskać więcej informacji, zobacz [What's New in Windows Communication Foundation](../../../docs/framework/wcf/whats-new.md) i [usługi WCF i platformy ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
### <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu  
 Aby uprościć konfigurację wartości domyślnej właściwości transportu zostały zmienione. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> zawiera wartości zasobów można skonfigurować dla czytników słownika XML, które ograniczają ilość pamięci wykorzystywany przez koder podczas tworzenia komunikatu. Te przydziały są konfigurowalne, wartości domyślne zostały zmienione na zmniejszenie prawdopodobieństwa, że deweloper musi ustawiony w sposób jawny. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### <a name="wcf-configuration-validation"></a>Sprawdzanie poprawności konfiguracji usługi WCF  
 Jako część procesu kompilacji w programie Visual Studio pliki konfiguracji usługi WCF teraz są weryfikowane pod kątem atrybuty zdefiniowane w projekcie. W programie Visual Studio jest wyświetlona lista błędy lub ostrzeżenia walidacji, jeśli weryfikacja zakończy się niepowodzeniem.  
  
### <a name="xml-editor-tooltips"></a>Etykietki narzędzi edytora XML  
 Aby ułatwić nowych i istniejących WCF usługi deweloperom konfigurowanie w swoich usług, Edytor XML usługi Visual Studio teraz udostępnia etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które jest częścią pliku konfiguracji usługi.  
  
## <a name="streaming-improvements"></a>Ulepszenia przesyłania strumieniowego  
 Dodano obsługę wartość true, asynchronicznego przesyłania strumieniowego gdzie stronie wysyłania teraz nie blokować wątków, jeśli nie odczytuje po stronie odbierania lub powolne podczas odczytywania, co zwiększa skalowalność. Usunąć ograniczenia komunikat buforowania, gdy klient wysyła się, że usługi WCF hostowanej komunikat przesyłany strumieniowo do usług IIS. Aby uzyskać więcej informacji, zobacz [funkcje upraszczania programu WCF](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
## <a name="simplifying-exposing-an-endpoint-over-https-with-iis"></a>Upraszczanie udostępnianie punktu końcowego za pośrednictwem protokołu HTTPS z usługami IIS  
 Mapowanie protokołu HTTPS dodano uprościć udostępnianie punktu końcowego za pośrednictwem protokołu HTTPS. Aby włączyć punkt końcowy HTTPS, upewnij się, że powiązanie HTTPS i skonfigurować certyfikat SSL witryny sieci Web, a następnie po prostu włącz protokół HTTPS dla katalogu wirtualnego, który jest hostem usługi. Jeśli metadane są włączone dla usługi, zostanie on wystawiony za pośrednictwem protokołu HTTPS również.  
  
## <a name="generating-a-single-wsdl-document"></a>Trwa generowanie dokumentu WSDL pojedynczego  
 Stosy WSDL przetwarzania niektórych innych firm nie są w stanie przetwarzania dokumentów WSDL, które są zależne inne dokumenty za pomocą XSD.  Usługi WCF umożliwia teraz określić, że wszystkie informacje WSDL zwrócone w jednym dokumencie. Aby zażądać dołączenia pojedynczego dokumentu WSDL "? singleWSDL" do identyfikatora URI, gdy żąda metadanych usługi.  
  
## <a name="websocket-support"></a>Obsługa protokołu WebSocket  
 Obiekty Websocket jest technologia, która zapewnia komunikację dwukierunkową true przez porty 80 i 443 z charakterystyki wydajności podobny do protokołu TCP. Dwa nowe powiązania zostały dodane do obsługi komunikacji za pośrednictwem transportu protokołu WebSocket. <xref:System.ServiceModel.NetHttpBinding> i <xref:System.ServiceModel.NetHttpsBinding>. Aby uzyskać więcej informacji, zobacz: [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="new-transport-default-values"></a>Nowe wartości domyślne transportu  
 W poniższej tabeli opisano ustawienia, które zostały zmienione i gdzie można znaleźć dodatkowe informacje.  
  
|Właściwość|On|Nowy domyślny|Aby uzyskać więcej informacji, zobacz|  
|--------------|--------|-----------------|------------------------------|  
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 sekund|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|ListenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 * liczba procesorów|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * liczba procesorów dla transportu<br /><br /> 4 \* liczba procesorów dla SMSvcHost.exe|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Konfigurowanie usługi współużytkowania portów Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * liczba procesorów|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 sekund|[Konfigurowanie usługi współużytkowania portów Net.TCP](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
  
## <a name="xml-editor-tooltips"></a>Etykietki narzędzi edytora XML  
 Aby ułatwić nowych i istniejących WCF usługi deweloperom konfigurowanie w swoich usług, Edytor XML usługi Visual Studio teraz udostępnia etykietki narzędzi dla każdego elementu konfiguracji i jego właściwości, które jest częścią pliku konfiguracji usługi.  
  
## <a name="configuring-wcf-services-in-code"></a>Konfigurowanie usług WCF w kodzie  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Umożliwia deweloperom konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu.  Pliki konfiguracji są przydatne, gdy usługa musi być skonfigurowana po wdrożeniu. Podczas korzystania z plików konfiguracyjnych, specjalistów IT wystarczy tylko zaktualizować pliku konfiguracji, kompilacji nie jest wymagana. Pliki konfiguracji, jednak można złożone i trudne w utrzymaniu. Nie jest obsługiwane dla debugowania plików konfiguracji i elementy konfiguracji odwołują się nazwy, dzięki czemu tworzenia plików konfiguracyjnych podatne na błędy i trudne. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Umożliwia również skonfigurować usługi w kodzie. W starszych wersjach [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 i starszych) Konfigurowanie usług w kodzie było łatwe w scenariuszach siebie <xref:System.ServiceModel.ServiceHost> klasa dozwolona konfigurowania punktów końcowych i zachowania przed wywołaniem ServiceHost.Open. W scenariuszach hostowana w sieci web, jednak nie masz dostępu do <xref:System.ServiceModel.ServiceHost> klasy. Aby skonfigurować sieci web hostowanej usługi są wymagane do utworzenia `System.ServiceModel.ServiceHostFactory` utworzony <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać wszelkie wymagane konfiguracji. W programie .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umożliwia łatwiejsze sposobem skonfigurowania obu hosta samodzielnego i sieci web hostowanych usług w kodzie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług WCF w kodzie](../../../docs/framework/wcf/configuring-wcf-services-in-code.md).  
  
## <a name="channelfactory-caching"></a>Buforowanie elementu ChannelFactory  
 Aplikacje klienta WCF <xref:System.ServiceModel.ChannelFactory%601> klasę, aby utworzyć kanał komunikacji z usługą WCF.  Tworzenie <xref:System.ServiceModel.ChannelFactory%601> wystąpień powoduje pewne nadmiarowe obciążenie, ponieważ obejmuje ona następujące operacje:  
  
1.  Konstruowanie <xref:System.ServiceModel.Description.ContractDescription> drzewa  
  
2.  Zdarzenie odzwierciedla wszystkie wymagane typy CLR  
  
3.  Konstruowanie stosu kanału  
  
4.  Usuwanie zasobów  
  
 Aby zminimalizować ten narzut, WCF może buforować fabryk kanałów, które, gdy jest używany serwer proxy klienta WCF. Aby uzyskać więcej informacji, zobacz [fabryki kanałów i buforowanie](../../../docs/framework/wcf/feature-details/channel-factory-and-caching.md).  
  
## <a name="compression-and-the-binary-encoder"></a>Kompresja i kodera binarnego  
 Począwszy od WCF 4.5 kodera binarnego WCF dodaje obsługę kompresji. Typ kompresji jest konfigurowana <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> właściwości. Zarówno klient, jak i usługi należy skonfigurować <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A> właściwości. Kompresja będzie działać dla protokołów HTTP, HTTPS i TCP. Jeśli klient określa kompresji, ale usługa nie obsługuje protokołu wyjątku wskazujący niezgodność protokołu. Aby uzyskać więcej informacji, zobacz [Wybieranie kodera komunikatów](../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
  
## <a name="udp"></a>UDP  
 Dodano obsługę dla transportu UDP, który umożliwia deweloperom pisanie usług korzystających z "wyzwalać i zapomnij" wiadomości. Klient wysyła komunikat do usługi i oczekuje na brak odpowiedzi z usługi.  
  
## <a name="multiple-authentication-support"></a>Obsługa wielu uwierzytelniania  
 Do obsługi wielu tryby uwierzytelniania, dodano obsługę jako obsługiwany przez usługi IIS, jeden punkt końcowy usługi WCF podczas korzystania z transportu HTTP i zabezpieczeń transportu. Usługi IIS umożliwia włączenie wielu tryby uwierzytelniania w katalogu wirtualnym, funkcja ta zapewnia jeden punkt końcowy usługi WCF do obsługi wielu tryby uwierzytelniania dla katalogu wirtualnego, gdzie usługa WCF jest hostowana włączone.  
  
## <a name="idn-support"></a>Obsługa IDN  
 Dodano obsługę do obsługi usług WCF za pomocą międzynarodowych nazw domen. Aby uzyskać więcej informacji, zobacz [WCF i międzynarodowe nazwy domen](../../../docs/framework/wcf/feature-details/wcf-and-internationalized-domain-names.md).  
  
## <a name="httpclient"></a>HttpClient  
 Nową klasę o nazwie <xref:System.Net.Http.HttpClient> został dodany do znacznie ułatwić pracę z żądania HTTP. Aby uzyskać więcej informacji, zobacz [uczynienie aplikacji społecznościowych i jest połączony z usług HTTP](http://go.microsoft.com/fwlink/?LinkId=231886) i [próbki klienta HTTP](http://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664).  
  
## <a name="configuration-intellisense"></a>Konfiguracja Intellisense  
 Wartości atrybutów w plikach konfiguracji dla atrybutów niestandardowych zdefiniowanych w projekcie teraz intellisense pomocy technicznej w celu ułatwienia pracy z konfiguracjami szybkiego.  
  
## <a name="configuration-tooltips"></a>Etykietki narzędzi konfiguracji  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] elementów i atrybutów teraz łatwiej trzeba etykietki narzędzi w edytorze XML, a dokładnie sprawdzić celem elementu lub atrybutu.  
  
## <a name="paste-data-as-classes"></a>Wklejanie danych jako klasy  
 W projekcie programu WCF typów danych zdefiniowanych w pliku XML (takie jak są widoczne w usłudze) można wkleić bezpośrednio do strony kodowej. Typ XML zostanie wklejona jako typu CLR. Zobacz [generowania klasy typów danych z pliku XML](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md) więcej szczegółów.  
  
## <a name="webservicehost-and-default-endpoints"></a>Typ WebServiceHost i domyślne punkty końcowe  
 W programie Visual Studio 2010 Typ WebServiceHost automatycznie tworzony jest domyślny punkt końcowy czy jawnie określonego punktu końcowego lub nie. W programie Visual Studio 2012 w Typ WebServiceHost tylko utworzy domyślnego punktu końcowego, gdy punkty końcowe nie zostały dodane w sposób jawny. Jeśli klient oczekuje domyślny punkt końcowy, można jawnie dodać punktu końcowego i wskaż klienta. Alternatywnie można określić, WCF, aby powrócić do poprzedniej zachowanie, dodając następujące ustawienie do pliku konfiguracji aplikacji  
  
```xml  
<appSettings>  
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>  
  </appSettings>  
```  
  
## <a name="ihttpcookiecontainermanager"></a>IHttpCookieContainerManager  
 Ten interfejs udostępniany przez <xref:System.ServiceModel.Channels.IChannelFactory%601>, sprawia, że praca z plików cookie po stronie klienta znacznie łatwiejsze. Gdy AllowCookies jest ustawiona na wartość true dla powiązania, są dostępne pliki cookie przy użyciu następującego kodu:  
  
```csharp  
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();   
System.Net.CookieContainer container = cookieManager.CookieContainer;  
```  
  
 Można pobrać lub ustawić pliki cookie z <xref:System.Net.CookieContainer>. AllowCookies jest ustawiona na wartość false, można ręcznie pobrać, plików cookie, za pomocą <xref:System.ServiceModel.OperationContext> i wysłać go w innych żądaniach przy użyciu innego <xref:System.ServiceModel.OperationContext> lub Inspektora wiadomości. Interfejs IHttpCookieContainerManager umożliwia uwierzytelnianie użytkowników za pomocą usługi i używać pliku cookie uwierzytelniania zwrócony przez tę usługę na potrzeby uwierzytelniania z innymi usługami.
