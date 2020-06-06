---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855124"
---
# \<messageLogging>
<span data-ttu-id="baad9-101">Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="baad9-101">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a><span data-ttu-id="baad9-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="baad9-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baad9-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="baad9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="baad9-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="baad9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baad9-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="baad9-105">Attributes</span></span>  
  
|<span data-ttu-id="baad9-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="baad9-106">Attribute</span></span>|<span data-ttu-id="baad9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="baad9-107">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="baad9-108">Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowany.</span><span class="sxs-lookup"><span data-stu-id="baad9-108">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="baad9-109">Wartość domyślna to `false` , co oznacza, że rejestrowany jest tylko nagłówek komunikatu.</span><span class="sxs-lookup"><span data-stu-id="baad9-109">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="baad9-110">To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatów (usługa, transport i nieprawidłowo sformułowane).</span><span class="sxs-lookup"><span data-stu-id="baad9-110">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="baad9-111">Wartość logiczna określająca, czy źle sformułowane komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="baad9-111">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="baad9-112">Źle sformułowane wiadomości nie są wliczane do `maxMessagesToLog` .</span><span class="sxs-lookup"><span data-stu-id="baad9-112">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="baad9-113">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="baad9-113">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="baad9-114">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowaniem i transformami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="baad9-114">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="baad9-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="baad9-115">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="baad9-116">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="baad9-116">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="baad9-117">Wszystkie filtry określone w pliku konfiguracyjnym są stosowane i śledzone są tylko komunikaty zgodne z filtrami.</span><span class="sxs-lookup"><span data-stu-id="baad9-117">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="baad9-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="baad9-118">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="baad9-119">Dodatnia liczba całkowita, która określa maksymalną liczbę komunikatów do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="baad9-119">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="baad9-120">Wartość domyślna to 1000.</span><span class="sxs-lookup"><span data-stu-id="baad9-120">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="baad9-121">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu do zarejestrowania w bajtach.</span><span class="sxs-lookup"><span data-stu-id="baad9-121">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="baad9-122">Komunikaty przekraczające limit nie będą rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="baad9-122">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="baad9-123">To ustawienie ma wpływ na wszystkie poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="baad9-123">This setting affects all trace levels.</span></span> <span data-ttu-id="baad9-124">Wartość domyślna to 262 144 (0x4000).</span><span class="sxs-lookup"><span data-stu-id="baad9-124">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baad9-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="baad9-125">Child Elements</span></span>  
  
|<span data-ttu-id="baad9-126">Element</span><span class="sxs-lookup"><span data-stu-id="baad9-126">Element</span></span>|<span data-ttu-id="baad9-127">Opis</span><span class="sxs-lookup"><span data-stu-id="baad9-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baad9-128">filtry</span><span class="sxs-lookup"><span data-stu-id="baad9-128">filters</span></span>|<span data-ttu-id="baad9-129">`filters`Element przechowuje kolekcję filtrów XPath.</span><span class="sxs-lookup"><span data-stu-id="baad9-129">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="baad9-130">Gdy rejestrowanie komunikatów transportu jest włączone ( `logMessagesAtTransportLevel` is `true` ), rejestrowane będą tylko komunikaty pasujące do filtrów.</span><span class="sxs-lookup"><span data-stu-id="baad9-130">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="baad9-131">Filtry są stosowane tylko w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="baad9-131">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="baad9-132">Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="baad9-132">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="baad9-133">Jedynym atrybutem dla tego elementu, `filter` ,, jest obiekt XPathFilter.</span><span class="sxs-lookup"><span data-stu-id="baad9-133">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="baad9-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="baad9-134">Parent Elements</span></span>  
  
|<span data-ttu-id="baad9-135">Element</span><span class="sxs-lookup"><span data-stu-id="baad9-135">Element</span></span>|<span data-ttu-id="baad9-136">Opis</span><span class="sxs-lookup"><span data-stu-id="baad9-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baad9-137">Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="baad9-137">diagnostics</span></span>|<span data-ttu-id="baad9-138">Definiuje ustawienia WCF na potrzeby inspekcji i kontroli środowiska uruchomieniowego dla administratora.</span><span class="sxs-lookup"><span data-stu-id="baad9-138">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baad9-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="baad9-139">Remarks</span></span>  
 <span data-ttu-id="baad9-140">Komunikaty są rejestrowane na trzech różnych poziomach w stosie: Service, transport i źle sformułowane.</span><span class="sxs-lookup"><span data-stu-id="baad9-140">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="baad9-141">Każdy poziom można aktywować osobno.</span><span class="sxs-lookup"><span data-stu-id="baad9-141">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="baad9-142">Filtry XPath można dodawać do rejestrowania określonych komunikatów na poziomie transportu i usług.</span><span class="sxs-lookup"><span data-stu-id="baad9-142">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="baad9-143">Jeśli żadne filtry nie są zdefiniowane, wszystkie komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="baad9-143">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="baad9-144">Filtry są stosowane tylko do nagłówków wiadomości.</span><span class="sxs-lookup"><span data-stu-id="baad9-144">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="baad9-145">Treść jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="baad9-145">The body is ignored.</span></span> <span data-ttu-id="baad9-146">Funkcja WCF ignoruje treść komunikatu w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="baad9-146">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="baad9-147">Jeśli chcesz filtrować w oparciu o zawartość treści, możesz utworzyć niestandardowy odbiornik z filtrem, który to robi.</span><span class="sxs-lookup"><span data-stu-id="baad9-147">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="baad9-148">Musisz utworzyć odbiornik śledzenia, aby aktywować śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="baad9-148">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="baad9-149">Odbiornik może być dowolnym odbiornikiem, który współpracuje z <xref:System.Diagnostics> architekturą śledzenia.</span><span class="sxs-lookup"><span data-stu-id="baad9-149">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="baad9-150">W poniższym przykładzie pokazano, jak utworzyć taki odbiornik.</span><span class="sxs-lookup"><span data-stu-id="baad9-150">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="baad9-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="baad9-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="baad9-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baad9-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="baad9-153">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="baad9-153">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
