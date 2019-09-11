---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855124"
---
# <a name="messagelogging"></a><span data-ttu-id="9e628-101">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="9e628-101">\<messageLogging></span></span>
<span data-ttu-id="9e628-102">Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9e628-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
<span data-ttu-id="9e628-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9e628-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9e628-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9e628-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9e628-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> diagnostyki**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="9e628-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="9e628-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<messageLogging >**</span><span class="sxs-lookup"><span data-stu-id="9e628-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e628-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e628-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e628-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9e628-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9e628-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9e628-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e628-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9e628-110">Attributes</span></span>  
  
|<span data-ttu-id="9e628-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9e628-111">Attribute</span></span>|<span data-ttu-id="9e628-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9e628-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="9e628-113">Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowany.</span><span class="sxs-lookup"><span data-stu-id="9e628-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="9e628-114">Wartość domyślna to `false`, co oznacza, że rejestrowany jest tylko nagłówek komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9e628-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="9e628-115">To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatów (usługa, transport i nieprawidłowo sformułowane).</span><span class="sxs-lookup"><span data-stu-id="9e628-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="9e628-116">Wartość logiczna określająca, czy źle sformułowane komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="9e628-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="9e628-117">Źle sformułowane wiadomości nie są wliczane do `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="9e628-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="9e628-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="9e628-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="9e628-119">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowaniem i transformami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="9e628-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="9e628-120">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="9e628-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="9e628-121">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="9e628-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="9e628-122">Wszystkie filtry określone w pliku konfiguracyjnym są stosowane i śledzone są tylko komunikaty zgodne z filtrami.</span><span class="sxs-lookup"><span data-stu-id="9e628-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="9e628-123">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="9e628-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="9e628-124">Dodatnia liczba całkowita, która określa maksymalną liczbę komunikatów do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="9e628-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="9e628-125">Wartość domyślna to 1000.</span><span class="sxs-lookup"><span data-stu-id="9e628-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="9e628-126">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu do zarejestrowania w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9e628-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="9e628-127">Komunikaty przekraczające limit nie będą rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="9e628-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="9e628-128">To ustawienie ma wpływ na wszystkie poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9e628-128">This setting affects all trace levels.</span></span> <span data-ttu-id="9e628-129">Wartość domyślna to 262 144 (0x4000).</span><span class="sxs-lookup"><span data-stu-id="9e628-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e628-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9e628-130">Child Elements</span></span>  
  
|<span data-ttu-id="9e628-131">Element</span><span class="sxs-lookup"><span data-stu-id="9e628-131">Element</span></span>|<span data-ttu-id="9e628-132">Opis</span><span class="sxs-lookup"><span data-stu-id="9e628-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e628-133">filtry</span><span class="sxs-lookup"><span data-stu-id="9e628-133">filters</span></span>|<span data-ttu-id="9e628-134">`filters` Element przechowuje kolekcję filtrów XPath.</span><span class="sxs-lookup"><span data-stu-id="9e628-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="9e628-135">Gdy rejestrowanie komunikatów transportu jest włączone (`logMessagesAtTransportLevel` is `true`), rejestrowane będą tylko komunikaty pasujące do filtrów.</span><span class="sxs-lookup"><span data-stu-id="9e628-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="9e628-136">Filtry są stosowane tylko w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="9e628-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="9e628-137">Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="9e628-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="9e628-138">Jedynym atrybutem dla tego elementu `filter`,,, jest obiekt XPathFilter.</span><span class="sxs-lookup"><span data-stu-id="9e628-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e628-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9e628-139">Parent Elements</span></span>  
  
|<span data-ttu-id="9e628-140">Element</span><span class="sxs-lookup"><span data-stu-id="9e628-140">Element</span></span>|<span data-ttu-id="9e628-141">Opis</span><span class="sxs-lookup"><span data-stu-id="9e628-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e628-142">diagnostyka</span><span class="sxs-lookup"><span data-stu-id="9e628-142">diagnostics</span></span>|<span data-ttu-id="9e628-143">Definiuje ustawienia WCF na potrzeby inspekcji i kontroli środowiska uruchomieniowego dla administratora.</span><span class="sxs-lookup"><span data-stu-id="9e628-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e628-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e628-144">Remarks</span></span>  
 <span data-ttu-id="9e628-145">Komunikaty są rejestrowane na trzech różnych poziomach w stosie: Service, transport i źle sformułowane.</span><span class="sxs-lookup"><span data-stu-id="9e628-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="9e628-146">Każdy poziom można aktywować osobno.</span><span class="sxs-lookup"><span data-stu-id="9e628-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="9e628-147">Filtry XPath można dodawać do rejestrowania określonych komunikatów na poziomie transportu i usług.</span><span class="sxs-lookup"><span data-stu-id="9e628-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="9e628-148">Jeśli żadne filtry nie są zdefiniowane, wszystkie komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="9e628-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="9e628-149">Filtry są stosowane tylko do nagłówków wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9e628-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="9e628-150">Treść jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="9e628-150">The body is ignored.</span></span> <span data-ttu-id="9e628-151">Funkcja WCF ignoruje treść komunikatu w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="9e628-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="9e628-152">Jeśli chcesz filtrować w oparciu o zawartość treści, możesz utworzyć niestandardowy odbiornik z filtrem, który to robi.</span><span class="sxs-lookup"><span data-stu-id="9e628-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="9e628-153">Musisz utworzyć odbiornik śledzenia, aby aktywować śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="9e628-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="9e628-154">Odbiornik może być dowolnym odbiornikiem, który współpracuje z <xref:System.Diagnostics> architekturą śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9e628-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="9e628-155">W poniższym przykładzie pokazano, jak utworzyć taki odbiornik.</span><span class="sxs-lookup"><span data-stu-id="9e628-155">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="9e628-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e628-156">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e628-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e628-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="9e628-158">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="9e628-158">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
