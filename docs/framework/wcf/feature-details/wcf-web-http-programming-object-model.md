---
title: Model obiektowy programowania protokołu HTTP sieci Web w programie WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7bf6512be6fabb87797fb6338f64320d5787d547
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-web-http-programming-object-model"></a>Model obiektowy programowania protokołu HTTP sieci Web w programie WCF
Modelu programowania protokołu HTTP sieci WEB WCF umożliwia deweloperom ujawnia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług za pośrednictwem podstawowego żądania HTTP sieci Web bez konieczności protokołu SOAP. Modelu programowania protokołu HTTP sieci WEB WCF jest oparty na istniejące [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu rozszerzalności. Definiuje następujące klasy:  
  
 **Model programowania:**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanały i dyspozytora infrastruktury:**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Klasy narzędzi i punkty rozszerzalności:**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, Gdy jest stosowany do operacji usługi, wskazuje ASP.NET wyjściowego profilu pamięci podręcznej w pliku konfiguracji, które mają być używane przez do pamięci podręcznej odpowiedzi z operacji w wyjściowej pamięci podręcznej ASP .NET. Ta właściwość ma tylko jeden parametr, nazwa profilu pamięci podręcznej, która określa ustawienia pamięci podręcznej w pliku konfiguracji.  
  
## <a name="webgetattribute"></a>Obiekt WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> Atrybut służy do oznaczania operacji usługi, które odpowiada na żądania HTTP GET. Jest zachowanie operacji pasywnym ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nic nie rób) dodaje metadanych w opisie operacji. Stosowanie <xref:System.ServiceModel.Web.WebGetAttribute> nie obowiązuje, chyba że zachowanie wygląda tych metadanych w opisie działania (w szczególności <xref:System.ServiceModel.Description.WebHttpBehavior>) zostanie dodany do kolekcji zachowań usługi. <xref:System.ServiceModel.Web.WebGetAttribute> Atrybut przyjmuje następujące parametry opcjonalne pokazano w poniższej tabeli.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BodyStyle`|Określa, czy do opakowywania żądania i odpowiedzi wysyłane do i odbierane z atrybut jest stosowany do operacji usługi.|  
|`RequestFormat`|Określa, jak sformatowanych komunikatów żądania.|  
|`ResponseFormat`|Określa, jak są sformatowane wiadomości odpowiedzi.|  
|`UriTemplate`|Określa szablon identyfikatora URI, który kontroluje, jakie żądania HTTP get zamapowany na ten atrybut jest stosowany do operacji usługi.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> Klasy zawiera obsługę XML, JSON i przy użyciu nieprzetworzone dane binarne <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Składa się z <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i <xref:System.ServiceModel.WebHttpSecurity> obiektu. <xref:System.ServiceModel.WebHttpBinding> Jest przeznaczony do użycia w połączeniu z <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atrybutu jest podobny do <xref:System.ServiceModel.Web.WebGetAttribute>, ale jest używane do operacji usługi zostać oznaczone jako taki, który odpowiada HTTP innych niż GET żądań. Jest zachowanie operacji pasywnym ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nic nie rób) dodaje metadanych w opisie operacji. Stosowanie <xref:System.ServiceModel.Web.WebInvokeAttribute> nie obowiązuje, chyba że zachowanie wygląda tych metadanych w opisie działania (w szczególności <xref:System.ServiceModel.Description.WebHttpBehavior>) zostanie dodany do kolekcji zachowań usługi.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atrybut przyjmuje następujące parametry opcjonalne pokazano w poniższej tabeli.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BodyStyle`|Określa, czy do opakowywania żądania i odpowiedzi wysyłane do i odbierane z atrybut jest stosowany do operacji usługi.|  
|`Method`|Określa metodę HTTP jest zamapowana operacji usługi.|  
|`RequestFormat`|Określa, jak sformatowanych komunikatów żądania.|  
|`ResponseFormat`|Określa, jak są sformatowane wiadomości odpowiedzi.|  
|`UriTemplate`|Określa szablon identyfikatora URI, który kontroluje, jakie żądania GET uzyskać zamapowany na ten atrybut jest stosowany do operacji usługi.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> Klasy można zdefiniować zestawu strukturę podobną identyfikatorów URI. Szablony składają się z dwóch części, ścieżkę i kwerendy. Ścieżka składa się z szeregu segmentów rozdzielonych przez ukośnika (/). Każdy z segmentów może mieć wartość literału, wartości zmiennej (zapisany w nawiasy klamrowe [{}], ograniczone do dopasowania zawartości dokładnie jeden segment) lub symbolem wieloznacznym (zapisane jako gwiazdka [\*], zgodnej "pozostałej części ścieżki"), który musi znajdować się na końca ścieżki. Wyrażenia zapytania może zostać całkowicie pominięty. Jeśli jest obecny, określa nieuporządkowaną serii par nazwa/wartość. Elementy wyrażenia zapytania mogą być albo literału pary (? x = 2) lub pary zmiennej (? x = {*wartość*}). Niesparowane wartości nie są dozwolone. <xref:System.UriTemplate> jest używana wewnętrznie przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu programowania pakietu sieci WEB HTTP, aby zamapować określonych identyfikatorów URI lub grupy identyfikatorów URI do operacji usługi.  
  
## <a name="uritemplatetable"></a>Obiekt UriTemplateTable  
 <xref:System.UriTemplateTable> Klasa reprezentuje asocjacyjnej zbiór <xref:System.UriTemplate> obiekty powiązane z obiektu dewelopera na wybór. Umożliwia ona dopasowywania candidate Uniform Resource Identifier (URI) szablony w zestawie i pobrać dane skojarzone z pasujących szablonów. <xref:System.UriTemplateTable> jest używana wewnętrznie przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu programowania pakietu sieci WEB HTTP, aby zamapować określonych identyfikatorów URI lub grupy identyfikatorów URI do operacji usługi.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> Rozszerza <xref:System.ServiceModel.ServiceHost> aby ułatwić do obsługi usługi sieci Web styl protokołem SOAP. Jeśli <xref:System.ServiceModel.Web.WebServiceHost> znajdzie żadnych punktów końcowych w opisie usługi automatycznie tworzy domyślny punkt końcowy na adres podstawowy usługi. Podczas tworzenia punktu końcowego HTTP domyślne <xref:System.ServiceModel.Web.WebServiceHost> również wyłącza strona pomocy HTTP oraz funkcje GET Web Services Description Language (WSDL), aby punkt końcowy metadanych nie zakłóca domyślny punkt końcowy HTTP. <xref:System.ServiceModel.Web.WebServiceHost> gwarantuje również, że wszystkie punkty końcowe korzystające <xref:System.ServiceModel.WebHttpBinding> mają wymaganych <xref:System.ServiceModel.Description.WebHttpBehavior> dołączony. Na koniec <xref:System.ServiceModel.Web.WebServiceHost> automatycznie konfiguruje powiązanie punktu końcowego do pracy z skojarzone ustawienia zabezpieczeń Internet Information Services (IIS) w bezpiecznym katalogu wirtualnego.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> Klasa jest używana do dynamicznego tworzenia <xref:System.ServiceModel.Web.WebServiceHost> gdy usługa jest obsługiwana w ramach usług Internet Information Services (IIS) ani Usługa aktywacji procesów systemu Windows (WAS). W przeciwieństwie do usługi hostowanej własnym gdzie tworzy hostingu aplikacji <xref:System.ServiceModel.Web.WebServiceHost>, usługi IIS hostowanej w obszarze lub klasa była używana do tworzenia <xref:System.ServiceModel.Web.WebServiceHost> dla usługi. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> Metoda jest wywoływana po otrzymaniu żądania przychodzącego dla usługi.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> Klasa dostarcza niezbędne elementy formatujące, selektorów operacji i tak dalej, wymaganych do obsługi stylu sieci Web w warstwie modelu usługi. Ten sposób jest implementowany jako zachowanie punktu końcowego (używane w połączeniu z <xref:System.ServiceModel.WebHttpBinding>) i umożliwia elementy formatujące i selektorów operacji można określić dla każdego punktu końcowego, który umożliwia wdrożenie tej samej usługi do udostępnienia zarówno protokołu SOAP i POX punktów końcowych.  
  
### <a name="extending-webhttpbehavior"></a>Rozszerzanie WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> jest rozszerzalny za pomocą metod wirtualnych: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, i <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Deweloperzy mogą dziedziczyć klasy z <xref:System.ServiceModel.Description.WebHttpBehavior> i zastępować te metody, aby dostosować zachowanie domyślne.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Przykładem rozszerzanie <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Włącza [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] punktów końcowych do odbierania żądań HTTP z przeglądarki klienta ASP.NET AJAX. [AJAX Service przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) przykładem za pomocą tego punktu rozszerzalności.  
  
> [!WARNING]
>  Korzystając z <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> nie są obsługiwane w ramach <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> Klasy używa <xref:System.UriTemplate> i <xref:System.UriTemplateTable> klasy wysłania wywołania do operacji usługi.  
  
## <a name="compatibility"></a>Zgodność  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Modelu programowania protokołu HTTP sieci WEB nie używa opartego na protokole SOAP komunikatów i dlatego nie obsługuje WS-* protokołów. Możesz jednak udostępnić ten sam kontrakt dwóch różnych punktu końcowego: go przy użyciu protokołu SOAP oraz innymi nie przy użyciu protokołu SOAP. Zobacz [porady: ujawnianie kontraktu klientom sieci Web i SOAP](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) przykład.  
  
## <a name="security"></a>Zabezpieczenia  
 Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu programowania protokołu HTTP sieci WEB nie obsługuje WS-* protokoły jedynym sposobem do zabezpieczania usługi sieci Web oparta na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest Model programowania protokołu HTTP sieci WEB do udostępnienia do usługi przy użyciu protokołu SSL. Aby uzyskać więcej informacji o konfigurowaniu protokołu SSL z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] zobacz [Implementowanie protokołu SSL w usługach IIS](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
 [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
