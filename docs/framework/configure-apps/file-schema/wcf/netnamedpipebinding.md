---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: b8bdfeb8f042d892280226e0f7c08b6804eabca9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400190"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="bcd54-101">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="bcd54-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="bcd54-102">Definiuje powiązanie, które jest bezpieczne, niezawodne i zoptymalizowane pod kątem komunikacji między procesami na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bcd54-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="bcd54-103">Domyślnie generuje stos komunikacji środowiska uruchomieniowego za pomocą protokołu WS-ReliableMessaging w celu zapewnienia niezawodności, zabezpieczeń transportu na potrzeby przesyłania komunikatów i nazwanych potoków na potrzeby dostarczania wiadomości i kodowania komunikatów binarnych.</span><span class="sxs-lookup"><span data-stu-id="bcd54-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
<span data-ttu-id="bcd54-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bcd54-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bcd54-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bcd54-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bcd54-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bcd54-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bcd54-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="bcd54-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcd54-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcd54-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcd54-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bcd54-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bcd54-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bcd54-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcd54-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bcd54-111">Attributes</span></span>  
  
|<span data-ttu-id="bcd54-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bcd54-112">Attribute</span></span>|<span data-ttu-id="bcd54-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bcd54-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bcd54-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="bcd54-114">closeTimeout</span></span>|<span data-ttu-id="bcd54-115"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="bcd54-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bcd54-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcd54-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bcd54-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="bcd54-118">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bcd54-118">hostNameComparisonMode</span></span>|<span data-ttu-id="bcd54-119">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="bcd54-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="bcd54-120">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="bcd54-120">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="bcd54-121">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="bcd54-121">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="bcd54-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bcd54-122">maxBufferPoolSize</span></span>|<span data-ttu-id="bcd54-123">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="bcd54-124">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="bcd54-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="bcd54-125">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="bcd54-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="bcd54-126">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="bcd54-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="bcd54-127">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="bcd54-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="bcd54-128">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="bcd54-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="bcd54-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="bcd54-129">maxBufferSize</span></span>|<span data-ttu-id="bcd54-130">Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu używany do przechowywania komunikatów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bcd54-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="bcd54-131">Jeśli bufor jest pełny, nadmiarowe dane pozostają w podstawowym gnieździe do momentu ponownego uruchomienia buforu.</span><span class="sxs-lookup"><span data-stu-id="bcd54-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="bcd54-132">Ta wartość nie może być mniejsza `maxReceivedMessageSize` niż atrybut.</span><span class="sxs-lookup"><span data-stu-id="bcd54-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="bcd54-133">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="bcd54-133">The default is 65536.</span></span> <span data-ttu-id="bcd54-134">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="bcd54-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="bcd54-135">maxConnections</span></span>|<span data-ttu-id="bcd54-136">Liczba całkowita określająca maksymalną liczbę połączeń wychodzących i przychodzących, które usługa zostanie utworzona/zaakceptowana.</span><span class="sxs-lookup"><span data-stu-id="bcd54-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="bcd54-137">Połączenia przychodzące i wychodzące są liczone względem oddzielnego limitu określonego przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="bcd54-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="bcd54-138">Połączenia przychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="bcd54-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="bcd54-139">Połączenia wychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="bcd54-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="bcd54-140">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="bcd54-140">The default is 10.</span></span>|  
|<span data-ttu-id="bcd54-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bcd54-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="bcd54-142">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="bcd54-143">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bcd54-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="bcd54-144">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bcd54-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="bcd54-145">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="bcd54-145">The default is 65536.</span></span>|  
|<span data-ttu-id="bcd54-146">nazwa</span><span class="sxs-lookup"><span data-stu-id="bcd54-146">name</span></span>|<span data-ttu-id="bcd54-147">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bcd54-148">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bcd54-149">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="bcd54-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bcd54-150">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bcd54-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="bcd54-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="bcd54-151">openTimeout</span></span>|<span data-ttu-id="bcd54-152"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="bcd54-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bcd54-153">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcd54-154">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bcd54-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="bcd54-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="bcd54-155">receiveTimeout</span></span>|<span data-ttu-id="bcd54-156"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="bcd54-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bcd54-157">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcd54-158">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bcd54-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="bcd54-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="bcd54-159">sendTimeout</span></span>|<span data-ttu-id="bcd54-160"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bcd54-161">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcd54-162">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bcd54-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="bcd54-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="bcd54-163">transactionFlow</span></span>|<span data-ttu-id="bcd54-164">Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="bcd54-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="bcd54-165">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="bcd54-165">The default is `false`.</span></span>|  
|<span data-ttu-id="bcd54-166">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="bcd54-166">transactionProtocol</span></span>|<span data-ttu-id="bcd54-167">Określa protokół transakcji, który ma być używany z tym powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="bcd54-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="bcd54-168">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="bcd54-168">Valid values are</span></span><br /><br /> <span data-ttu-id="bcd54-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="bcd54-169">-   OleTransactions</span></span><br /><span data-ttu-id="bcd54-170">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="bcd54-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="bcd54-171">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="bcd54-171">The default is OleTransactions.</span></span> <span data-ttu-id="bcd54-172">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="bcd54-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="bcd54-173">transferMode</span></span>|<span data-ttu-id="bcd54-174"><xref:System.ServiceModel.TransferMode> Wartość określająca, czy komunikaty są buforowane, czy przesyłane strumieniowo, czy też żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="bcd54-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcd54-175">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bcd54-175">Child Elements</span></span>  
  
|<span data-ttu-id="bcd54-176">Element</span><span class="sxs-lookup"><span data-stu-id="bcd54-176">Element</span></span>|<span data-ttu-id="bcd54-177">Opis</span><span class="sxs-lookup"><span data-stu-id="bcd54-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcd54-178">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bcd54-178">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="bcd54-179">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="bcd54-180">Ten element jest typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="bcd54-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcd54-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="bcd54-182">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="bcd54-183">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="bcd54-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bcd54-184">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bcd54-184">Parent Elements</span></span>  
  
|<span data-ttu-id="bcd54-185">Element</span><span class="sxs-lookup"><span data-stu-id="bcd54-185">Element</span></span>|<span data-ttu-id="bcd54-186">Opis</span><span class="sxs-lookup"><span data-stu-id="bcd54-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcd54-187">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="bcd54-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="bcd54-188">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bcd54-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcd54-189">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bcd54-189">Remarks</span></span>  
 <span data-ttu-id="bcd54-190">`NetNamedPipeBinding` Generuje stos komunikacji w czasie wykonywania domyślnie, który używa zabezpieczeń transportu, potoków nazwanych do dostarczania komunikatów i kodowania komunikatów binarnych.</span><span class="sxs-lookup"><span data-stu-id="bcd54-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="bcd54-191">To powiązanie jest odpowiednim wyborem systemu Windows Communication Foundation (WCF) w przypadku komunikacji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bcd54-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="bcd54-192">Obsługuje ona również transakcje.</span><span class="sxs-lookup"><span data-stu-id="bcd54-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="bcd54-193">Konfiguracja domyślna dla programu `NetNamedPipeBinding` jest podobna do konfiguracji zapewnianej `NetTcpBinding`przez program, ale jest prostsze, ponieważ implementacja programu WCF jest przeznaczona tylko do użytku na komputerze i w związku z tym jest mniej narażonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="bcd54-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="bcd54-194">Najbardziej istotną różnicą jest to `securityMode` , że ustawienie `None` oferuje tylko `Transport` opcje i.</span><span class="sxs-lookup"><span data-stu-id="bcd54-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="bcd54-195">Obsługa zabezpieczeń protokołu SOAP nie jest uwzględnioną opcją.</span><span class="sxs-lookup"><span data-stu-id="bcd54-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="bcd54-196">Zachowanie zabezpieczeń można skonfigurować przy użyciu opcjonalnego `securityMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bcd54-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcd54-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="bcd54-197">Example</span></span>  
 <span data-ttu-id="bcd54-198">Poniższy przykład ilustruje powiązanie netNamedPipeBinding, które zapewnia komunikację między procesami na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bcd54-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="bcd54-199">Nazwane potoki nie działają między maszynami.</span><span class="sxs-lookup"><span data-stu-id="bcd54-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="bcd54-200">Powiązanie jest określone w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="bcd54-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="bcd54-201">Typ powiązania jest określony w `binding` atrybucie `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="bcd54-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="bcd54-202">Jeśli chcesz skonfigurować powiązanie netNamedPipeBinding i zmienić niektóre z jego ustawień, musisz zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="bcd54-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="bcd54-203">Punkt końcowy musi odwoływać się do konfiguracji powiązania za pomocą `bindingConfiguration` nazwy z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="bcd54-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="bcd54-204">W tym przykładzie Konfiguracja powiązania ma nazwę Binding1.</span><span class="sxs-lookup"><span data-stu-id="bcd54-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
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
  
## <a name="see-also"></a><span data-ttu-id="bcd54-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcd54-205">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="bcd54-206">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="bcd54-206">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="bcd54-207">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bcd54-207">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bcd54-208">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="bcd54-208">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bcd54-209">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="bcd54-209">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
