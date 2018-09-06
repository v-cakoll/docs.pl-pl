---
title: Model obiektowy programowania protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: 8400798e4edcad41c4f5336d59646413900347f8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861640"
---
# <a name="wcf-web-http-programming-object-model"></a>Model obiektowy programowania protokołu HTTP sieci Web w programie WCF
Usługi WCF WEB HTTP programowania modelu pozwala deweloperom na Uwidacznianie usług Windows Communication Foundation (WCF) w sieci Web za pomocą podstawowego żądania HTTP bez protokołu SOAP. WCF WEB HTTP programowania modelu została stworzona na podstawie istniejącego modelu rozszerzalności programu WCF. Definiuje następujące klasy:  
  
 **Model programowania:**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanały i wysyłający infrastruktury:**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Klasy narzędzi i punkty rozszerzalności:**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, Po zastosowaniu do operacji usługi wskazuje ASP.NET dane wyjściowe profil pamięci podręcznej w pliku konfiguracji, które mają być używane przez do pamięci podręcznej odpowiedzi z operacji w wyjściowej pamięci podręcznej programu ASP .NET. Ta właściwość ma tylko jeden parametr, nazwa profilu pamięci podręcznej, który określa ustawienia pamięci podręcznej w pliku konfiguracji.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> Atrybut jest używany do oznaczania operacji usługi jako jeden, który odpowiada na żądania HTTP GET. To zachowanie operacji pasywnym ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nic nie rób) dodająca metadanych opis operacji. Stosowanie <xref:System.ServiceModel.Web.WebGetAttribute> nie ma wpływu, chyba że zachowania wygląda dla tych metadanych w opisie działania (w szczególności <xref:System.ServiceModel.Description.WebHttpBehavior>) jest dodawany do kolekcji zachowania usługi. <xref:System.ServiceModel.Web.WebGetAttribute> Atrybut przyjmuje następujące parametry opcjonalne pokazano w poniższej tabeli.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BodyStyle`|Określa, czy do opakowania żądań i odpowiedzi wysyłane do i odbierane z operacji usługi, który jest stosowany.|  
|`RequestFormat`|Określa, jak są sformatowane komunikaty żądania.|  
|`ResponseFormat`|Określa, jak są sformatowane wiadomości odpowiedzi.|  
|`UriTemplate`|Określa szablon identyfikatora URI, który kontroluje, jakie żądania HTTP są mapowane do operacji usługi, który jest stosowany.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> Klasy zawiera obsługę XML, JSON i nieprzetworzone dane binarne, przy użyciu <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Składa się z <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i <xref:System.ServiceModel.WebHttpSecurity> obiektu. <xref:System.ServiceModel.WebHttpBinding> Jest przeznaczony do użycia w połączeniu z <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atrybutu jest podobny do <xref:System.ServiceModel.Web.WebGetAttribute>, ale jest używany do oznaczania operacji usługi, ponieważ taki, który odpowiada HTTP inne niż GET żądań. To zachowanie operacji pasywnym ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nic nie rób) dodająca metadanych opis operacji. Stosowanie <xref:System.ServiceModel.Web.WebInvokeAttribute> nie ma wpływu, chyba że zachowania wygląda dla tych metadanych w opisie działania (w szczególności <xref:System.ServiceModel.Description.WebHttpBehavior>) jest dodawany do kolekcji zachowania usługi.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atrybut przyjmuje następujące parametry opcjonalne pokazano w poniższej tabeli.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BodyStyle`|Określa, czy do opakowania żądań i odpowiedzi wysyłane do i odbierane z operacji usługi, który jest stosowany.|  
|`Method`|Określa metodę HTTP, który jest mapowany operacji usługi.|  
|`RequestFormat`|Określa, jak są sformatowane komunikaty żądania.|  
|`ResponseFormat`|Określa, jak są sformatowane wiadomości odpowiedzi.|  
|`UriTemplate`|Określa szablon identyfikatora URI, który kontroluje, jakie żądania GET są mapowane do operacji usługi, który jest stosowany.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> Klasa umożliwia zdefiniowanie zestawu strukturalnie podobne identyfikatorów URI. Szablony składają się z dwóch części, ścieżkę i zapytanie. Ścieżka składa się z szeregu segmentów rozdzielonych ukośnikiem (/). Każdy z segmentów może mieć wartości literału, wartość zmiennej (napisanego w nawiasy klamrowe {[}], ograniczone do dopasowania zawartości dokładnie jednego segmentu) lub symbol wieloznaczny (zapisane jako znak gwiazdki [\*], który dopasowuje "pozostałą część ścieżki"), który musi znajdować się na końca ścieżki. Można całkowicie pominąć wyrażenia zapytania. Jeśli jest obecny, określa nieuporządkowaną serii par nazwa/wartość. Elementy wyrażenia zapytania mogą być albo literał pary (? x = 2) lub pary zmiennej (? x = {*wartość*}). Także niesparowane wartości nie są dozwolone. <xref:System.UriTemplate> jest używana wewnętrznie przez usługi WCF WEB HTTP programowania Model do określonych identyfikatorów URI lub grup identyfikatory URI są mapowane na operacje usługi.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Klasa reprezentuje zestaw asocjacyjnych <xref:System.UriTemplate> obiekty powiązane z obiektu dewelopera jego wybranie. Dzięki temu można dopasować Release candidate Uniform Resource Identifier (URI) szablonów w zestawie i pobrać dane skojarzone z szablonami dopasowania. <xref:System.UriTemplateTable> jest używana wewnętrznie przez usługi WCF WEB HTTP programowania Model do określonych identyfikatorów URI lub grup identyfikatory URI są mapowane na operacje usługi.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> Rozszerza <xref:System.ServiceModel.ServiceHost> ułatwiają hostowanie usługi sieci Web stylu protokołem SOAP. Jeśli <xref:System.ServiceModel.Web.WebServiceHost> wykryje brak punktów końcowych w opisie usługi automatycznie tworzy domyślny punkt końcowy na adres podstawowy usługi. Podczas tworzenia domyślnego punktu końcowego HTTP, <xref:System.ServiceModel.Web.WebServiceHost> także wyłącza stronę pomocy protokołu HTTP i funkcje GET usługi sieci Web Services Description Language (WSDL), więc punkt końcowy metadanych nie kolidują z domyślnego punktu końcowego HTTP. <xref:System.ServiceModel.Web.WebServiceHost> gwarantuje również, że wszystkie punkty końcowe korzystające <xref:System.ServiceModel.WebHttpBinding> mają wymaganych <xref:System.ServiceModel.Description.WebHttpBehavior> dołączone. Na koniec <xref:System.ServiceModel.Web.WebServiceHost> automatycznie konfiguruje powiązanie punktu końcowego do pracy z skojarzone ustawienia zabezpieczeń Internet Information Services (IIS), gdy są używane w bezpieczny katalog wirtualny.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> Klasa jest używana do dynamicznego tworzenia <xref:System.ServiceModel.Web.WebServiceHost> gdy usługa jest obsługiwana w ramach usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS). W przeciwieństwie do samodzielnie hostowanej usługi, których tworzy wystąpienie aplikacji macierzystej <xref:System.ServiceModel.Web.WebServiceHost>, usługi IIS hostowanej w ramach lub został klasa jest używana do tworzenia <xref:System.ServiceModel.Web.WebServiceHost> dla usługi. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> Metoda jest wywoływana po odebraniu żądania przychodzące dla usługi.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> Klasa dostarcza niezbędne elementy formatujące, operacja selektory i tak dalej, wymagane do obsługi stylu sieci Web w warstwie modelu usługi. Ten sposób jest implementowany jako zachowanie punktu końcowego (używane w połączeniu z <xref:System.ServiceModel.WebHttpBinding>) i pozwala elementy formatujące i selektory operację, należy określić dla każdego punktu końcowego, który umożliwia tym samym implementacji service uwidaczniają punkty końcowe protokołu SOAP i POX.  
  
### <a name="extending-webhttpbehavior"></a>Rozszerzanie WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> jest rozszerzalny za pomocą pewnej liczby metod wirtualnych: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, i <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Deweloperzy mogą wyprowadzić klasę z <xref:System.ServiceModel.Description.WebHttpBehavior> i zastąpić te metody, aby dostosować zachowanie domyślne.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Jest przykładem rozszerzanie <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Umożliwia punktów końcowych usług Windows Communication Foundation (WCF), aby otrzymywać żądania HTTP od klienta ASP.NET AJAX oparte na przeglądarce. [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) znajduje się przykład za pomocą tego punktu rozszerzalności.  
  
> [!WARNING]
>  Korzystając z <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> nie są obsługiwane w ramach <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> Klasy używa <xref:System.UriTemplate> i <xref:System.UriTemplateTable> klasy wysyłanie wywołań do operacji usługi.  
  
## <a name="compatibility"></a>Zgodność  
 WCF WEB HTTP programowania modelu nie korzysta z opartej na protokole SOAP wiadomości i dlatego nie obsługuje protokołu WS-* protokołów. Można jednak udostępnić ten sam kontrakt przez dwa różne punkt końcowy: ją przy użyciu protokołu SOAP, a inne nie przy użyciu protokołu SOAP. Zobacz [instrukcje: ujawnianie kontraktu klientom internetowym i SOAP](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) przykład.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ WCF WEB HTTP modelu programowania nie obsługuje protokołu WS-* protokołów, jedynym sposobem, aby zabezpieczyć usługi sieci Web oparta na sieci WEB HTTP modelu programowania programu WCF jest do udostępnienia usługi za pomocą protokołu SSL. Aby uzyskać więcej informacji o konfigurowaniu protokołu SSL za pomocą [!INCLUDE[iisver](../../../../includes/iisver-md.md)] zobacz [Implementowanie protokołu SSL w usługach IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
 [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
