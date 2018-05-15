---
title: '&lt;messageLogging&gt;'
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: e137070b71cf8a481eef3ea16260c135e29b4932
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagelogginggt"></a><span data-ttu-id="76be8-102">&lt;messageLogging&gt;</span><span class="sxs-lookup"><span data-stu-id="76be8-102">&lt;messageLogging&gt;</span></span>
<span data-ttu-id="76be8-103">Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="76be8-103">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="76be8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="76be8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="76be8-105">\<diagnostycznych ></span><span class="sxs-lookup"><span data-stu-id="76be8-105">\<diagnostic></span></span>  
<span data-ttu-id="76be8-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="76be8-106">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76be8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="76be8-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
                            <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76be8-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="76be8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="76be8-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="76be8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76be8-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="76be8-110">Attributes</span></span>  
  
|<span data-ttu-id="76be8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="76be8-111">Attribute</span></span>|<span data-ttu-id="76be8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="76be8-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="76be8-113">Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="76be8-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="76be8-114">Wartość domyślna to `false`, co oznacza, że tylko nagłówek komunikatu jest rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="76be8-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="76be8-115">To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatów (usługi, transport i źle sformułowane).</span><span class="sxs-lookup"><span data-stu-id="76be8-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="76be8-116">Wartość logiczna określająca, czy wadliwe komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="76be8-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="76be8-117">Wadliwe komunikaty nie są wliczane do `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="76be8-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="76be8-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="76be8-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="76be8-119">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowania - i transformacjami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="76be8-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="76be8-120">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="76be8-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="76be8-121">Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be8-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="76be8-122">Wszystkie filtry w pliku konfiguracyjnym są stosowane, a tylko komunikaty zgodne z filtrami są śledzone.</span><span class="sxs-lookup"><span data-stu-id="76be8-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="76be8-123">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="76be8-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="76be8-124">Dodatnia liczba całkowita, która określa maksymalną liczbę komunikatów do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="76be8-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="76be8-125">Wartość domyślna to 1000.</span><span class="sxs-lookup"><span data-stu-id="76be8-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="76be8-126">Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach komunikatu do dziennika.</span><span class="sxs-lookup"><span data-stu-id="76be8-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="76be8-127">Wiadomości przekracza limit nie będą rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="76be8-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="76be8-128">To ustawienie ma wpływ na wszystkie poziomy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="76be8-128">This setting affects all trace levels.</span></span> <span data-ttu-id="76be8-129">Wartość domyślna to 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="76be8-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76be8-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="76be8-130">Child Elements</span></span>  
  
|<span data-ttu-id="76be8-131">Element</span><span class="sxs-lookup"><span data-stu-id="76be8-131">Element</span></span>|<span data-ttu-id="76be8-132">Opis</span><span class="sxs-lookup"><span data-stu-id="76be8-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76be8-133">filtry</span><span class="sxs-lookup"><span data-stu-id="76be8-133">filters</span></span>|<span data-ttu-id="76be8-134">`filters` Element przetrzymuje kolekcję filtrów XPath.</span><span class="sxs-lookup"><span data-stu-id="76be8-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="76be8-135">Po włączeniu rejestrowania komunikatów transportu (`logMessagesAtTransportLevel` jest `true`), będą rejestrowane tylko komunikatów spełniających kryteria filtrów.</span><span class="sxs-lookup"><span data-stu-id="76be8-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="76be8-136">Filtry są stosowane tylko w przypadku warstwy transportu.</span><span class="sxs-lookup"><span data-stu-id="76be8-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="76be8-137">Usługa rejestrowania komunikatów poziomu i źle sformułowane nie dotyczy filtrów.</span><span class="sxs-lookup"><span data-stu-id="76be8-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="76be8-138">Atrybut tylko dla tego elementu `filter`, jest obiekt XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="76be8-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="76be8-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="76be8-139">Parent Elements</span></span>  
  
|<span data-ttu-id="76be8-140">Element</span><span class="sxs-lookup"><span data-stu-id="76be8-140">Element</span></span>|<span data-ttu-id="76be8-141">Opis</span><span class="sxs-lookup"><span data-stu-id="76be8-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76be8-142">diagnostyka</span><span class="sxs-lookup"><span data-stu-id="76be8-142">diagnostics</span></span>|<span data-ttu-id="76be8-143">Definiuje ustawienia WCF dla środowiska uruchomieniowego inspekcji i kontroli administratora.</span><span class="sxs-lookup"><span data-stu-id="76be8-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76be8-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76be8-144">Remarks</span></span>  
 <span data-ttu-id="76be8-145">Komunikaty są rejestrowane w trzech różnych poziomów w stosie: usługi, transport i jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="76be8-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="76be8-146">Każdy poziom można aktywować oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="76be8-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="76be8-147">Filtrach XPath można dodać do logowania określonego wiadomości na poziomie transportu i usługi.</span><span class="sxs-lookup"><span data-stu-id="76be8-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="76be8-148">Jeśli filtry nie są zdefiniowane, wszystkie komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="76be8-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="76be8-149">Filtry są stosowane tylko do nagłówków wiadomości.</span><span class="sxs-lookup"><span data-stu-id="76be8-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="76be8-150">Treść jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="76be8-150">The body is ignored.</span></span> <span data-ttu-id="76be8-151">Usługi WCF ignoruje treść wiadomości, aby zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="76be8-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="76be8-152">Jeśli chcesz filtrować na podstawie zawartości treści, można utworzyć niestandardowe odbiornika z filtrem to.</span><span class="sxs-lookup"><span data-stu-id="76be8-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="76be8-153">Musisz utworzyć odbiornik śledzenia, aby uaktywnić śledzenie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="76be8-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="76be8-154">Odbiornik sam może być żadnych odbiornika, który działa z <xref:System.Diagnostics> architektura śledzenia.</span><span class="sxs-lookup"><span data-stu-id="76be8-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="76be8-155">W poniższym przykładzie pokazano, jak utworzyć takie odbiornika.</span><span class="sxs-lookup"><span data-stu-id="76be8-155">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
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
  
## <a name="example"></a><span data-ttu-id="76be8-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="76be8-156">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76be8-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76be8-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [<span data-ttu-id="76be8-158">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="76be8-158">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
