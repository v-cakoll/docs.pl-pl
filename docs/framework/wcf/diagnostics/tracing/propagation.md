---
title: Propagacja
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578958"
---
# <a name="propagation"></a><span data-ttu-id="98761-102">Propagacja</span><span class="sxs-lookup"><span data-stu-id="98761-102">Propagation</span></span>
<span data-ttu-id="98761-103">W tym temacie opisano propagację działań w modelu śledzenia Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="98761-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="98761-104">Używanie propagacji do skorelowania działań w punktach końcowych</span><span class="sxs-lookup"><span data-stu-id="98761-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="98761-105">Propagacja udostępnia użytkownikowi bezpośrednią korelację śladów błędów dla tej samej jednostki przetwarzania między punktami końcowymi aplikacji, na przykład żądania.</span><span class="sxs-lookup"><span data-stu-id="98761-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="98761-106">Błędy emitowane w różnych punktach końcowych dla tej samej jednostki przetwarzania są pogrupowane w tym samym działaniu, nawet w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98761-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="98761-107">Jest to realizowane przez propagację identyfikatora działania w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="98761-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="98761-108">W związku z tym, jeśli klient przeprowadzi limit czasu z powodu błędu wewnętrznego na serwerze, oba błędy pojawiają się w tym samym działaniu dla bezpośredniej korelacji.</span><span class="sxs-lookup"><span data-stu-id="98761-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="98761-109">Aby to zrobić, użyj `ActivityTracing` Ustawienia, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="98761-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="98761-110">Ponadto należy ustawić `propagateActivity` atrybut dla `System.ServiceModel` źródła śledzenia we wszystkich punktach końcowych.</span><span class="sxs-lookup"><span data-stu-id="98761-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="98761-111">Propagacja działań to konfigurowalna funkcja, która powoduje, że program WCF dodaje nagłówek do komunikatów wychodzących, który obejmuje identyfikator działania w protokole TLS.</span><span class="sxs-lookup"><span data-stu-id="98761-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="98761-112">W tym celu w przypadku kolejnych śladów po stronie serwera można skorelować działania klientów i serwerów.</span><span class="sxs-lookup"><span data-stu-id="98761-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="98761-113">Definicja propagacji</span><span class="sxs-lookup"><span data-stu-id="98761-113">Propagation Definition</span></span>  
 <span data-ttu-id="98761-114">Podczas działania gAId M jest propagowany do działania N, jeśli spełnione są wszystkie poniższe warunki.</span><span class="sxs-lookup"><span data-stu-id="98761-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
- <span data-ttu-id="98761-115">N jest tworzony z powodu M</span><span class="sxs-lookup"><span data-stu-id="98761-115">N is created because of M</span></span>  
  
- <span data-ttu-id="98761-116">GAId M jest znany jako N</span><span class="sxs-lookup"><span data-stu-id="98761-116">M’s gAId is known to N</span></span>  
  
- <span data-ttu-id="98761-117">GAId N jest równe gAId M.</span><span class="sxs-lookup"><span data-stu-id="98761-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="98761-118">GAId jest propagowany za pomocą nagłówka komunikatu ActivityId, jak pokazano w poniższym schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="98761-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="98761-119">Poniżej znajduje się przykład nagłówka komunikatu.</span><span class="sxs-lookup"><span data-stu-id="98761-119">The following is an example of the message header.</span></span>  
  
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
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="98761-120">Propagowanie i granice działania</span><span class="sxs-lookup"><span data-stu-id="98761-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="98761-121">Gdy identyfikator działania jest propagowany między punktami końcowymi, odbiorca komunikatów emituje uruchomienie i zatrzymanie śladów z tym (propagowanym) IDENTYFIKATORem działania.</span><span class="sxs-lookup"><span data-stu-id="98761-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="98761-122">W związku z tym istnieje rozpoczęcie i zatrzymanie śledzenia z tym gAId z każdego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="98761-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="98761-123">Jeśli punkty końcowe są w tym samym procesie i używają tej samej nazwy źródła śledzenia, są tworzone wiele operacji uruchamiania i zatrzymywania z tymi samymi (gAId, tym samym źródłem śladów).</span><span class="sxs-lookup"><span data-stu-id="98761-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="98761-124">Synchronizacja</span><span class="sxs-lookup"><span data-stu-id="98761-124">Synchronization</span></span>  
 <span data-ttu-id="98761-125">Aby synchronizować zdarzenia między punktami końcowymi, które działają na różnych komputerach, identyfikator korelacji jest dodawany do nagłówka ActivityId, który jest propagowany w komunikatach.</span><span class="sxs-lookup"><span data-stu-id="98761-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="98761-126">Narzędzia mogą używać tego identyfikatora do synchronizowania zdarzeń między maszynami z niezgodnością zegara.</span><span class="sxs-lookup"><span data-stu-id="98761-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="98761-127">Narzędzie Podgląd śledzenia usług używa tego identyfikatora do wyświetlania przepływów komunikatów między punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="98761-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98761-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98761-128">See also</span></span>

- [<span data-ttu-id="98761-129">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="98761-129">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="98761-130">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="98761-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="98761-131">Scenariusze kompleksowego śledzenia</span><span class="sxs-lookup"><span data-stu-id="98761-131">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="98761-132">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="98761-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
