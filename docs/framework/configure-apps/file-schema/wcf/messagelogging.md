---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191581"
---
# <a name="messagelogging"></a><span data-ttu-id="5a8c6-101">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="5a8c6-101">\<messageLogging></span></span>
<span data-ttu-id="5a8c6-102">Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5a8c6-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="5a8c6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a8c6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a8c6-104">\<diagnostyczne ></span><span class="sxs-lookup"><span data-stu-id="5a8c6-104">\<diagnostic></span></span>  
<span data-ttu-id="5a8c6-105">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="5a8c6-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8c6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a8c6-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a8c6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5a8c6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5a8c6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a8c6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5a8c6-109">Attributes</span></span>  
  
|<span data-ttu-id="5a8c6-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5a8c6-110">Attribute</span></span>|<span data-ttu-id="5a8c6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5a8c6-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="5a8c6-112">Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="5a8c6-113">Wartość domyślna to `false`, co oznacza, że tylko nagłówek wiadomości jest rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="5a8c6-114">To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatu (usługi, transport i jest źle sformułowane).</span><span class="sxs-lookup"><span data-stu-id="5a8c6-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="5a8c6-115">Wartość logiczna określająca czy wadliwe komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="5a8c6-116">Źle sformułowane komunikaty nie są uwzględniane w kierunku `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="5a8c6-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="5a8c6-118">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowania — i transformacjami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="5a8c6-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="5a8c6-119">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="5a8c6-120">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="5a8c6-121">Filtry w pliku konfiguracyjnym zostały zastosowane, a tylko te komunikaty, które pasują do filtrów są śledzone.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="5a8c6-122">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="5a8c6-123">Dodatnia liczba całkowita, określająca maksymalną liczbę wiadomości rejestrowaną w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="5a8c6-124">Wartość domyślna to 1000.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="5a8c6-125">Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach, komunikat do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="5a8c6-126">Większy niż limit komunikaty nie zostaną zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="5a8c6-127">To ustawienie ma wpływ na wszystkie poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-127">This setting affects all trace levels.</span></span> <span data-ttu-id="5a8c6-128">Wartość domyślna to 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="5a8c6-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a8c6-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5a8c6-129">Child Elements</span></span>  
  
|<span data-ttu-id="5a8c6-130">Element</span><span class="sxs-lookup"><span data-stu-id="5a8c6-130">Element</span></span>|<span data-ttu-id="5a8c6-131">Opis</span><span class="sxs-lookup"><span data-stu-id="5a8c6-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a8c6-132">filtry</span><span class="sxs-lookup"><span data-stu-id="5a8c6-132">filters</span></span>|<span data-ttu-id="5a8c6-133">`filters` Element przetrzymuje kolekcję filtrów XPath.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="5a8c6-134">Po włączeniu rejestrowania komunikatów transportu (`logMessagesAtTransportLevel` jest `true`), będą rejestrowane tylko wiadomości pasujące do filtrów.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="5a8c6-135">Filtry są stosowane tylko w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="5a8c6-136">Rejestrowanie komunikatów poziomu i źle sformułowane usługi nie dotyczy filtrów.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="5a8c6-137">To jedyny atrybut dla tego elementu `filter`, to obiekt XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a8c6-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5a8c6-138">Parent Elements</span></span>  
  
|<span data-ttu-id="5a8c6-139">Element</span><span class="sxs-lookup"><span data-stu-id="5a8c6-139">Element</span></span>|<span data-ttu-id="5a8c6-140">Opis</span><span class="sxs-lookup"><span data-stu-id="5a8c6-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a8c6-141">diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5a8c6-141">diagnostics</span></span>|<span data-ttu-id="5a8c6-142">Definiuje ustawienia WCF dla środowiska uruchomieniowego kontroli i kontroli dla administratora.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a8c6-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a8c6-143">Remarks</span></span>  
 <span data-ttu-id="5a8c6-144">Komunikaty są rejestrowane na trzech różnych poziomach w stosie: usługa, transport i jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="5a8c6-145">Każdy poziom można aktywować oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="5a8c6-146">Filtrach XPath można dodać do logowania określonego wiadomości na poziomie transportu i usług.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="5a8c6-147">Jeśli zdefiniowano żadnych filtrów, wszystkie komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="5a8c6-148">Filtry są stosowane tylko do nagłówków wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="5a8c6-149">Treść jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-149">The body is ignored.</span></span> <span data-ttu-id="5a8c6-150">Usługi WCF ignoruje treść wiadomości, aby zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="5a8c6-151">Jeśli chcesz filtrować na podstawie zawartości treści, można utworzyć odbiornika niestandardowych za pomocą filtru, która wykonuje.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="5a8c6-152">Należy utworzyć odbiornik śledzenia, aby uaktywnić śledzenie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="5a8c6-153">Odbiornik, sama może być dowolnym odbiornik, który współdziała z <xref:System.Diagnostics> architektury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="5a8c6-154">Poniższy przykład przedstawia sposób tworzenia takie odbiornik.</span><span class="sxs-lookup"><span data-stu-id="5a8c6-154">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="5a8c6-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a8c6-155">Example</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="5a8c6-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a8c6-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="5a8c6-157">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="5a8c6-157">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
