---
title: Model obiektowy programowania protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: 39c7ec31827d1cde5d95516cc3867f9d6bf9817f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739866"
---
# <a name="wcf-web-http-programming-object-model"></a>Model obiektowy programowania protokołu HTTP sieci Web w programie WCF
Model programowania HTTP sieci WEB w programie WCF umożliwia deweloperom udostępnianie usług sieci Web Windows Communication Foundation (WCF) za pośrednictwem podstawowych żądań HTTP bez konieczności stosowania protokołu SOAP. Model programowania HTTP sieci WEB w programie WCF jest oparty na istniejącym modelu rozszerzalności WCF. Definiuje następujące klasy:  
  
 **Model programowania:**  
  
- <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
- <xref:System.ServiceModel.Web.WebGetAttribute>  
  
- <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
- <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Infrastruktura kanałów i dyspozytorów:**  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Klasy narzędzi i punkty rozszerzalności:**  
  
- <xref:System.UriTemplate>  
  
- <xref:System.UriTemplateTable>  
  
- <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, po zastosowaniu do operacji usługi, wskazuje profil wyjściowej pamięci podręcznej ASP.NET w pliku konfiguracji, który powinien być używany przez program do buforowania odpowiedzi z operacji w wyjściowej pamięci podręcznej ASP .NET. Ta właściwość przyjmuje tylko jeden parametr, nazwa profilu pamięci podręcznej, która określa ustawienia pamięci podręcznej w pliku konfiguracji.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 Atrybut <xref:System.ServiceModel.Web.WebGetAttribute> służy do oznaczania operacji usługi, która odpowiada na żądania HTTP GET. Jest to zachowanie operacji pasywnej (<xref:System.ServiceModel.Description.IOperationBehavior> metod nic nie rób), które dodaje metadane do opisu operacji. Zastosowanie <xref:System.ServiceModel.Web.WebGetAttribute> nie działa, chyba że zachowanie, które szuka tych metadanych w opisie operacji (w szczególnie <xref:System.ServiceModel.Description.WebHttpBehavior>) jest dodawane do kolekcji zachowań usługi. Atrybut <xref:System.ServiceModel.Web.WebGetAttribute> wymaga parametrów opcjonalnych przedstawionych w poniższej tabeli.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BodyStyle`|Określa, czy należy zawijać żądania i odpowiedzi wysyłane do i odbierane z operacji usługi, do której ma zastosowanie atrybut.|  
|`RequestFormat`|Kontroluje sposób formatowania komunikatów żądania.|  
|`ResponseFormat`|Kontroluje sposób formatowania komunikatów odpowiedzi.|  
|`UriTemplate`|Określa szablon identyfikatora URI, który kontroluje, jakie żądania HTTP są mapowane do operacji usługi, do której jest stosowany atrybut.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 Klasa <xref:System.ServiceModel.WebHttpBinding> obejmuje obsługę danych XML, JSON i nieprzetworzone dane binarne przy użyciu <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Składa się z <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i <xref:System.ServiceModel.WebHttpSecurity> obiektu. <xref:System.ServiceModel.WebHttpBinding> jest zaprojektowana do użycia w połączeniu z <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 Atrybut <xref:System.ServiceModel.Web.WebInvokeAttribute> jest podobny do <xref:System.ServiceModel.Web.WebGetAttribute>, ale służy do oznaczania operacji usługi, która odpowiada na żądania HTTP inne niż GET. Jest to zachowanie operacji pasywnej (<xref:System.ServiceModel.Description.IOperationBehavior> metod nic nie rób), które dodaje metadane do opisu operacji. Zastosowanie <xref:System.ServiceModel.Web.WebInvokeAttribute> nie działa, chyba że zachowanie, które szuka tych metadanych w opisie operacji (w szczególnie <xref:System.ServiceModel.Description.WebHttpBehavior>) jest dodawane do kolekcji zachowań usługi.  
  
 Atrybut <xref:System.ServiceModel.Web.WebInvokeAttribute> wymaga parametrów opcjonalnych przedstawionych w poniższej tabeli.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BodyStyle`|Określa, czy należy zawijać żądania i odpowiedzi wysyłane do i odbierane z operacji usługi, do której ma zastosowanie atrybut.|  
|`Method`|Określa metodę HTTP, do której jest zamapowana operacja usługi.|  
|`RequestFormat`|Kontroluje sposób formatowania komunikatów żądania.|  
|`ResponseFormat`|Kontroluje sposób formatowania komunikatów odpowiedzi.|  
|`UriTemplate`|Określa szablon identyfikatora URI, który kontroluje, jakie żądania GET są mapowane do operacji usługi, do której jest stosowany atrybut.|  
  
## <a name="uritemplate"></a>UriTemplate  
 Klasa <xref:System.UriTemplate> umożliwia zdefiniowanie zestawu podobnych identyfikatorów URI. Szablony składają się z dwóch części, ścieżki i zapytania. Ścieżka składa się z serii segmentów rozdzielonych ukośnikiem (/). Każdy segment może mieć wartość literału, wartość zmiennej (zapisaną w nawiasach klamrowych [{}], ograniczona do zawartości dokładnie jednego segmentu) lub symbol wieloznaczny (zapisany jako gwiazdka [\*], który pasuje do "reszty ścieżki"), który musi występować na końcu ścieżki. Wyrażenie zapytania można całkowicie pominąć. Jeśli jest obecny, określa nieuporządkowaną serię par nazwa/wartość. Elementy wyrażenia zapytania mogą być parami literałów (? x = 2) lub par zmiennych (? x = {*Value*}). Niesparowane wartości są niedozwolone. <xref:System.UriTemplate> jest używany wewnętrznie przez model programowania HTTP sieci WEB w programie WCF do mapowania określonych identyfikatorów URI lub grup identyfikatorów URI na operacje usług.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 Klasa <xref:System.UriTemplateTable> reprezentuje zestaw asocjacyjny <xref:System.UriTemplate> obiektów powiązanych z obiektem wyboru dewelopera. Pozwala dopasować identyfikatory URI (Uniform Resource Identifier) kandydatów do szablonów w zestawie i pobrać dane skojarzone z pasującymi szablonami. <xref:System.UriTemplateTable> jest używany wewnętrznie przez model programowania HTTP sieci WEB w programie WCF do mapowania określonych identyfikatorów URI lub grup identyfikatorów URI na operacje usług.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> rozszerza <xref:System.ServiceModel.ServiceHost>, aby ułatwić Hostowanie usługi w stylu sieci Web bez protokołu SOAP. Jeśli <xref:System.ServiceModel.Web.WebServiceHost> nie odnajdzie punktów końcowych w opisie usługi, automatycznie tworzy domyślny punkt końcowy na adresie podstawowym usługi. Podczas tworzenia domyślnego punktu końcowego HTTP <xref:System.ServiceModel.Web.WebServiceHost> wyłącza również stronę pomocy HTTP i funkcję pobierania Web Services Description Language (WSDL), dzięki czemu punkt końcowy metadanych nie zakłóca domyślnego punktu końcowego HTTP. <xref:System.ServiceModel.Web.WebServiceHost> zapewnia również, że wszystkie punkty końcowe używające <xref:System.ServiceModel.WebHttpBinding> mają dołączone <xref:System.ServiceModel.Description.WebHttpBehavior> wymagane. Na koniec <xref:System.ServiceModel.Web.WebServiceHost> automatycznie konfiguruje powiązanie punktu końcowego do pracy ze skojarzonymi ustawieniami zabezpieczeń Internet Information Services (IIS), jeśli są używane w bezpiecznym katalogu wirtualnym.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 Klasa <xref:System.ServiceModel.Activation.WebServiceHostFactory> służy do dynamicznego tworzenia <xref:System.ServiceModel.Web.WebServiceHost>, gdy usługa jest hostowana w ramach Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS). W przeciwieństwie do usługi samodzielnej, w której aplikacja hostingu tworzy wystąpienie <xref:System.ServiceModel.Web.WebServiceHost>, usług hostowanych w ramach usług IIS lub używało tej klasy do utworzenia <xref:System.ServiceModel.Web.WebServiceHost> dla usługi. Metoda <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> jest wywoływana, gdy zostanie odebrane żądanie przychodzące dla usługi.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 Klasa <xref:System.ServiceModel.Description.WebHttpBehavior> dostarcza niezbędnych elementów formatujących, selektorów operacji i tak dalej, które są wymagane do obsługi usługi w stylu sieci Web w warstwie modelu usług. Ta funkcja jest zaimplementowana jako zachowanie punktu końcowego (używane w połączeniu z <xref:System.ServiceModel.WebHttpBinding>) i umożliwia określenie programów formatującego i selektorów operacji dla każdego punktu końcowego, co umożliwia tej samej implementacji usługi Uwidacznianie punktów końcowych protokołu SOAP i POX.  
  
### <a name="extending-webhttpbehavior"></a>Rozszerzanie WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> jest rozszerzalna przy użyciu wielu metod wirtualnych: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>i <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Deweloperzy mogą dziedziczyć klasy z <xref:System.ServiceModel.Description.WebHttpBehavior> i przesłonić te metody, aby dostosować zachowanie domyślne.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> jest przykładem rozszerzania <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> włącza punkty końcowe Windows Communication Foundation (WCF) do odbierania żądań HTTP z klienta ASP.NET AJAX opartego na przeglądarce. Przykładem użycia tego punktu rozszerzalności jest [Usługa AJAX korzystająca z protokołu HTTP Post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .  
  
> [!WARNING]
> W przypadku korzystania z <xref:System.ServiceModel.Description.WebScriptEnablingBehavior><xref:System.UriTemplate> nie są obsługiwane w atrybutach <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 Klasa <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> używa klas <xref:System.UriTemplate> i <xref:System.UriTemplateTable> do wysyłania wywołań do operacji usługi.  
  
## <a name="compatibility"></a>Zgodność  
 Model programowania HTTP sieci WEB w programie WCF nie korzysta z komunikatów opartych na protokole SOAP, dlatego nie obsługuje protokołów WS-*. Można jednak uwidocznić ten sam kontrakt przez dwa różne punkty końcowe: jeden przy użyciu protokołu SOAP, a drugi nie używa protokołu SOAP. Zapoznaj się z tematem [jak to zrobić: uwidocznienie kontraktu dla klientów protokołu SOAP i sieci Web](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) na przykład.  
  
## <a name="security"></a>Zabezpieczenia  

Ponieważ model programowania HTTP sieci WEB w programie WCF nie obsługuje protokołów WS-*, jedynym sposobem zabezpieczenia usługi sieci Web opartej na modelu programowania HTTP sieci WEB w programie WCF jest udostępnienie usługi przy użyciu protokołu SSL. Aby uzyskać więcej informacji na temat konfigurowania protokołu SSL w usługach IIS 7,0, zobacz [jak zaimplementować protokół SSL w usługach IIS](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
