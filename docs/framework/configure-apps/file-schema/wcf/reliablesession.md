---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 95f6646041dc2dd7bae7691a0a9f748c844f50b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738747"
---
# \<reliableSession>
<span data-ttu-id="dccd9-101">Definiuje ustawienie dla obsługi komunikatów w usłudze WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="dccd9-101">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="dccd9-102">Gdy ten element zostanie dodany do niestandardowego powiązania, otrzymany kanał może obsługiwać tylko jednokrotne gwarancje dostarczania.</span><span class="sxs-lookup"><span data-stu-id="dccd9-102">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**  
  
## <a name="syntax"></a><span data-ttu-id="dccd9-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="dccd9-103">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dccd9-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dccd9-104">Attributes and Elements</span></span>  
 <span data-ttu-id="dccd9-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dccd9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dccd9-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dccd9-106">Attributes</span></span>  
  
|<span data-ttu-id="dccd9-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dccd9-107">Attribute</span></span>|<span data-ttu-id="dccd9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="dccd9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dccd9-109">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="dccd9-109">acknowledgementInterval</span></span>|<span data-ttu-id="dccd9-110">A <xref:System.TimeSpan> , który zawiera maksymalny czas oczekiwania kanału na wysłanie potwierdzenia dla wiadomości otrzymanych do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="dccd9-110">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="dccd9-111">Wartość domyślna to 00:00:0,2.</span><span class="sxs-lookup"><span data-stu-id="dccd9-111">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="dccd9-112">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="dccd9-112">flowControlEnabled</span></span>|<span data-ttu-id="dccd9-113">Wartość logiczna wskazująca, czy jest uaktywniana Zaawansowana kontrola przepływów — implementacja sterowania przepływem dla usługi WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="dccd9-113">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="dccd9-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="dccd9-114">The default is `true`.</span></span>|  
|<span data-ttu-id="dccd9-115">inactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="dccd9-115">inactivityTimeout</span></span>|<span data-ttu-id="dccd9-116"><xref:System.TimeSpan>Określa maksymalny czas, przez który kanał będzie zezwalał innej stronie komunikacyjnej, aby nie wysyłał żadnych komunikatów przed awarią kanału.</span><span class="sxs-lookup"><span data-stu-id="dccd9-116">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="dccd9-117">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="dccd9-117">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="dccd9-118">Działanie w kanale jest zdefiniowane jako otrzymywanie komunikatów aplikacji lub infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="dccd9-118">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="dccd9-119">Ta właściwość określa maksymalny czas utrzymywania aktywnej sesji.</span><span class="sxs-lookup"><span data-stu-id="dccd9-119">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="dccd9-120">Jeśli dłuższy czas upłynie bez aktywności, sesja zostanie przerwana przez infrastrukturę i błędy kanałów.</span><span class="sxs-lookup"><span data-stu-id="dccd9-120">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="dccd9-121">**Uwaga:**  Nie jest konieczne, aby aplikacja okresowo wysyłał komunikaty w celu utrzymania aktywności połączenia.</span><span class="sxs-lookup"><span data-stu-id="dccd9-121">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="dccd9-122">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="dccd9-122">maxPendingChannels</span></span>|<span data-ttu-id="dccd9-123">Liczba całkowita określająca maksymalną liczbę kanałów, które mogą oczekiwać na zaakceptowanie odbiornika.</span><span class="sxs-lookup"><span data-stu-id="dccd9-123">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="dccd9-124">Ta wartość powinna należeć do zakresu od 1 do 16384 włącznie.</span><span class="sxs-lookup"><span data-stu-id="dccd9-124">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="dccd9-125">Wartość domyślna to 4.</span><span class="sxs-lookup"><span data-stu-id="dccd9-125">The default is 4.</span></span><br /><br /> <span data-ttu-id="dccd9-126">Kanały oczekują na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="dccd9-126">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="dccd9-127">Po osiągnięciu tego limitu nie są tworzone żadne kanały.</span><span class="sxs-lookup"><span data-stu-id="dccd9-127">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="dccd9-128">Zamiast tego są one umieszczane w trybie oczekiwania, dopóki ta liczba nie przejdzie w dół (akceptując kanały oczekujące).</span><span class="sxs-lookup"><span data-stu-id="dccd9-128">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="dccd9-129">Jest to limit dla poszczególnych fabryk.</span><span class="sxs-lookup"><span data-stu-id="dccd9-129">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="dccd9-130">Po osiągnięciu progu, gdy aplikacja zdalna podejmie próbę nawiązania nowej niezawodnej sesji, żądanie zostanie odrzucone i zostanie otwarta operacja, która monituje o te błędy.</span><span class="sxs-lookup"><span data-stu-id="dccd9-130">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="dccd9-131">Ten limit nie ma zastosowania do liczby oczekujących kanałów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="dccd9-131">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="dccd9-132">Wartość MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="dccd9-132">maxRetryCount</span></span>|<span data-ttu-id="dccd9-133">Liczba całkowita określająca maksymalną liczbę prób ponownego przesłania przez niezawodny kanał komunikatu, dla którego nie otrzymano potwierdzenia, przez wywołanie metody send w kanale źródłowym.</span><span class="sxs-lookup"><span data-stu-id="dccd9-133">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="dccd9-134">Ta wartość powinna być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="dccd9-134">This value should be greater than zero.</span></span> <span data-ttu-id="dccd9-135">Wartość domyślna to 8.</span><span class="sxs-lookup"><span data-stu-id="dccd9-135">The default is 8.</span></span><br /><br /> <span data-ttu-id="dccd9-136">Ta wartość powinna być liczbą całkowitą większą od zera.</span><span class="sxs-lookup"><span data-stu-id="dccd9-136">This value should be an integer greater than zero.</span></span> <span data-ttu-id="dccd9-137">Jeśli potwierdzenie nie zostanie odebrane po ostatniej ponownej transmisji, wystąpią błędy kanałów.</span><span class="sxs-lookup"><span data-stu-id="dccd9-137">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="dccd9-138">Wiadomość jest uznawana za przetransferowaną, jeśli jej dostarczenie w odbiorcy zostało potwierdzone przez adresata.</span><span class="sxs-lookup"><span data-stu-id="dccd9-138">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="dccd9-139">Jeśli potwierdzenie nie zostało odebrane w określonym czasie przez komunikat, który został przesłany, infrastruktura automatycznie ponownie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="dccd9-139">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="dccd9-140">Infrastruktura próbuje ponownie wysłać komunikat przez maksymalnie liczbę razy określony przez tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="dccd9-140">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="dccd9-141">Jeśli potwierdzenie nie zostanie odebrane po ostatniej ponownej transmisji, wystąpią błędy kanałów.</span><span class="sxs-lookup"><span data-stu-id="dccd9-141">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="dccd9-142">Infrastruktura używa algorytmu wycofywania wykładniczego, aby określić, kiedy należy ponownie przesłać, w oparciu o obliczony średni czas błądzenia.</span><span class="sxs-lookup"><span data-stu-id="dccd9-142">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="dccd9-143">Czas początkowo rozpoczyna się o 1 sekundę przed ponownym przesłaniem i Podwajanie opóźnienia przy każdej próbie, co powoduje około 8,5 minut przekazywania między pierwszą próbą transmisji a ostatnią ponowną transmisją.</span><span class="sxs-lookup"><span data-stu-id="dccd9-143">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="dccd9-144">Czas pierwszej próby ponownej transmisji jest dostosowywany zgodnie z obliczonym czasem błądzenia i wynikowym rozciągnięciem czasu, który podejmuje te próby.</span><span class="sxs-lookup"><span data-stu-id="dccd9-144">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="dccd9-145">Umożliwia to czas ponownej transmisji, który dynamicznie dostosowuje się do różnych warunków sieciowych.</span><span class="sxs-lookup"><span data-stu-id="dccd9-145">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="dccd9-146">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="dccd9-146">maxTransferWindowSize</span></span>|<span data-ttu-id="dccd9-147">Liczba całkowita określająca maksymalny rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="dccd9-147">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="dccd9-148">Prawidłowe wartości to od 1 do 4096 włącznie.</span><span class="sxs-lookup"><span data-stu-id="dccd9-148">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="dccd9-149">Ten atrybut określa maksymalny rozmiar buforu używany przez niezawodny kanał do przechowywania komunikatów, które nie zostały jeszcze potwierdzone przez odbiornik.</span><span class="sxs-lookup"><span data-stu-id="dccd9-149">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="dccd9-150">Jednostka przydziału jest komunikatem.</span><span class="sxs-lookup"><span data-stu-id="dccd9-150">The unit of the quota is a message.</span></span> <span data-ttu-id="dccd9-151">Jeśli bufor jest pełny, dalsze operacje wysyłania są blokowane.</span><span class="sxs-lookup"><span data-stu-id="dccd9-151">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="dccd9-152">W odniesieniu do odbiorcy ten atrybut definiuje maksymalny rozmiar buforu używany przez kanał do przechowywania przychodzących komunikatów, które nie zostały jeszcze wysłane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dccd9-152">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="dccd9-153">Jeśli bufor jest pełny, dalsze komunikaty są dyskretnie usuwane przez odbiornik i wymagają ponownej transmisji przez klienta.</span><span class="sxs-lookup"><span data-stu-id="dccd9-153">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="dccd9-154">uporządkowany</span><span class="sxs-lookup"><span data-stu-id="dccd9-154">ordered</span></span>|<span data-ttu-id="dccd9-155">Wartość logiczna określająca, czy komunikaty są gwarantowane w kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="dccd9-155">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="dccd9-156">Jeśli to ustawienie ma wartość `false` , komunikaty mogą dotrzeć poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="dccd9-156">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="dccd9-157">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="dccd9-157">The default is `true`.</span></span>|  
|<span data-ttu-id="dccd9-158">ReliableMessagingVersion określająca</span><span class="sxs-lookup"><span data-stu-id="dccd9-158">reliableMessagingVersion</span></span>|<span data-ttu-id="dccd9-159">Prawidłowa wartość <xref:System.ServiceModel.ReliableMessagingVersion> określająca, czy wersja protokołu WS-ReliableMessaging ma być używana.</span><span class="sxs-lookup"><span data-stu-id="dccd9-159">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dccd9-160">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dccd9-160">Child Elements</span></span>  
 <span data-ttu-id="dccd9-161">Brak</span><span class="sxs-lookup"><span data-stu-id="dccd9-161">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dccd9-162">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dccd9-162">Parent Elements</span></span>  
  
|<span data-ttu-id="dccd9-163">Element</span><span class="sxs-lookup"><span data-stu-id="dccd9-163">Element</span></span>|<span data-ttu-id="dccd9-164">Opis</span><span class="sxs-lookup"><span data-stu-id="dccd9-164">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="dccd9-165">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="dccd9-165">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dccd9-166">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dccd9-166">Remarks</span></span>  
 <span data-ttu-id="dccd9-167">Niezawodne sesje zapewniają funkcje niezawodnej obsługi komunikatów i sesji.</span><span class="sxs-lookup"><span data-stu-id="dccd9-167">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="dccd9-168">Niezawodna komunikacja w celu komunikacji przy niepowodzeń i pozwala na określenie gwarancji dostarczania, takich jak wysyłanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="dccd9-168">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="dccd9-169">Sesje utrzymują stan dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="dccd9-169">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="dccd9-170">Ten element również opcjonalnie udostępnia uporządkowane dostarczanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="dccd9-170">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="dccd9-171">Ta zaimplementowana sesja może przekroczyć pośredniki SOAP i transportu.</span><span class="sxs-lookup"><span data-stu-id="dccd9-171">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="dccd9-172">Każdy element powiązania reprezentuje etap przetwarzania podczas wysyłania lub otrzymywania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dccd9-172">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="dccd9-173">W czasie wykonywania elementy powiązania tworzą fabryki kanałów i odbiorniki, które są niezbędne do tworzenia stosów kanałów wychodzących i przychodzących wymaganych do wysyłania i odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dccd9-173">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="dccd9-174">`reliableSession`Zapewnia opcjonalną warstwę w stosie, która może nawiązywać niezawodne sesje między punktami końcowymi i skonfigurować zachowanie tej sesji.</span><span class="sxs-lookup"><span data-stu-id="dccd9-174">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="dccd9-175">Aby uzyskać więcej informacji, zobacz [niezawodne sesje](../../../wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="dccd9-175">For more information, see [Reliable Sessions](../../../wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dccd9-176">Przykład</span><span class="sxs-lookup"><span data-stu-id="dccd9-176">Example</span></span>  
 <span data-ttu-id="dccd9-177">Poniższy przykład ilustruje sposób konfigurowania powiązania niestandardowego z różnymi elementami transportu i transportem komunikatów, szczególnie w przypadku włączania niezawodnych sesji, które utrzymują stan klienta i określa gwarancje dostarczania w kolejności.</span><span class="sxs-lookup"><span data-stu-id="dccd9-177">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="dccd9-178">Ta funkcja jest konfigurowana w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="dccd9-178">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="dccd9-179">W przykładzie przedstawiono konfigurację usługi.</span><span class="sxs-lookup"><span data-stu-id="dccd9-179">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="dccd9-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dccd9-180">See also</span></span>

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="dccd9-181">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="dccd9-181">Reliable Sessions</span></span>](../../../wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="dccd9-182">Powiązania</span><span class="sxs-lookup"><span data-stu-id="dccd9-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dccd9-183">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="dccd9-183">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="dccd9-184">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="dccd9-184">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
