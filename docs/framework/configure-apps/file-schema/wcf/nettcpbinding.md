---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: 7d847ffd4c1e3d924b9c45497c1b2ee172887e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933011"
---
# <a name="nettcpbinding"></a><span data-ttu-id="4f123-101">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4f123-101">\<netTcpBinding></span></span>

<span data-ttu-id="4f123-102">Określa bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="4f123-102">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="4f123-103">Domyślnie generuje stos komunikacji środowiska uruchomieniowego z zabezpieczeniami systemu Windows w celu zabezpieczenia i uwierzytelniania komunikatów, protokołu TCP na potrzeby dostarczania komunikatów i kodowania komunikatów binarnych.</span><span class="sxs-lookup"><span data-stu-id="4f123-103">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="4f123-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4f123-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f123-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="4f123-105">\<bindings></span></span>  
<span data-ttu-id="4f123-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4f123-106">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f123-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f123-107">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f123-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4f123-108">Attributes and elements</span></span>

<span data-ttu-id="4f123-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4f123-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f123-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4f123-110">Attributes</span></span>  
  
|<span data-ttu-id="4f123-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4f123-111">Attribute</span></span>|<span data-ttu-id="4f123-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4f123-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4f123-113"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="4f123-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4f123-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4f123-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4f123-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4f123-115">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="4f123-116">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="4f123-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4f123-117">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="4f123-117">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4f123-118">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="4f123-118">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="4f123-119">Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów oczekujących na akceptację odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4f123-119">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="4f123-120">Połączenia o przekroczeniu tego limitu są umieszczane w kolejce do momentu udostępnienia przestrzeni poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="4f123-120">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="4f123-121">`connectionTimeout` Atrybut ogranicza czas, przez który klient będzie oczekiwał na połączenie przed wygenerowaniem wyjątku połączenia.</span><span class="sxs-lookup"><span data-stu-id="4f123-121">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="4f123-122">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="4f123-122">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="4f123-123">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4f123-124">Wartość domyślna to 512 \* 1024 bajtów.</span><span class="sxs-lookup"><span data-stu-id="4f123-124">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="4f123-125">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="4f123-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4f123-126">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="4f123-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4f123-127">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="4f123-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4f123-128">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="4f123-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="4f123-129">Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu używany do przechowywania komunikatów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f123-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="4f123-130">Jeśli atrybut jest równy, ten atrybut `maxReceivedMessageSize` powinien być równy wartości atrybutu. `Buffered` `transferMode`</span><span class="sxs-lookup"><span data-stu-id="4f123-130">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="4f123-131">Jeśli atrybut jest równy, ten atrybut `maxReceivedMessageSize` nie może być większy niż wartość atrybutu i powinien mieć co najmniej rozmiar nagłówków. `Streamed` `transferMode`</span><span class="sxs-lookup"><span data-stu-id="4f123-131">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="4f123-132">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="4f123-132">The default is 65536.</span></span> <span data-ttu-id="4f123-133">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f123-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="4f123-134">Liczba całkowita określająca maksymalną liczbę połączeń wychodzących i przychodzących, które usługa zostanie utworzona/zaakceptowana.</span><span class="sxs-lookup"><span data-stu-id="4f123-134">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="4f123-135">Połączenia przychodzące i wychodzące są liczone względem oddzielnego limitu określonego przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="4f123-135">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="4f123-136">Połączenia przychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="4f123-136">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="4f123-137">Połączenia wychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="4f123-137">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="4f123-138">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="4f123-138">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="4f123-139">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4f123-140">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4f123-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4f123-141">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4f123-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4f123-142">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="4f123-142">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="4f123-143">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4f123-144">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4f123-145">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="4f123-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4f123-146">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4f123-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="4f123-147"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="4f123-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4f123-148">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4f123-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4f123-149">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4f123-149">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="4f123-150">Wartość logiczna określająca, czy włączone jest Udostępnianie portów TCP dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="4f123-150">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="4f123-151">`false`W takim przypadku każde powiązanie używa własnego portu wyłącznego.</span><span class="sxs-lookup"><span data-stu-id="4f123-151">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="4f123-152">To ustawienie ma zastosowanie tylko do usług, ponieważ nie ma to znaczenia dla klientów.</span><span class="sxs-lookup"><span data-stu-id="4f123-152">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4f123-153"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="4f123-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4f123-154">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4f123-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4f123-155">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="4f123-155">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="4f123-156"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="4f123-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4f123-157">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4f123-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4f123-158">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4f123-158">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="4f123-159">Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="4f123-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="4f123-160">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="4f123-160">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="4f123-161">Określa protokół transakcji, który ma być używany z tym powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4f123-161">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="4f123-162">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="4f123-162">Valid values are</span></span><br /><br /> <span data-ttu-id="4f123-163">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="4f123-163">-   OleTransactions</span></span><br /><span data-ttu-id="4f123-164">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="4f123-164">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="4f123-165">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="4f123-165">The default is OleTransactions.</span></span> <span data-ttu-id="4f123-166">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="4f123-166">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="4f123-167"><xref:System.ServiceModel.TransferMode> Wartość określająca, czy komunikaty są buforowane, czy przesyłane strumieniowo, czy też żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4f123-167">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f123-168">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4f123-168">Child elements</span></span>  
  
|<span data-ttu-id="4f123-169">Element</span><span class="sxs-lookup"><span data-stu-id="4f123-169">Element</span></span>|<span data-ttu-id="4f123-170">Opis</span><span class="sxs-lookup"><span data-stu-id="4f123-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f123-171">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4f123-171">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="4f123-172">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="4f123-173">Ten element jest typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4f123-173">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|<span data-ttu-id="4f123-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4f123-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4f123-175">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4f123-176">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4f123-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="4f123-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4f123-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="4f123-178">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="4f123-178">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f123-179">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4f123-179">Parent elements</span></span>  
  
|<span data-ttu-id="4f123-180">Element</span><span class="sxs-lookup"><span data-stu-id="4f123-180">Element</span></span>|<span data-ttu-id="4f123-181">Opis</span><span class="sxs-lookup"><span data-stu-id="4f123-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f123-182">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="4f123-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="4f123-183">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4f123-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f123-184">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f123-184">Remarks</span></span>

<span data-ttu-id="4f123-185">To powiązanie generuje stos komunikacji w czasie wykonywania domyślnie, który korzysta z zabezpieczeń transportu, protokołu TCP do dostarczania komunikatów i kodowania komunikatów binarnych.</span><span class="sxs-lookup"><span data-stu-id="4f123-185">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="4f123-186">To powiązanie jest odpowiednim wyborem systemu Windows Communication Foundation (WCF) w przypadku komunikacji za pośrednictwem intranetu.</span><span class="sxs-lookup"><span data-stu-id="4f123-186">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="4f123-187">Konfiguracja domyślna dla programu `netTcpBinding` jest szybsza niż konfiguracja podana `wsHttpBinding`przez, ale jest przeznaczona tylko do komunikacji z WCF.</span><span class="sxs-lookup"><span data-stu-id="4f123-187">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="4f123-188">Zachowanie zabezpieczeń można skonfigurować przy użyciu opcjonalnego `securityMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4f123-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="4f123-189">Korzystanie z protokołu WS-ReliableMessaging można skonfigurować przy użyciu opcjonalnego `reliableSessionEnabled` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4f123-189">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="4f123-190">Jednak niezawodna obsługa komunikatów jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="4f123-190">But reliable messaging is off by default.</span></span> <span data-ttu-id="4f123-191">Ogólnie rzecz biorąc, powiązania dostarczone przez system http, takie `wsHttpBinding` jak `basicHttpBinding` i, są domyślnie skonfigurowane do włączania funkcji, natomiast `netTcpBinding` powiązanie to domyślnie wyłączone, co pozwala na uzyskanie pomocy technicznej, na przykład dla jednego z specyfikacje WS-\*.</span><span class="sxs-lookup"><span data-stu-id="4f123-191">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="4f123-192">Oznacza to, że domyślna konfiguracja protokołu TCP jest szybsza podczas wymiany komunikatów między punktami końcowymi niż te skonfigurowane dla powiązań HTTP domyślnie.</span><span class="sxs-lookup"><span data-stu-id="4f123-192">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f123-193">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f123-193">Example</span></span>

<span data-ttu-id="4f123-194">Powiązanie jest określone w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="4f123-194">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4f123-195">Typ powiązania jest określony w `binding` atrybucie `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4f123-195">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="4f123-196">Jeśli chcesz skonfigurować powiązanie netTcpBinding i zmienić niektóre z jego ustawień, musisz zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-196">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="4f123-197">Punkt końcowy musi odwoływać się do konfiguracji powiązania `bindingConfiguration` z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="4f123-197">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="4f123-198">W poniższym przykładzie zdefiniowano konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="4f123-198">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="4f123-199">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f123-199">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="4f123-200">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4f123-200">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f123-201">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="4f123-201">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4f123-202">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4f123-202">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4f123-203">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="4f123-203">\<binding></span></span>](../../../misc/binding.md)
