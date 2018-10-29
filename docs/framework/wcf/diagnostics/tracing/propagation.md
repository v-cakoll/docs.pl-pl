---
title: Propagacja
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 1d5ac743e94edd845650a1b550b3e982929d1b32
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198253"
---
# <a name="propagation"></a><span data-ttu-id="942cd-102">Propagacja</span><span class="sxs-lookup"><span data-stu-id="942cd-102">Propagation</span></span>
<span data-ttu-id="942cd-103">W tym temacie opisano Propagacja działania w modelu śledzenia usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="942cd-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="942cd-104">Korelowanie działania punktów końcowych przy użyciu propagacji</span><span class="sxs-lookup"><span data-stu-id="942cd-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="942cd-105">Propagacja zapewnia użytkownikowi bezpośrednia korelacja błąd ślady dla tej samej jednostki przetwarzania między punktami końcowymi aplikacji, na przykład żądania.</span><span class="sxs-lookup"><span data-stu-id="942cd-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="942cd-106">Emitowane na różne punkty końcowe dla tej samej jednostki przetwarzania, błędy są grupowane w tym samym działaniu, nawet w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="942cd-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="942cd-107">Jest to realizowane za pośrednictwem Propagacja identyfikatora działania w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="942cd-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="942cd-108">W związku z tym jeśli upłynie limit czasu klienta z powodu wewnętrznego błędu serwera, oba błędy są wyświetlane w tym samym działaniu dla bezpośrednia korelacja.</span><span class="sxs-lookup"><span data-stu-id="942cd-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="942cd-109">Aby to zrobić, należy użyć `ActivityTracing` ustawienia, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="942cd-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="942cd-110">Dodatkowo, ustawienia `propagateActivity` atrybutu dla `System.ServiceModel` źródła śledzenia w wszystkie punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="942cd-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="942cd-111">Propagacja działania jest konfigurowalnych możliwości, który powoduje, że WCF można dodać nagłówka do wiadomości wychodzących, która zawiera identyfikator działania na TLS.</span><span class="sxs-lookup"><span data-stu-id="942cd-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="942cd-112">Jeśli dołączysz to na kolejne ślady po stronie serwera, firma Microsoft skorelować działania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="942cd-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="942cd-113">Propagacji definicji</span><span class="sxs-lookup"><span data-stu-id="942cd-113">Propagation Definition</span></span>  
 <span data-ttu-id="942cd-114">GAId M działania jest propagowana do działania N, jeśli wszystkie następujące warunki zastosowania.</span><span class="sxs-lookup"><span data-stu-id="942cd-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
-   <span data-ttu-id="942cd-115">N jest tworzony z powodu M</span><span class="sxs-lookup"><span data-stu-id="942cd-115">N is created because of M</span></span>  
  
-   <span data-ttu-id="942cd-116">Wiadomo gAId firmy M, N</span><span class="sxs-lookup"><span data-stu-id="942cd-116">M’s gAId is known to N</span></span>  
  
-   <span data-ttu-id="942cd-117">GAId firmy N jest równy gAId firmy M.</span><span class="sxs-lookup"><span data-stu-id="942cd-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="942cd-118">GAId są propagowane przez identyfikator nagłówka wiadomości, jak pokazano w poniższym schematu XML.</span><span class="sxs-lookup"><span data-stu-id="942cd-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="942cd-119">Oto przykład nagłówka komunikatu.</span><span class="sxs-lookup"><span data-stu-id="942cd-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="942cd-120">Propagacja i granice działania</span><span class="sxs-lookup"><span data-stu-id="942cd-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="942cd-121">Po identyfikator działania są propagowane w obrębie punktów końcowych, odbiorcom wiadomości emituje jest rozpoczęcie i zatrzymanie ślady za pomocą tego identyfikatora działania (propagowany).</span><span class="sxs-lookup"><span data-stu-id="942cd-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="942cd-122">Dlatego jest uruchamianie i zatrzymywanie śledzenia przy użyciu tego gAId z każdego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="942cd-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="942cd-123">Jeśli punkty końcowe są w tym samym procesie, użyj tej samej nazwy źródła śledzenia wielu uruchamianie i zatrzymywanie, o tej samej sekcji (tego samego gAId, tego samego źródła śledzenia, ten sam proces) są tworzone.</span><span class="sxs-lookup"><span data-stu-id="942cd-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="942cd-124">Synchronizacja</span><span class="sxs-lookup"><span data-stu-id="942cd-124">Synchronization</span></span>  
 <span data-ttu-id="942cd-125">Aby zsynchronizować zdarzenia różnych punktów końcowych, które działają na różnych maszynach, CorrelationId jest dodawany do nagłówka ActivityId, która jest propagowana do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="942cd-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="942cd-126">Narzędzia można użyć tego Identyfikatora synchronizacji zdarzeń na komputerach z rozbieżność zegara.</span><span class="sxs-lookup"><span data-stu-id="942cd-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="942cd-127">W szczególności narzędzia przeglądarki danych śledzenia usługi używa tego Identyfikatora do wyświetlania komunikatu przepływów między punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="942cd-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="942cd-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="942cd-128">See Also</span></span>  
 [<span data-ttu-id="942cd-129">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="942cd-129">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="942cd-130">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="942cd-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="942cd-131">Scenariusze kompleksowego śledzenia</span><span class="sxs-lookup"><span data-stu-id="942cd-131">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="942cd-132">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="942cd-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
