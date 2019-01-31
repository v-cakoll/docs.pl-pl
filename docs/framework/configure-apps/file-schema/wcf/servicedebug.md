---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 1ab7058d8667344197e8bc1ddc59cc7200f22270
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268564"
---
# <a name="servicedebug"></a>\<serviceDebug>
Określa funkcje informacji pomocy i debugowania dla usługi Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceDebug>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceDebug httpHelpPageBinding="String"
              httpHelpPageBindingConfiguration="String"
              httpHelpPageEnabled="Boolean"
              httpHelpPageUrl="Uri"
              httpsHelpPageBinding="String"
              httpsHelpPageBindingConfiguration="String"
              httpsHelpPageEnabled="Boolean"
              httpsHelpPageUrl="Uri"
              includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|httpHelpPageBinding|Wartość ciągu, który określa typ powiązania używanego gdy HTTP jest wykorzystywany Aby uzyskać dostęp do strony pomocy usługi.<br /><br /> Tylko powiązania z elementami wewnętrznymi powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> właściwości powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Ciąg określający nazwę powiązania, który jest określony w `httpHelpPageBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę muszą być zdefiniowane w `<bindings>` sekcji.|  
|httpHelpPageEnabled|Wartość logiczna kontrolować, czy WCF publikuje stronę pomocy HTML pod adresem określonym przez `httpHelpPageUrl` atrybutu. Wartość domyślna to `true`.<br /><br /> Można ustawić tę właściwość na `false` wyłączyć publikacji stronę pomocy HTML widoczne dla przeglądarki HTML.<br /><br /> Aby zapewnić pomoc HTML strony jest publikowany w lokalizacji kontrolowane przez `httpHelpPageUrl` atrybutu, należy ustawić ten atrybut `true`. Ponadto jeden z następujących warunków muszą również być spełnione:<br /><br /> `httpHelpPageUrl` Atrybut jest adresem bezwzględnym, który obsługuje schemat protokołu HTTP.<br />-Istnieje adres podstawowy dla usługi, która obsługuje schemat protokołu HTTP.<br /><br /> Mimo że jest zgłaszany wyjątek, jeśli adresem bezwzględnym, który nie obsługuje schemat protokołu HTTP jest przypisany do `httpHelpPageUrl` atrybutu każdej innej sytuacji, w których nie poprzedniego kryteriów jest niespełnienia skutkuje żaden wyjątek nie stronę pomocy HTML.|  
|httpHelpPageUrl|Identyfikator URI, który określa względny lub bezwzględny oparty na protokole HTTP adres URL niestandardowego kodu HTML pomóc, plik użytkownik widzi, gdy punkt końcowy jest wyświetlany za pomocą przeglądarki HTML.<br /><br /> Można użyć tego atrybutu, aby umożliwić korzystanie z niestandardowego pliku Pomocy HTML, zwracanego z żądania HTTP/Get, na przykład z przeglądarki HTML. Lokalizacja pliku Pomocy HTML jest rozwiązywany w następujący sposób.<br /><br /> 1.  Jeśli wartość tego atrybutu jest adres względny, lokalizację pliku Pomocy HTML jest wartość adres podstawowy usługi, która obsługuje żądania HTTP, a także wartość tej właściwości.<br />2.  Jeśli wartość tego atrybutu jest adresem bezwzględnym i obsługuje żądania HTTP, lokalizację pliku Pomocy HTML jest wartość tej właściwości.<br />3.  Jeśli wartość tego atrybutu jest bezwzględny, ale nie obsługuje żądania HTTP, jest zgłaszany wyjątek.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `httpHelpPageEnabled` atrybut jest `true`.|  
|httpsHelpPageBinding|Wartość ciągu, który określa typ powiązania używanego gdy HTTPS jest wykorzystywany Aby uzyskać dostęp do strony pomocy usługi.<br /><br /> Tylko powiązania z elementami wewnętrznymi powiązania, które obsługują <xref:System.ServiceModel.Channels.IReplyChannel> będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> właściwości powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Ciąg określający nazwę powiązania, który jest określony w `httpsHelpPageBinding` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego powiązania. Taką samą nazwę muszą być zdefiniowane w `<bindings>` sekcji.|  
|httpsHelpPageEnabled|Wartość logiczna kontrolować, czy WCF publikuje stronę pomocy HTML pod adresem określonym przez `httpsHelpPageUrl` atrybutu. Wartość domyślna to `true`.<br /><br /> Można ustawić tę właściwość na `false` wyłączyć publikacji stronę pomocy HTML widoczne dla przeglądarki HTML.<br /><br /> Aby zapewnić pomoc HTML strony jest publikowany w lokalizacji kontrolowane przez `httpsHelpPageUrl` atrybutu, należy ustawić ten atrybut `true`. Ponadto jeden z następujących warunków muszą również być spełnione:<br /><br /> `httpsHelpPageUrl` Atrybut jest adresem bezwzględnym, który obsługuje schemat protokołu HTTPS.<br />-Istnieje adres podstawowy dla usługi, która obsługuje schemat protokołu HTTPS.<br /><br /> Mimo że jest zgłaszany wyjątek, jeśli adresem bezwzględnym, który nie obsługuje schematu protokół HTTPS jest przypisany do `httpsHelpPageUrl` atrybutu każdej innej sytuacji, w których nie poprzedniego kryteriów jest niespełnienia skutkuje żaden wyjątek nie stronę pomocy HTML.|  
|httpsHelpPageUrl|Identyfikator URI, który określa względny lub bezwzględny oparty na protokole HTTPS adres URL niestandardowego kodu HTML pomóc, plik użytkownik widzi, gdy punkt końcowy jest wyświetlany za pomocą przeglądarki HTML.<br /><br /> Można użyć tego atrybutu, aby umożliwić korzystanie z niestandardowego pliku Pomocy HTML, zwracanego z żądania HTTPS/Get, na przykład z przeglądarki HTML. Lokalizacja pliku Pomocy HTML można rozwiązać w następujący sposób:<br /><br /> — Jeśli wartość tej właściwości jest adres względny, lokalizację pliku Pomocy HTML jest wartość adres podstawowy usługi, która obsługuje żądania HTTPS, a także wartość tej właściwości.<br />— Jeśli wartość tej właściwości jest adresem bezwzględnym i obsługuje żądania HTTPS, lokalizację pliku Pomocy HTML jest wartość tej właściwości.<br />— Jeśli wartość tej właściwości jest bezwzględny, ale nie obsługuje żądania HTTPS, jest zgłaszany wyjątek.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `httpHelpPageEnabled` atrybut jest `true`.|  
|includeExceptionDetailInFaults|Wartość, która określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klienta na potrzeby debugowania. Wartość domyślna to `false`.<br /><br /> Jeśli ten atrybut jest ustawiony `true`, można włączyć przepływ informacji o zarządzanych wyjątku do klienta do celów debugowania, a także publikacji HTML plików informacji użytkownikom przeglądanie usług w przeglądarkach sieci Web. **Uwaga:**  Zwracanie informacje o zarządzanym wyjątku do klientów może stanowić zagrożenie bezpieczeństwa. Jest to spowodowane szczegóły wyjątku ujawniać informacje o implementacji usługi wewnętrznej, która mogłaby być używana przez nieautoryzowane klientów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienie `includeExceptionDetailInFaults` do `true` umożliwia zwracanej każdy wyjątek, który jest zgłaszany przez kod aplikacji, nawet jeśli wyjątek nie jest zadeklarowany za pomocą usługi <xref:System.ServiceModel.FaultContractAttribute>. To ustawienie jest przydatne podczas debugowania przypadków, gdy serwer jest zgłaszanie nieoczekiwany wyjątek. Za pomocą tego atrybutu, zwracany jest serializowane postaci nieznany wyjątek i sprawdzić szczegółowe informacje o wyjątku.  
  
> [!CAUTION]
>  Zwracanie informacje o zarządzanym wyjątku do klientów może być to zagrożenie bezpieczeństwa, ponieważ szczegóły wyjątku ujawniać informacje o implementacji usługi wewnętrznej, która mogłaby być używana przez nieautoryzowane klientów. Ze względu na zagadnień związanych z zabezpieczeniami zaleca się, że tylko w tym kontrolowanymi scenariuszami debugowania. Należy ustawić `includeExceptionDetailInFaults` do `false` podczas wdrażania aplikacji.  
  
 Aby uzyskać szczegółowe informacje o problemach zabezpieczeń związane z wyjątków zarządzanych, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Przykładowy kod, zobacz [zachowanie debugowania usług](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Można również ustawić `httpsHelpPageEnabled` i `httpsHelpPageUrl` Aby włączyć lub wyłączyć strony pomocy. Każda usługa Opcjonalnie można ujawnić stronę pomocy, który zawiera informacje dotyczące usługi, w tym punkt końcowy, aby uzyskać WSDL usługi. To może być włączona `httpHelpPageEnabled` do `true`. Dzięki temu strony pomocy do zwrócenia na żądanie GET do podstawowego adresu usługi. Ten adres można zmienić, określając `httpHelpPageUrl` atrybutu. Ponadto można zapewnić to bezpieczeństwo za pośrednictwem protokołu HTTPS zamiast protokołu HTTP.  
  
 Opcjonalny `httpHelpPageBinding` i `httpHelpPageBinding` atrybutów umożliwiają skonfigurowanie powiązań umożliwiający dostęp do strony sieci web usługi. Jeśli nie są określone, domyślne powiązania (`HttpTransportBindingElement`, w przypadku protokołu HTTP i `HttpsTransportBindingElement`, w przypadku protokołu HTTPS) są używane do dostępu do strony pomocy usługi zgodnie z potrzebami. Należy zauważyć, że nie możesz użyć tych atrybutów z wbudowanych powiązaniami WCF. Tylko powiązania z elementami wewnętrznymi powiązania, które obsługują xref:System.ServiceModel.Channels.IReplyChannel > będą obsługiwane. Ponadto <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> właściwości powiązania musi być <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Obsługa wyjątków i błędów](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Zachowanie debugowania usług](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)
