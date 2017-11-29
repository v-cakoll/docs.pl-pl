---
title: "Konfigurowanie śledzenia przepływu komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77a7148a0fc96c4a043a06fbfac7b139c7720d4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-message-flow-tracing"></a>Konfigurowanie śledzenia przepływu komunikatów
Gdy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] czynność śledzenia jest włączona, End-To-End identyfikatory aktywności są przypisane do logicznego działań w całym [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stosu. W [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], jest teraz wyższą wersję wydajności tej funkcji, która działa z zdarzenia śledzenia dla systemu Windows (ETW) o nazwie śledzenia przepływu komunikatów. Po włączeniu End-To-End identyfikatory aktywności są pobierane z (lub przypisane do, jeśli puste) wiadomości przychodzących i są propagowane do wszystkich zdarzeń śledzenia, które są emitowane po wiadomość ma został odczytany przez kanał. Klientów można użyć tej funkcji odtworzenie po dekodowania przepływów wiadomości z dziennikami śledzenia z różnych usług.  
  
 Śledzenie można włączona po zostanie wykryty problem z aplikacją i następnie wyłączone, po usunięciu problemu.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Można włączyć śledzenia przepływu komunikatów przez ustawienie dla platformy .NET Framework 4 `messageFlowTracing` element konfiguracji do `true`, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Ponieważ `endToEndTracing` element konfiguracji znajduje się w pliku Web.config, nie może być dynamicznie skonfigurowane w taki sam sposób jak ETW. Aby uzyskać `endToEndTracing` element konfiguracji zaczęły obowiązywać, aplikacja musi zostać odtworzona.  
  
 Działania są skorelowane przez wymianę identyfikatora identyfikator działania. Ten identyfikator jest identyfikatorem GUID i jest generowany przez klasę System.Diagnostics.CorrelationManager. Manipulowanie System.Diagnostics.Trace.CorrelationManager.ActivityID, upewnij się, że ma wartość z oryginalną przesyłania Kontrola wykonywania przywracając WCF kodu.  Ponadto jeśli używasz modelu programowania asynchronicznego WCF upewnij się, że System.Diagnostics.Trace.CorrelationManager.ActivityID są przesyłane między wątkami.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Usługi REST i śledzenia przepływu komunikatów  
 Śledzenia przepływu komunikatów służy do żądania pełnego śledzenia.  Z usług opartych na protokole SOAP identyfikator działania jest wysyłany w nagłówku wiadomości protokołu SOAP. REST nie zawierają tego nagłówka, zamiast niego jest używana specjalne Nagłówek zdarzenia HTTP. Poniższy fragment kodu przedstawia, jak programowo można pobrać wartości identyfikator działania:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Programowo można dodać nagłówka, używając następującego kodu:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
