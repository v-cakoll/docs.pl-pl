---
title: '&lt;reliableSession&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8484fe902b356f7fae4e526bdaa5610bf7d7ac6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltreliablesessiongt"></a><span data-ttu-id="9a807-102">&lt;reliableSession&gt;</span><span class="sxs-lookup"><span data-stu-id="9a807-102">&lt;reliableSession&gt;</span></span>
<span data-ttu-id="9a807-103">Definiuje ustawienie dla WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="9a807-103">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="9a807-104">Gdy ten element jest dodawany do niestandardowego powiązania, wynikowy kanał obsługuje dokładnie — raz gwarancje dostarczenia.</span><span class="sxs-lookup"><span data-stu-id="9a807-104">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="9a807-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9a807-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9a807-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9a807-106">\<bindings></span></span>  
<span data-ttu-id="9a807-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9a807-107">\<customBinding></span></span>  
<span data-ttu-id="9a807-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9a807-108">\<binding></span></span>  
<span data-ttu-id="9a807-109">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="9a807-109">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a807-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a807-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a807-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9a807-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9a807-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9a807-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a807-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9a807-113">Attributes</span></span>  
  
|<span data-ttu-id="9a807-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9a807-114">Attribute</span></span>|<span data-ttu-id="9a807-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9a807-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a807-116">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="9a807-116">acknowledgementInterval</span></span>|<span data-ttu-id="9a807-117">A <xref:System.TimeSpan> zawiera maksymalny czas kanału będzie oczekiwał na wysłanie potwierdzenia dla wiadomości otrzymanych do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="9a807-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="9a807-118">Wartość domyślna to 00:00:0.2.</span><span class="sxs-lookup"><span data-stu-id="9a807-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="9a807-119">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="9a807-119">flowControlEnabled</span></span>|<span data-ttu-id="9a807-120">Wartość logiczna wskazująca, czy Zaawansowane sterowanie przepływem, implementacja specyficzna dla Microsoft kontroli przepływu dla obsługi wiadomości WS-Reliable, jest aktywowana.</span><span class="sxs-lookup"><span data-stu-id="9a807-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="9a807-121">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="9a807-121">The default is `true`.</span></span>|  
|<span data-ttu-id="9a807-122">Limit czasu nieaktywności</span><span class="sxs-lookup"><span data-stu-id="9a807-122">inactivityTimeout</span></span>|<span data-ttu-id="9a807-123">A <xref:System.TimeSpan> , który określa maksymalny czas, który będzie kanał zezwoli innemu uczestnikowi komunikacji nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału.</span><span class="sxs-lookup"><span data-stu-id="9a807-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="9a807-124">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9a807-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="9a807-125">Działań w kanale jest zdefiniowany jako odbieranie aplikacji lub infrastruktury komunikatów.</span><span class="sxs-lookup"><span data-stu-id="9a807-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="9a807-126">Ta właściwość kontroluje maksymalną ilość czasu podtrzymywania nieaktywnych sesji.</span><span class="sxs-lookup"><span data-stu-id="9a807-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="9a807-127">Jeśli dłużej zakończy się pomyślnie bez żadnych działań, sesji został przerwany przez infrastrukturę i usterek kanału.</span><span class="sxs-lookup"><span data-stu-id="9a807-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="9a807-128">**Uwaga:** nie jest niezbędna dla aplikacji, aby okresowo wysyłania komunikatów podtrzymywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="9a807-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="9a807-129">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="9a807-129">maxPendingChannels</span></span>|<span data-ttu-id="9a807-130">Liczba całkowita określająca maksymalną liczbę kanałów oczekujących na akceptację odbiornika.</span><span class="sxs-lookup"><span data-stu-id="9a807-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="9a807-131">Ta wartość może zawierać od 1 do 16384 włącznie.</span><span class="sxs-lookup"><span data-stu-id="9a807-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="9a807-132">Wartość domyślna to 4.</span><span class="sxs-lookup"><span data-stu-id="9a807-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="9a807-133">Kanały oczekują na kiedy są oczekuje na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="9a807-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="9a807-134">Po osiągnięciu tego limitu tworzone są Brak kanałów.</span><span class="sxs-lookup"><span data-stu-id="9a807-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="9a807-135">Zamiast wprowadzeniem oczekujących tryb dopóki liczba osiąga w dół (akceptując oczekujących kanałów).</span><span class="sxs-lookup"><span data-stu-id="9a807-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="9a807-136">Jest to limit dla fabryki.</span><span class="sxs-lookup"><span data-stu-id="9a807-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="9a807-137">Po osiągnięciu progu i aplikacji zdalnej próbuje utworzyć nowe niezawodnej sesji, żądanie zostanie odrzucone i otwórz operację, która zostanie wyświetlony monit tej usterki.</span><span class="sxs-lookup"><span data-stu-id="9a807-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="9a807-138">To ograniczenie nie dotyczy liczby oczekujących kanałów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="9a807-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="9a807-139">Wartość MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="9a807-139">maxRetryCount</span></span>|<span data-ttu-id="9a807-140">Liczba całkowita określająca maksymalną liczbę razy niezawodny kanał prób ponownego przesłania wiadomości nie otrzymano potwierdzenia, poprzez wywoływanie metody Send kanału źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9a807-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="9a807-141">Ta wartość powinna być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="9a807-141">This value should be greater than zero.</span></span> <span data-ttu-id="9a807-142">Wartość domyślna to 8.</span><span class="sxs-lookup"><span data-stu-id="9a807-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="9a807-143">Ta wartość powinna być liczbą całkowitą większą niż zero.</span><span class="sxs-lookup"><span data-stu-id="9a807-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="9a807-144">Jeśli potwierdzenie nie zostanie odebrana po ostatnim retransmisji, błędów kanału.</span><span class="sxs-lookup"><span data-stu-id="9a807-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="9a807-145">Komunikat jest uznawany za do przeniesienia, jeśli potwierdzenia dostarczenia po stronie odbiorcy przez odbiorcę.</span><span class="sxs-lookup"><span data-stu-id="9a807-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="9a807-146">Jeśli nie otrzymano potwierdzenia w ciągu pewnego czasu dla wiadomości, które zostały przesłane, infrastruktury automatycznie ponownie wysyła wiadomość.</span><span class="sxs-lookup"><span data-stu-id="9a807-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="9a807-147">Infrastruktura próbuje ponownie wysłać wiadomość co najwyżej liczbę powtórzeń przez tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="9a807-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="9a807-148">Jeśli potwierdzenie nie zostanie odebrana po ostatnim retransmisji, błędów kanału.</span><span class="sxs-lookup"><span data-stu-id="9a807-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="9a807-149">Infrastruktura używa algorytm wykładnicze wycofania do określenia, kiedy ponownego przesłania, oparte na obliczona średnia czasu rundy.</span><span class="sxs-lookup"><span data-stu-id="9a807-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="9a807-150">Czas początkowo rozpoczyna się od 1 sekundy przed retransmisji i podwajając opóźnienie co nieudanej próby podania, co prowadzi do przekazywania między przy pierwszej próbie transmisji i ostatnią próbę retransmisji około 8,5 minut.</span><span class="sxs-lookup"><span data-stu-id="9a807-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="9a807-151">Podczas pierwszej próby retransmisji jest dostosowane według czasu Rundy obliczeniowej i odcinek wynikowy czas trwania tymi próbami różni odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9a807-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="9a807-152">Dzięki temu czas retransmisji dynamicznie dostosowywana w zmiennych warunkach sieciowych.</span><span class="sxs-lookup"><span data-stu-id="9a807-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="9a807-153">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="9a807-153">maxTransferWindowSize</span></span>|<span data-ttu-id="9a807-154">Liczba całkowita określająca maksymalny rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="9a807-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="9a807-155">Prawidłowe są wartości z zakresu od 1 do 4096 włącznie.</span><span class="sxs-lookup"><span data-stu-id="9a807-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="9a807-156">Na komputerze klienckim ten atrybut określa maksymalny rozmiar bufora używanego przez kanał niezawodny do przechowywania komunikatów potwierdzonych nie została jeszcze przez odbiornik.</span><span class="sxs-lookup"><span data-stu-id="9a807-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="9a807-157">Jednostki przydziału jest komunikat.</span><span class="sxs-lookup"><span data-stu-id="9a807-157">The unit of the quota is a message.</span></span> <span data-ttu-id="9a807-158">Jeśli bufor jest pełna, dodatkowe operacje WYSYŁANIA są zablokowane.</span><span class="sxs-lookup"><span data-stu-id="9a807-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="9a807-159">Odbiornika ten atrybut określa maksymalny rozmiar bufora używanego przez kanał do przechowywania wiadomości przychodzących, które nie zostały jeszcze wysłane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a807-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="9a807-160">Jeśli bufor jest pełna, dalsze komunikaty dyskretnie są usuwane przez odbiornik i wymagają retransmisji przez klienta.</span><span class="sxs-lookup"><span data-stu-id="9a807-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="9a807-161">uporządkowany</span><span class="sxs-lookup"><span data-stu-id="9a807-161">ordered</span></span>|<span data-ttu-id="9a807-162">Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania.</span><span class="sxs-lookup"><span data-stu-id="9a807-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="9a807-163">Jeśli to ustawienie jest `false`, można odebraniu komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="9a807-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="9a807-164">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="9a807-164">The default is `true`.</span></span>|  
|<span data-ttu-id="9a807-165">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="9a807-165">reliableMessagingVersion</span></span>|<span data-ttu-id="9a807-166">Prawidłowa wartość z <xref:System.ServiceModel.ReliableMessagingVersion> określająca wersję WS-ReliableMessaging do użycia.</span><span class="sxs-lookup"><span data-stu-id="9a807-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a807-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9a807-167">Child Elements</span></span>  
 <span data-ttu-id="9a807-168">Brak</span><span class="sxs-lookup"><span data-stu-id="9a807-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a807-169">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9a807-169">Parent Elements</span></span>  
  
|<span data-ttu-id="9a807-170">Element</span><span class="sxs-lookup"><span data-stu-id="9a807-170">Element</span></span>|<span data-ttu-id="9a807-171">Opis</span><span class="sxs-lookup"><span data-stu-id="9a807-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a807-172">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9a807-172">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9a807-173">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9a807-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a807-174">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a807-174">Remarks</span></span>  
 <span data-ttu-id="9a807-175">Niezawodne sesje zapewniają funkcje dla niezawodna obsługa komunikatów i sesji.</span><span class="sxs-lookup"><span data-stu-id="9a807-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="9a807-176">Niezawodna obsługa komunikatów ponowi próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, takich jak otrzymanie wiadomości, można określić w kolejności.</span><span class="sxs-lookup"><span data-stu-id="9a807-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="9a807-177">Sesje przechowywania stanu dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="9a807-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="9a807-178">Ten element zawiera również opcjonalnie dostarczanie komunikatów uporządkowanej.</span><span class="sxs-lookup"><span data-stu-id="9a807-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="9a807-179">Ta sesja zaimplementowanym mogą przechodzić pośredników SOAP i transportu.</span><span class="sxs-lookup"><span data-stu-id="9a807-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="9a807-180">Każdy element powiązania reprezentuje krok przetwarzania przy wysyłaniu lub odbieraniu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9a807-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="9a807-181">W czasie wykonywania elementy powiązania utworzyć fabryk kanałów i odbiorników, które są niezbędne do utworzenia wychodzące i przychodzące stosy kanału wymagane do wysyłania i odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9a807-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="9a807-182">`reliableSession` Zapewnia opcjonalne warstwę stosu, który można utworzyć niezawodnej sesji między punktami końcowymi i skonfigurować działanie tej sesji.</span><span class="sxs-lookup"><span data-stu-id="9a807-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="9a807-183">Aby uzyskać więcej informacji, zobacz [sesji niezawodnej](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="9a807-183">For more information, see [Reliable Sessions](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a807-184">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a807-184">Example</span></span>  
 <span data-ttu-id="9a807-185">W poniższym przykładzie pokazano sposób konfigurowania niestandardowego powiązania z różnymi transportu i wiadomości kodowania elementów, szczególnie Włączanie niezawodnej sesji, która przechowuje stan klienta i określa gwarancje dostarczenia w kolejności.</span><span class="sxs-lookup"><span data-stu-id="9a807-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="9a807-186">Ta funkcja jest skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="9a807-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="9a807-187">Pokaż przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="9a807-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a807-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a807-188">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [<span data-ttu-id="9a807-189">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="9a807-189">Reliable Sessions</span></span>](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [<span data-ttu-id="9a807-190">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9a807-190">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9a807-191">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9a807-191">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9a807-192">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9a807-192">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9a807-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9a807-193">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
