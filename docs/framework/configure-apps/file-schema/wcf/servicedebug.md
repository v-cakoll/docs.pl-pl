---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 4eb79cc91ef489501c4c8bb6311f240d855ed053
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399646"
---
# <a name="servicedebug"></a>\<serviceDebug>
Określa funkcje debugowania i pomocy dla usługi Windows Communication Foundation (WCF).  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> serviceDebug**  
  
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
|httpHelpPageBinding|Wartość ciągu określająca typ powiązania, który ma być używany podczas korzystania z protokołu HTTP w celu uzyskania dostępu do strony pomocy usługi.<br /><br /> Obsługiwane są tylko powiązania z wewnętrznymi elementami <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> powiązania, które obsługują. Ponadto właściwość powiązania <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musi mieć <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>wartość.|  
|httpHelpPageBindingConfiguration|Ciąg określający nazwę powiązania, które jest określone w `httpHelpPageBinding` atrybucie, który odwołuje się do dodatkowych informacji konfiguracyjnych tego powiązania. Ta sama nazwa musi być zdefiniowana w `<bindings>` sekcji.|  
|httpHelpPageEnabled|Wartość logiczna, która kontroluje, czy WCF publikuje stronę pomocy HTML pod adresem określonym przez `httpHelpPageUrl` atrybut. Wartość domyślna to `true`.<br /><br /> Możesz ustawić tę właściwość na `false` , aby wyłączyć publikację strony pomocy HTML widocznej dla przeglądarek html.<br /><br /> Aby upewnić się, że strona pomocy HTML jest publikowana w lokalizacji `httpHelpPageUrl` kontrolowanej przez atrybut, należy ustawić ten `true`atrybut na. Ponadto musi być spełniony jeden z następujących warunków:<br /><br /> `httpHelpPageUrl` -Atrybut jest adresem bezwzględnym, który obsługuje schemat protokołu HTTP.<br />-Istnieje adres podstawowy usługi obsługujący schemat protokołu HTTP.<br /><br /> Chociaż wyjątek jest zgłaszany, jeśli adres bezwzględny, który nie obsługuje schematu protokołu HTTP jest przypisany do `httpHelpPageUrl` atrybutu, każdy inny scenariusz, w którym żaden z powyższych kryteriów nie jest spełniony, powoduje brak wyjątku i stronę pomocy HTML.|  
|httpHelpPageUrl|Identyfikator URI, który określa względny lub bezwzględny adres URL oparty na protokole HTTP niestandardowego pliku pomocy HTML, który użytkownik widzi, gdy punkt końcowy jest wyświetlany w przeglądarce HTML.<br /><br /> Tego atrybutu można użyć, aby umożliwić korzystanie z niestandardowego pliku pomocy HTML, który jest zwracany z żądania HTTP/GET, na przykład z przeglądarki HTML. Lokalizacja pliku pomocy HTML jest rozpoznawana w następujący sposób.<br /><br /> 1.  Jeśli wartość tego atrybutu jest adresem względnym, lokalizacja pliku pomocy HTML jest wartością adresu podstawowego usługi, który obsługuje żądania HTTP, oraz tę wartość właściwości.<br />2.  Jeśli wartość tego atrybutu jest adresem bezwzględnym i obsługuje żądania HTTP, lokalizacja pliku pomocy HTML jest wartością tej właściwości.<br />3.  Jeśli wartość tego atrybutu jest bezwzględna, ale nie obsługuje żądań HTTP, zgłaszany jest wyjątek.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, `httpHelpPageEnabled` gdy atrybut `true`jest.|  
|httpsHelpPageBinding|Wartość ciągu określająca typ powiązania, który ma być używany podczas korzystania z protokołu HTTPS w celu uzyskania dostępu do strony pomocy usługi.<br /><br /> Obsługiwane są tylko powiązania z wewnętrznymi elementami <xref:System.ServiceModel.Channels.IReplyChannel> powiązania, które obsługują. Ponadto właściwość powiązania <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musi mieć <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>wartość.|  
|httpsHelpPageBindingConfiguration|Ciąg określający nazwę powiązania, które jest określone w `httpsHelpPageBinding` atrybucie, który odwołuje się do dodatkowych informacji konfiguracyjnych tego powiązania. Ta sama nazwa musi być zdefiniowana w `<bindings>` sekcji.|  
|httpsHelpPageEnabled|Wartość logiczna, która kontroluje, czy WCF publikuje stronę pomocy HTML pod adresem określonym przez `httpsHelpPageUrl` atrybut. Wartość domyślna to `true`.<br /><br /> Możesz ustawić tę właściwość na `false` , aby wyłączyć publikację strony pomocy HTML widocznej dla przeglądarek html.<br /><br /> Aby upewnić się, że strona pomocy HTML jest publikowana w lokalizacji `httpsHelpPageUrl` kontrolowanej przez atrybut, należy ustawić ten `true`atrybut na. Ponadto musi być spełniony jeden z następujących warunków:<br /><br /> `httpsHelpPageUrl` -Atrybut jest adresem bezwzględnym, który obsługuje schemat protokołu HTTPS.<br />-Istnieje adres podstawowy usługi obsługujący schemat protokołu HTTPS.<br /><br /> Chociaż wyjątek jest zgłaszany, jeśli adres bezwzględny, który nie obsługuje schematu protokołu HTTPS jest przypisany do `httpsHelpPageUrl` atrybutu, każdy inny scenariusz, w którym żaden z powyższych kryteriów nie jest spełniony, powoduje brak wyjątku i stronę pomocy HTML.|  
|httpsHelpPageUrl|Identyfikator URI, który określa względny lub bezwzględny adres URL oparty na protokole HTTPS niestandardowego pliku pomocy HTML, który użytkownik widzi, gdy punkt końcowy jest wyświetlany w przeglądarce HTML.<br /><br /> Tego atrybutu można użyć, aby umożliwić korzystanie z niestandardowego pliku pomocy HTML, który jest zwracany z żądania HTTPS/GET, na przykład z przeglądarki HTML. Lokalizacja pliku pomocy HTML jest rozpoznawana w następujący sposób:<br /><br /> — Jeśli wartość tej właściwości jest adresem względnym, lokalizacja pliku pomocy HTML jest wartością adresu podstawowego usługi, który obsługuje żądania HTTPS, oraz tę wartość właściwości.<br />— Jeśli wartość tej właściwości jest adresem bezwzględnym i obsługuje żądania HTTPS, lokalizacja pliku pomocy HTML jest wartością tej właściwości.<br />-Jeśli wartość tej właściwości jest bezwzględna, ale nie obsługuje żądań HTTPS, zgłaszany jest wyjątek.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, `httpHelpPageEnabled` gdy atrybut `true`jest.|  
|includeExceptionDetailInFaults|Wartość określająca, czy w celach debugowania mają być uwzględniane informacje o zarządzanych wyjątkach. Wartość domyślna to `false`.<br /><br /> Jeśli ten atrybut zostanie ustawiony na `true`, można włączyć przepływ informacji o zarządzanych wyjątkach do klienta na potrzeby debugowania, a także publikację plików informacji HTML dla użytkowników przeglądających usługę w przeglądarkach sieci Web. **Ostrzeżenie**  Zwrócenie informacji o wyjątku zarządzanym do klientów może stanowić zagrożenie bezpieczeństwa. Wynika to z faktu, że szczegóły wyjątku ujawniają informacje o implementacji wewnętrznej usługi, która może być używana przez nieautoryzowanych klientów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienie `includeExceptionDetailInFaults` umożliwia usłudze zwrócenie dowolnego wyjątku, który jest generowany przez kod aplikacji, nawet jeśli wyjątek nie <xref:System.ServiceModel.FaultContractAttribute>jest zadeklarowany przy użyciu. `true` To ustawienie jest przydatne w przypadku debugowania, gdy serwer zgłasza nieoczekiwany wyjątek. Korzystając z tego atrybutu, zwracana jest serializowana forma nieznanego wyjątku i można zapoznać się z większą liczbą szczegółów wyjątku.  
  
> [!CAUTION]
> Zwrócenie informacji o wyjątku zarządzanym do klientów może stanowić zagrożenie bezpieczeństwa, ponieważ szczegóły wyjątku ujawniają informacje o implementacji wewnętrznej usługi, która może być używana przez nieautoryzowanych klientów. Ze względu na problemy związane z bezpieczeństwem zdecydowanie zaleca się wykonanie tych czynności tylko w scenariuszach z kontrolowanym debugowaniem. Po wdrożeniu aplikacji należy ustawić wartość `includeExceptionDetailInFaults`. `false`  
  
 Aby uzyskać szczegółowe informacje o problemach z zabezpieczeniami związanymi z wyjątkiem zarządzanym, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md). Aby uzyskać przykład kodu, zobacz [zachowanie debugowania usługi](../../../wcf/samples/service-debug-behavior.md).  
  
 Możesz również ustawić `httpsHelpPageEnabled` i `httpsHelpPageUrl` włączyć lub wyłączyć stronę pomocy. Każda usługa może opcjonalnie uwidocznić stronę pomocy, która zawiera informacje o usłudze, w tym punkt końcowy do pobrania WSDL dla usługi. Można to włączyć, ustawiając wartość `httpHelpPageEnabled`. `true` Dzięki temu strona pomocy ma zostać zwrócona do żądania GET na adres podstawowy usługi. Ten adres można zmienić, ustawiając `httpHelpPageUrl` atrybut. Ponadto można to zabezpieczyć przy użyciu protokołu HTTPS zamiast protokołu HTTP.  
  
 Opcjonalne `httpHelpPageBinding` i`httpHelpPageBinding` atrybuty umożliwiają skonfigurowanie powiązań używanych do uzyskiwania dostępu do strony sieci Web usługi. Jeśli nie są one określone, domyślne powiązania (`HttpTransportBindingElement`w przypadku protokołu HTTP i `HttpsTransportBindingElement`, w przypadku protokołu HTTPS) są używane w celu uzyskania dostępu do strony pomocy usługi. Należy zauważyć, że nie można używać tych atrybutów z wbudowanymi powiązaniami programu WCF. Obsługiwane są tylko powiązania z elementami wewnętrznymi powiązania, które obsługują linki XREF: System. ServiceModel. Channels. IReplyChannel >. Ponadto właściwość powiązania <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> musi mieć <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>wartość.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Określanie i obsługa błędów w kontraktach i usługach](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Obsługa wyjątków i błędów](../../../wcf/extending/handling-exceptions-and-faults.md)
- [Zachowanie debugowania usług](../../../wcf/samples/service-debug-behavior.md)
