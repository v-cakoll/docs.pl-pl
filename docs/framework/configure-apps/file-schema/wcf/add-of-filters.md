---
title: <add> dla <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926698"
---
# <a name="add-of-filters"></a>\<Dodawanie > \<filtrów >
Filtr XPath określa rodzaj wiadomości do zarejestrowania.  
  
 \<system.ServiceModel>  
\<> diagnostyki  
\<messageLogging >  
\<Filtry >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|filtr|Ciąg określający zapytanie na dokumencie XML zdefiniowanym przez wyrażenie XPath 1,0. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtry >](filters.md)|Zawiera kolekcję filtrów XPath używanych do kontroli rodzaju rejestrowanych komunikatów.|  
  
## <a name="remarks"></a>Uwagi  
 Filtry są stosowane tylko w warstwie transportowej, określonej `logMessagesAtTransportLevel` przez `true`is. Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.  
  
 Aby dodać filtr do kolekcji, użyj `add` słowa kluczowego. Jeśli zdefiniowano co najmniej jeden filtr, rejestrowane są tylko komunikaty zgodne z co najmniej jednym filtrem. Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty są przekazywane.  
  
 Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w której pojawiają się w pliku konfiguracji. Składnia nieprawidłowego filtru powoduje wyjątek w konfiguracji.  
  
 Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Konfigurowanie rejestrowania komunikatów](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging >](messagelogging.md)
