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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8df32a64c07db8a45dfb41a46e7a65a92fbef434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-message-flow-tracing"></a><span data-ttu-id="6d470-102">Konfigurowanie śledzenia przepływu komunikatów</span><span class="sxs-lookup"><span data-stu-id="6d470-102">Configuring Message Flow Tracing</span></span>
<span data-ttu-id="6d470-103">Gdy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] czynność śledzenia jest włączona, End-To-End identyfikatory aktywności są przypisane do logicznego działań w całym [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stosu.</span><span class="sxs-lookup"><span data-stu-id="6d470-103">When [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] activity tracing is enabled, End-To-End Activity IDs are assigned to logical activities throughout the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack.</span></span> <span data-ttu-id="6d470-104">W [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], jest teraz wyższą wersję wydajności tej funkcji, która działa z zdarzenia śledzenia dla systemu Windows (ETW) o nazwie śledzenia przepływu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6d470-104">In [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], there is now a higher performance version of this feature that works with Event Tracing for Windows (ETW) called message flow tracing.</span></span> <span data-ttu-id="6d470-105">Po włączeniu End-To-End identyfikatory aktywności są pobierane z (lub przypisane do, jeśli puste) wiadomości przychodzących i są propagowane do wszystkich zdarzeń śledzenia, które są emitowane po wiadomość ma został odczytany przez kanał.</span><span class="sxs-lookup"><span data-stu-id="6d470-105">When enabled, End-To-End activity IDs are taken from (or assigned to if empty) incoming messages and are propagated to all tracing events that are emitted after the message has been decoded by the channel.</span></span> <span data-ttu-id="6d470-106">Klientów można użyć tej funkcji odtworzenie po dekodowania przepływów wiadomości z dziennikami śledzenia z różnych usług.</span><span class="sxs-lookup"><span data-stu-id="6d470-106">Customers can use this feature to reconstruct message flows with trace logs from different services after decoding.</span></span>  
  
 <span data-ttu-id="6d470-107">Śledzenie można włączona po zostanie wykryty problem z aplikacją i następnie wyłączone, po usunięciu problemu.</span><span class="sxs-lookup"><span data-stu-id="6d470-107">Tracing can be enabled after a problem is detected with the application and then disabled once the problem is resolved.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="6d470-108">Włączenie debugowania</span><span class="sxs-lookup"><span data-stu-id="6d470-108">Enabling Tracing</span></span>  
 <span data-ttu-id="6d470-109">Można włączyć śledzenia przepływu komunikatów przez ustawienie dla platformy .NET Framework 4 `messageFlowTracing` element konfiguracji do `true`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d470-109">You can enable message flow tracing by setting the .NET Framework 4 `messageFlowTracing` configuration element to `true`, as shown in the following example.</span></span>  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="6d470-110">Ponieważ `endToEndTracing` element konfiguracji znajduje się w pliku Web.config, nie może być dynamicznie skonfigurowane w taki sam sposób jak ETW.</span><span class="sxs-lookup"><span data-stu-id="6d470-110">Because the `endToEndTracing` configuration element resides in a Web.config file, it cannot be dynamically configured in the same way as ETW.</span></span> <span data-ttu-id="6d470-111">Aby uzyskać `endToEndTracing` element konfiguracji zaczęły obowiązywać, aplikacja musi zostać odtworzona.</span><span class="sxs-lookup"><span data-stu-id="6d470-111">For the `endToEndTracing` configuration element to take effect, the application must be recycled.</span></span>  
  
 <span data-ttu-id="6d470-112">Działania są skorelowane przez wymianę identyfikatora identyfikator działania.</span><span class="sxs-lookup"><span data-stu-id="6d470-112">Activities are correlated by the interchange of an identifier called the activity ID.</span></span> <span data-ttu-id="6d470-113">Ten identyfikator jest identyfikatorem GUID i jest generowany przez klasę System.Diagnostics.CorrelationManager.</span><span class="sxs-lookup"><span data-stu-id="6d470-113">This identifier is a GUID, and is generated by the System.Diagnostics.CorrelationManager class.</span></span> <span data-ttu-id="6d470-114">Manipulowanie System.Diagnostics.Trace.CorrelationManager.ActivityID, upewnij się, że ma wartość z oryginalną przesyłania Kontrola wykonywania przywracając WCF kodu.</span><span class="sxs-lookup"><span data-stu-id="6d470-114">If you manipulate System.Diagnostics.Trace.CorrelationManager.ActivityID, ensure that the value is set to original when execution control transfers back to WCF code.</span></span>  <span data-ttu-id="6d470-115">Ponadto jeśli używasz modelu programowania asynchronicznego WCF upewnij się, że System.Diagnostics.Trace.CorrelationManager.ActivityID są przesyłane między wątkami.</span><span class="sxs-lookup"><span data-stu-id="6d470-115">Also, if you use an asynchronous WCF programming model ensure that System.Diagnostics.Trace.CorrelationManager.ActivityID is transferred between the threads.</span></span>  
  
## <a name="message-flow-tracing-and-rest-services"></a><span data-ttu-id="6d470-116">Usługi REST i śledzenia przepływu komunikatów</span><span class="sxs-lookup"><span data-stu-id="6d470-116">Message Flow Tracing and REST Services</span></span>  
 <span data-ttu-id="6d470-117">Śledzenia przepływu komunikatów służy do żądania pełnego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6d470-117">Message flow tracing allows you to trace a request end to end.</span></span>  <span data-ttu-id="6d470-118">Z usług opartych na protokole SOAP identyfikator działania jest wysyłany w nagłówku wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6d470-118">With SOAP-based services an Activity ID is sent in a SOAP message header.</span></span> <span data-ttu-id="6d470-119">REST nie zawierają tego nagłówka, zamiast niego jest używana specjalne Nagłówek zdarzenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="6d470-119">REST requests do not contain this header so a special HTTP event header is used instead.</span></span> <span data-ttu-id="6d470-120">Poniższy fragment kodu przedstawia, jak programowo można pobrać wartości identyfikator działania:</span><span class="sxs-lookup"><span data-stu-id="6d470-120">The following code snippet shows how you can programmatically retrieve the Activity ID value:</span></span>  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 <span data-ttu-id="6d470-121">Programowo można dodać nagłówka, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6d470-121">You can programmatically add the header using the following code:</span></span>  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
