---
title: '&lt;netTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: 0849120edf7d4b8948b3632cfe2fc81f1bdff1eb
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148191"
---
# <a name="ltnettcpbindinggt"></a><span data-ttu-id="f69cf-102">&lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f69cf-102">&lt;netTcpBinding&gt;</span></span>

<span data-ttu-id="f69cf-103">Określa bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="f69cf-103">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="f69cf-104">Domyślnie generuje ona stosu środowiska uruchomieniowego komunikacji z usługą Windows Security dla zabezpieczenia wiadomości i każde uwierzytelnienie, protokołu TCP na potrzeby dostarczania wiadomości i kodowania komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="f69cf-104">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="f69cf-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f69cf-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f69cf-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f69cf-106">\<bindings></span></span>  
<span data-ttu-id="f69cf-107">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f69cf-107">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f69cf-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f69cf-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f69cf-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f69cf-109">Attributes and elements</span></span>

<span data-ttu-id="f69cf-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f69cf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f69cf-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f69cf-111">Attributes</span></span>  
  
|<span data-ttu-id="f69cf-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f69cf-112">Attribute</span></span>|<span data-ttu-id="f69cf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f69cf-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f69cf-114">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="f69cf-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f69cf-115">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f69cf-116">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f69cf-116">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="f69cf-117">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="f69cf-117">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f69cf-118">Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f69cf-118">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f69cf-119">Wartość domyślna to `StrongWildcard`, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-119">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="f69cf-120">Dodatnia liczba całkowita, określająca maksymalną liczbę kanałów, które oczekuje na zatwierdzenie na odbiorniku.</span><span class="sxs-lookup"><span data-stu-id="f69cf-120">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="f69cf-121">Połączenia przekraczające ten limit są umieszczane w kolejce, dopóki miejsce poniżej limitu staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="f69cf-121">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="f69cf-122">`connectionTimeout` Atrybut ogranicza czas, klient będzie czekać połączenia zanim zostanie zgłoszony wyjątek połączenia.</span><span class="sxs-lookup"><span data-stu-id="f69cf-122">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="f69cf-123">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="f69cf-123">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="f69cf-124">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="f69cf-125">Wartość domyślna to 512 \* 1024 bajty.</span><span class="sxs-lookup"><span data-stu-id="f69cf-125">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="f69cf-126">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="f69cf-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="f69cf-127">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="f69cf-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f69cf-128">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="f69cf-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f69cf-129">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="f69cf-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="f69cf-130">Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach buforu używany do przechowywania komunikatów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f69cf-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="f69cf-131">Jeśli `transferMode` atrybutu jest równa `Buffered`, ten atrybut powinien być równy `maxReceivedMessageSize` wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f69cf-131">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="f69cf-132">Jeśli `transferMode` atrybutu jest równa `Streamed`, ten atrybut nie może mieć więcej niż `maxReceivedMessageSize` wartość atrybutu, a powinien wynosić co najmniej rozmiar nagłówków.</span><span class="sxs-lookup"><span data-stu-id="f69cf-132">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="f69cf-133">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="f69cf-133">The default is 65536.</span></span> <span data-ttu-id="f69cf-134">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="f69cf-135">Liczba całkowita określająca maksymalną liczbę połączeń wychodzące i przychodzące usługa tworzenia/akceptuje.</span><span class="sxs-lookup"><span data-stu-id="f69cf-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="f69cf-136">Połączenia przychodzące i wychodzące są przeliczane względem oddzielne limit określony przez atrybut.</span><span class="sxs-lookup"><span data-stu-id="f69cf-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="f69cf-137">Połączenia przychodzące poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="f69cf-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="f69cf-138">Połączenia wychodzące poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="f69cf-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="f69cf-139">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="f69cf-139">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="f69cf-140">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="f69cf-140">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f69cf-141">Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f69cf-141">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="f69cf-142">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f69cf-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f69cf-143">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="f69cf-143">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="f69cf-144">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f69cf-145">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f69cf-146">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="f69cf-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f69cf-147">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f69cf-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f69cf-148">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="f69cf-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f69cf-149">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f69cf-150">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f69cf-150">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="f69cf-151">Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f69cf-151">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="f69cf-152">Jeśli jest to `false`, wyłączny portu korzysta z każdego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-152">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="f69cf-153">To ustawienie jest odpowiednie tylko dla usług, ponieważ nie dotyczy to klientów.</span><span class="sxs-lookup"><span data-stu-id="f69cf-153">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f69cf-154">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f69cf-155">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f69cf-156">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f69cf-156">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f69cf-157">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f69cf-158">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f69cf-159">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f69cf-159">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="f69cf-160">Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="f69cf-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="f69cf-161">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f69cf-161">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="f69cf-162">Określa protokół transakcji do użycia z tym powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="f69cf-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="f69cf-163">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f69cf-163">Valid values are</span></span><br /><br /> <span data-ttu-id="f69cf-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f69cf-164">-   OleTransactions</span></span><br /><span data-ttu-id="f69cf-165">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="f69cf-165">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="f69cf-166">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="f69cf-166">The default is OleTransactions.</span></span> <span data-ttu-id="f69cf-167">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="f69cf-168">A <xref:System.ServiceModel.TransferMode> wartość określającą, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f69cf-168">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f69cf-169">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f69cf-169">Child elements</span></span>  
  
|<span data-ttu-id="f69cf-170">Element</span><span class="sxs-lookup"><span data-stu-id="f69cf-170">Element</span></span>|<span data-ttu-id="f69cf-171">Opis</span><span class="sxs-lookup"><span data-stu-id="f69cf-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f69cf-172">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f69cf-172">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="f69cf-173">Definiuje ustawienia zabezpieczeń dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="f69cf-174">Ten element jest typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-174">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[<span data-ttu-id="f69cf-175">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="f69cf-175">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f69cf-176">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f69cf-177">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f69cf-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="f69cf-178">reliableSession</span><span class="sxs-lookup"><span data-stu-id="f69cf-178">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="f69cf-179">Określa, jeśli niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="f69cf-179">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f69cf-180">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f69cf-180">Parent elements</span></span>  
  
|<span data-ttu-id="f69cf-181">Element</span><span class="sxs-lookup"><span data-stu-id="f69cf-181">Element</span></span>|<span data-ttu-id="f69cf-182">Opis</span><span class="sxs-lookup"><span data-stu-id="f69cf-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f69cf-183">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f69cf-183">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f69cf-184">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f69cf-184">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f69cf-185">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f69cf-185">Remarks</span></span>

<span data-ttu-id="f69cf-186">To powiązanie generuje stosu komunikację w czasie wykonywania, domyślna, która używa zabezpieczenia transportu TCP do dostarczania wiadomości i kodowania komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="f69cf-186">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="f69cf-187">To powiązanie jest odpowiednie Windows Communication Foundation (WCF) dostarczane przez system wyborem dla komunikacji za pośrednictwem sieci Intranet.</span><span class="sxs-lookup"><span data-stu-id="f69cf-187">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="f69cf-188">W domyślnej konfiguracji `netTcpBinding` jest szybsza niż konfiguracja, dostarczone przez `wsHttpBinding`, ale jest przeznaczona tylko do komunikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="f69cf-188">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="f69cf-189">Zachowania zabezpieczeń jest można skonfigurować za pomocą opcjonalnego `securityMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f69cf-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="f69cf-190">Korzystanie z WS-ReliableMessaging jest można skonfigurować za pomocą opcjonalnego `reliableSessionEnabled` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f69cf-190">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="f69cf-191">Jednak niezawodna obsługa komunikatów jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f69cf-191">But reliable messaging is off by default.</span></span> <span data-ttu-id="f69cf-192">Ogólnie rzecz biorąc, HTTP powiązania dostarczane przez system takich jak `wsHttpBinding` i `basicHttpBinding` są skonfigurowane do włączyć domyślnie, natomiast `netTcpBinding` powiązania wyłącza rzeczy domyślnie, aby musisz wyrazić zgodę na uzyskiwanie pomocy technicznej, na przykład dla jednego z WS-\* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f69cf-192">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="f69cf-193">Oznacza to, że konfigurację domyślną dla protokołu TCP jest szybszy o wymiana wiadomości między punktami końcowymi, niż jest domyślnie skonfigurowana do powiązania protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f69cf-193">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f69cf-194">Przykład</span><span class="sxs-lookup"><span data-stu-id="f69cf-194">Example</span></span>

<span data-ttu-id="f69cf-195">Powiązanie jest określona w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="f69cf-195">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="f69cf-196">Typ powiązania jest określona w `binding` atrybutu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f69cf-196">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="f69cf-197">Jeśli chcesz skonfigurować powiązanie netTcpBinding i zmienić niektóre z jego ustawienia, należy zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-197">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="f69cf-198">Punkt końcowy musi odwoływać się do konfiguracji powiązania z `bindingConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f69cf-198">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="f69cf-199">W poniższym przykładzie zdefiniowano Konfiguracja powiązania.</span><span class="sxs-lookup"><span data-stu-id="f69cf-199">In the following example, a binding configuration is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f69cf-200">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f69cf-200">See also</span></span>  

- <xref:System.ServiceModel.NetTcpBinding>  
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
- [<span data-ttu-id="f69cf-201">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f69cf-201">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
- [<span data-ttu-id="f69cf-202">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f69cf-202">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
- [<span data-ttu-id="f69cf-203">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f69cf-203">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
- [<span data-ttu-id="f69cf-204">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f69cf-204">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
