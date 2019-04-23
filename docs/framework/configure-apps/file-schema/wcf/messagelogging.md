---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191581"
---
# <a name="messagelogging"></a><span data-ttu-id="c748c-101">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="c748c-101">\<messageLogging></span></span>
<span data-ttu-id="c748c-102">Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c748c-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="c748c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c748c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c748c-104">\<diagnostyczne ></span><span class="sxs-lookup"><span data-stu-id="c748c-104">\<diagnostic></span></span>  
<span data-ttu-id="c748c-105">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="c748c-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c748c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c748c-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c748c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c748c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c748c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c748c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c748c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c748c-109">Attributes</span></span>  
  
|<span data-ttu-id="c748c-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c748c-110">Attribute</span></span>|<span data-ttu-id="c748c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c748c-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="c748c-112">Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="c748c-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="c748c-113">Wartość domyślna to `false`, co oznacza, że tylko nagłówek wiadomości jest rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="c748c-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="c748c-114">To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatu (usługi, transport i jest źle sformułowane).</span><span class="sxs-lookup"><span data-stu-id="c748c-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="c748c-115">Wartość logiczna określająca czy wadliwe komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="c748c-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="c748c-116">Źle sformułowane komunikaty nie są uwzględniane w kierunku `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="c748c-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="c748c-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c748c-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="c748c-118">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowania — i transformacjami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="c748c-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="c748c-119">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c748c-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="c748c-120">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="c748c-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="c748c-121">Filtry w pliku konfiguracyjnym zostały zastosowane, a tylko te komunikaty, które pasują do filtrów są śledzone.</span><span class="sxs-lookup"><span data-stu-id="c748c-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="c748c-122">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c748c-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="c748c-123">Dodatnia liczba całkowita, określająca maksymalną liczbę wiadomości rejestrowaną w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="c748c-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="c748c-124">Wartość domyślna to 1000.</span><span class="sxs-lookup"><span data-stu-id="c748c-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="c748c-125">Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach, komunikat do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="c748c-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="c748c-126">Większy niż limit komunikaty nie zostaną zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="c748c-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="c748c-127">To ustawienie ma wpływ na wszystkie poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c748c-127">This setting affects all trace levels.</span></span> <span data-ttu-id="c748c-128">Wartość domyślna to 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="c748c-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c748c-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c748c-129">Child Elements</span></span>  
  
|<span data-ttu-id="c748c-130">Element</span><span class="sxs-lookup"><span data-stu-id="c748c-130">Element</span></span>|<span data-ttu-id="c748c-131">Opis</span><span class="sxs-lookup"><span data-stu-id="c748c-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c748c-132">filtry</span><span class="sxs-lookup"><span data-stu-id="c748c-132">filters</span></span>|<span data-ttu-id="c748c-133">`filters` Element przetrzymuje kolekcję filtrów XPath.</span><span class="sxs-lookup"><span data-stu-id="c748c-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="c748c-134">Po włączeniu rejestrowania komunikatów transportu (`logMessagesAtTransportLevel` jest `true`), będą rejestrowane tylko wiadomości pasujące do filtrów.</span><span class="sxs-lookup"><span data-stu-id="c748c-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="c748c-135">Filtry są stosowane tylko w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="c748c-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="c748c-136">Rejestrowanie komunikatów poziomu i źle sformułowane usługi nie dotyczy filtrów.</span><span class="sxs-lookup"><span data-stu-id="c748c-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="c748c-137">To jedyny atrybut dla tego elementu `filter`, to obiekt XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="c748c-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="c748c-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c748c-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c748c-139">Element</span><span class="sxs-lookup"><span data-stu-id="c748c-139">Element</span></span>|<span data-ttu-id="c748c-140">Opis</span><span class="sxs-lookup"><span data-stu-id="c748c-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c748c-141">diagnostyka</span><span class="sxs-lookup"><span data-stu-id="c748c-141">diagnostics</span></span>|<span data-ttu-id="c748c-142">Definiuje ustawienia WCF dla środowiska uruchomieniowego kontroli i kontroli dla administratora.</span><span class="sxs-lookup"><span data-stu-id="c748c-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c748c-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c748c-143">Remarks</span></span>  
 <span data-ttu-id="c748c-144">Komunikaty są rejestrowane na trzech różnych poziomach w stosie: usługa, transport i jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="c748c-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="c748c-145">Każdy poziom można aktywować oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="c748c-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="c748c-146">Filtrach XPath można dodać do logowania określonego wiadomości na poziomie transportu i usług.</span><span class="sxs-lookup"><span data-stu-id="c748c-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="c748c-147">Jeśli zdefiniowano żadnych filtrów, wszystkie komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="c748c-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="c748c-148">Filtry są stosowane tylko do nagłówków wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c748c-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="c748c-149">Treść jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="c748c-149">The body is ignored.</span></span> <span data-ttu-id="c748c-150">Usługi WCF ignoruje treść wiadomości, aby zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="c748c-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="c748c-151">Jeśli chcesz filtrować na podstawie zawartości treści, można utworzyć odbiornika niestandardowych za pomocą filtru, która wykonuje.</span><span class="sxs-lookup"><span data-stu-id="c748c-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="c748c-152">Należy utworzyć odbiornik śledzenia, aby uaktywnić śledzenie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c748c-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="c748c-153">Odbiornik, sama może być dowolnym odbiornik, który współdziała z <xref:System.Diagnostics> architektury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c748c-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="c748c-154">Poniższy przykład przedstawia sposób tworzenia takie odbiornik.</span><span class="sxs-lookup"><span data-stu-id="c748c-154">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c748c-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="c748c-155">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c748c-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c748c-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="c748c-157">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="c748c-157">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
