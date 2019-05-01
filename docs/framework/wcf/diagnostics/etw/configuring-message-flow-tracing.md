---
title: Konfigurowanie śledzenia przepływu komunikatów
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999521"
---
# <a name="configuring-message-flow-tracing"></a>Konfigurowanie śledzenia przepływu komunikatów
Gdy włączone jest śledzenie aktywności Windows Communication Foundation (WCF), End-To-End identyfikatory aktywności są przypisane do logicznej działań w całym stosie WCF. W [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], jest teraz nowszą wersją wydajności tę funkcję, która współdziała z śledzenie zdarzeń dla Windows (ETW) o nazwie śledzenia przepływu komunikatów. Po włączeniu End-To-End identyfikatory aktywności są pobierane z (lub przypisane do, jeśli puste) wiadomości przychodzących i są propagowane do wszystkich zdarzeń śledzenia, które są emitowane po ma został zdekodowany komunikat przez kanał. Klienci mogą używać tej funkcji na rekonstrukcję przepływów wiadomości przy użyciu dzienników śledzenia z różnych usług po dekodowania.  
  
 Śledzenie włączone po wykryciu problemu z aplikacją i następnie wyłączone, gdy problem zostanie rozwiązany.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Można włączyć śledzenia przepływu komunikatów przez ustawienie programu .NET Framework 4 `messageFlowTracing` element konfiguracji do `true`, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Ponieważ `endToEndTracing` element konfiguracji, który znajduje się w pliku Web.config, nie można dynamicznie konfigurować w taki sam sposób jak ETW. Aby uzyskać `endToEndTracing` element konfiguracji zaczęły obowiązywać, aplikacja musi zostać odtworzona.  
  
 Działania są powiązane przez wymianę identyfikatora zwanego identyfikator działania. Ten identyfikator jest identyfikatorem GUID i jest generowany przez klasę System.Diagnostics.CorrelationManager. Jeśli manipulować System.Diagnostics.Trace.CorrelationManager.ActivityID upewnij się, że wartość jest równa oryginalny przesyłania Kontrola wykonywania do kodu usługi WCF.  Ponadto jeśli używasz asynchronicznego modelu programowania usług WCF upewnij się, że System.Diagnostics.Trace.CorrelationManager.ActivityID są przesyłane między wątkami.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Śledzenia przepływu komunikatów i usług REST  
 Śledzenia przepływu komunikatów umożliwia śledzenie żądań typu end to end.  Za pomocą usługi oparte na protokole SOAP identyfikator działania jest wysyłany w nagłówku komunikatu protokołu SOAP. Żądania REST nie zawierają tego pliku nagłówkowego, więc specjalne Nagłówek zdarzenia HTTP jest używana zamiast tego. Poniższy fragment kodu przedstawia, jak programowo pobrać wartość identyfikator działania:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Możesz programowo dodać nagłówek, używając następującego kodu:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
