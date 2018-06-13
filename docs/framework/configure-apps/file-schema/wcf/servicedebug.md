---
title: '&lt;serviceDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 0a0c6a45b6103d533a87a921e6e428bf30d81b20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352249"
---
# <a name="ltservicedebuggt"></a>&lt;serviceDebug&gt;
Określa funkcje informacji pomocy i debugowania dla usługi Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceDebug >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceDebug     httpHelpPageBinding="String"    httpHelpPageBindingConfiguration="String"  
    httpHelpPageEnabled="Boolean"  
    httpHelpPageUrl="Uri"  
    httpsHelpPageBinding="String"    httpsHelpPageBindingConfiguration="String"  
    httpsHelpPageEnabled="Boolean"  
    httpsHelpPageUrl="Uri"  
    includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|httpHelpPageBinding|Wartość ciągu, który określa typ powiązania używanego gdy HTTP jest wykorzystywany do strony usługi pomocy.<br /><br /> Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Ciąg określający nazwę powiązania, które jest określone w `httpHelpPageBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę, muszą być zdefiniowane w `<bindings>` sekcji.|  
|HttpHelpPageEnabled|Wartość logiczna kontroli tego, czy WCF publikuje stronę pomocy HTML pod adresem określonym przez `httpHelpPageUrl` atrybutu. Wartość domyślna to `true`.<br /><br /> Tę właściwość można ustawić, `false` wyłączyć publikacji stronę pomocy HTML widoczne dla przeglądarki HTML.<br /><br /> Zapewnienie pomocy HTML strony jest publikowana w miejscu kontrolowane przez `httpHelpPageUrl` atrybutu, musisz ustawić dla tego atrybutu `true`. Ponadto jeden z następujących warunków muszą być również spełnione:<br /><br /> - `httpHelpPageUrl` Atrybut jest adresu bezwzględnego, który obsługuje schemat protokołu HTTP.<br />-Brak adres podstawowy usługi, który obsługuje schemat protokołu HTTP.<br /><br /> Chociaż jest zgłaszany wyjątek, jeśli adresu bezwzględnego, który nie obsługuje schemat protokołu HTTP jest przypisany do `httpHelpPageUrl` atrybutu innej sytuacji, w których nie powyższe kryteria jest niespełnienia powoduje nie wyjątków oraz żadnej strony pomocy HTML.|  
|HttpHelpPageUrl|Identyfikator URI, który określa względny lub bezwzględny oparte na protokole HTTP adres URL niestandardowej HTML pomocy pliku użytkownik widzi, gdy punkt końcowy jest wyświetlany w przeglądarce HTML.<br /><br /> Ten atrybut umożliwia korzystanie z niestandardowego pliku Pomocy HTML, zwracanego z żądania HTTP/Get, na przykład z przeglądarki HTML. Lokalizacja pliku Pomocy HTML, zostaje rozwiązany w następujący sposób.<br /><br /> 1.  Jeśli wartość tego atrybutu jest adresem względnym, lokalizację pliku Pomocy HTML jest wartość adres podstawowy usługi, która obsługuje żądania HTTP, a także wartość tej właściwości.<br />2.  Jeśli wartość tego atrybutu jest adresem bezwzględnym i obsługuje żądania HTTP, lokalizację pliku Pomocy HTML jest wartość tej właściwości.<br />3.  Jeśli wartość tego atrybutu jest bezwzględnym, ale nie obsługuje żądania HTTP, jest zwracany wyjątek.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `httpHelpPageEnabled` atrybutu `true`.|  
|httpsHelpPageBinding|Wartość ciągu, który określa typ powiązania używanego gdy HTTPS jest wykorzystywany do strony usługi pomocy.<br /><br /> Tylko powiązania z elementami powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Ciąg określający nazwę powiązania, które jest określone w `httpsHelpPageBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę, muszą być zdefiniowane w `<bindings>` sekcji.|  
|HttpsHelpPageEnabled|Wartość logiczna kontroli tego, czy WCF publikuje stronę pomocy HTML pod adresem określonym przez `httpsHelpPageUrl` atrybutu. Wartość domyślna to `true`.<br /><br /> Tę właściwość można ustawić, `false` wyłączyć publikacji stronę pomocy HTML widoczne dla przeglądarki HTML.<br /><br /> Zapewnienie pomocy HTML strony jest publikowana w miejscu kontrolowane przez `httpsHelpPageUrl` atrybutu, musisz ustawić dla tego atrybutu `true`. Ponadto jeden z następujących warunków muszą być również spełnione:<br /><br /> - `httpsHelpPageUrl` Atrybut jest adresu bezwzględnego, który obsługuje schemat protokołu HTTPS.<br />-Brak adres podstawowy usługi, który obsługuje schemat protokołu HTTPS.<br /><br /> Chociaż jest zgłaszany wyjątek, jeśli adresu bezwzględnego, który nie obsługuje schematu protokołu HTTPS jest przypisany do `httpsHelpPageUrl` atrybutu innej sytuacji, w których nie powyższe kryteria jest niespełnienia powoduje nie wyjątków oraz żadnej strony pomocy HTML.|  
|HttpsHelpPageUrl|Identyfikator URI, który określa względny lub bezwzględny oparty na protokole HTTPS adres URL niestandardowej HTML pomocy pliku użytkownik widzi, gdy punkt końcowy jest wyświetlany w przeglądarce HTML.<br /><br /> Ten atrybut umożliwia korzystanie z niestandardowego pliku Pomocy HTML, zwracanego z żądania HTTPS/Get, na przykład z przeglądarki HTML. Lokalizacja pliku Pomocy HTML zostanie rozwiązany w następujący sposób:<br /><br /> — Jeśli wartość tej właściwości jest adresem względnym, lokalizację pliku Pomocy HTML jest wartość adres podstawowy usługi, która obsługuje żądania HTTPS, a także wartość tej właściwości.<br />— Jeśli wartość tej właściwości jest adresem bezwzględnym i obsługuje żądania HTTPS, lokalizację pliku Pomocy HTML jest wartość tej właściwości.<br />— Jeśli wartość tej właściwości jest bezwzględnym, ale nie obsługuje żądania HTTPS, jest zwracany wyjątek.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `httpHelpPageEnabled` atrybutu `true`.|  
|IncludeExceptionDetailInFaults|Wartość, która określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klienta na potrzeby debugowania. Wartość domyślna to `false`.<br /><br /> Jeśli ustawisz ten atrybut `true`, można włączyć przepływ informacji o zarządzanych wyjątkach do klienta dla celów debugowania, a także publikacji pliki HTML informacje dla użytkowników, przeglądanie usług w przeglądarkach sieci Web. **Uwaga:** zwraca informacje o zarządzanym wyjątku do klientów mogą stanowić zagrożenie bezpieczeństwa. Jest to spowodowane szczegóły wyjątku ujawnienie informacji o implementacji usługi wewnętrznego, które mogą być używane przez nieautoryzowanych klientów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienie `includeExceptionDetailInFaults` do `true` umożliwia zwracanej wyjątku zgłoszonego przez kod aplikacji, nawet jeśli wyjątek nie został zadeklarowany za pomocą usługi <xref:System.ServiceModel.FaultContractAttribute>. To ustawienie jest przydatne, gdy debugowanie przypadków, gdy serwer jest zgłaszanie wystąpił nieoczekiwany wyjątek. Za pomocą tego atrybutu, jest zwracany serializacji formę nieznany wyjątek i można sprawdzić szczegółowe informacje o wyjątku.  
  
> [!CAUTION]
>  Zwracanie informacje o zarządzanym wyjątku do klientów może być zagrożenie bezpieczeństwa, ponieważ szczegóły wyjątku ujawnienie informacji o implementacji usługi wewnętrznego, które mogą być używane przez nieautoryzowanych klientów. Z powodu zagadnień związanych z zabezpieczeniami zaleca się, że tylko w tym kontrolowanymi scenariuszami debugowania. Należy ustawić `includeExceptionDetailInFaults` do `false` podczas wdrażania aplikacji.  
  
 Aby uzyskać szczegółowe informacje dotyczące problemów z zabezpieczeniami dotyczące zarządzanych wyjątkach, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Przykładowy kod [zachowanie debugowania usługi](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Można również ustawić `httpsHelpPageEnabled` i `httpsHelpPageUrl` Aby włączyć lub wyłączyć strony pomocy. Każda usługa opcjonalnie mogą uwidaczniać strona pomocy, który zawiera informacje dotyczące usługi, w tym punktu końcowego można pobrać WSDL dla usługi. Można je włączyć, ustawiając `httpHelpPageEnabled` do `true`. Umożliwia to strona pomocy ma zostać zwrócona na żądanie GET adres podstawowy usługi. Ten adres można zmienić, określając `httpHelpPageUrl` atrybutu. Ponadto możesz wprowadzić to bezpieczne przy użyciu protokołu HTTPS zamiast protokołu HTTP.  
  
 Opcjonalny `httpHelpPageBinding` i `httpHelpPageBinding` atrybutów umożliwiają konfigurowanie powiązań umożliwiają dostęp do strony usługi sieci web. Jeśli nie są one określone, powiązania domyślnego (`HttpTransportBindingElement`, w przypadku protokołu HTTP i `HttpsTransportBindingElement`, w przypadku protokołu HTTPS) są używane do dostępu do strony pomocy usługi zgodnie z potrzebami. Zwróć uwagę, że nie można użyć tych atrybutów z wbudowanych powiązaniami WCF. Tylko powiązania z elementami powiązania, które obsługują xref:System.ServiceModel.Channels.IReplyChannel > będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> właściwość powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceDebugElement>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Obsługa wyjątków i błędów](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Zachowanie debugowania usług](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)
