---
title: '&lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a582f009719245483bdfe9192d775347c1f1a29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetnamedpipebindinggt"></a><span data-ttu-id="a8713-102">&lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a8713-102">&lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="a8713-103">Definiuje powiązanie, które jest bezpieczne, niezawodne, zoptymalizowane pod kątem na komputerze komunikacji pomiędzy procesami.</span><span class="sxs-lookup"><span data-stu-id="a8713-103">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="a8713-104">Domyślnie generuje środowiska uruchomieniowego stosu komunikacji z WS-ReliableMessaging niezawodności, zabezpieczeń transportu dla bezpieczeństwa transfer nazwanych potoków do dostarczanie komunikatów, a Kodowanie komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="a8713-104">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="a8713-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a8713-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8713-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a8713-106">\<bindings></span></span>  
<span data-ttu-id="a8713-107">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="a8713-107">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8713-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8713-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"   
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"  
      transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"  
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
      <security mode="None/Transport">  
            <transport  protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8713-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a8713-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a8713-110">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a8713-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8713-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a8713-111">Attributes</span></span>  
  
|<span data-ttu-id="a8713-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a8713-112">Attribute</span></span>|<span data-ttu-id="a8713-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a8713-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8713-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a8713-114">closeTimeout</span></span>|<span data-ttu-id="a8713-115">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="a8713-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a8713-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8713-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8713-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8713-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a8713-118">parametru hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a8713-118">hostnameComparisonMode</span></span>|<span data-ttu-id="a8713-119">Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="a8713-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="a8713-120">Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="a8713-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a8713-121">Wartość domyślna to `StrongWildcard`, który ignoruje nazwy hosta w dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a8713-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="a8713-122">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a8713-122">maxBufferPoolSize</span></span>|<span data-ttu-id="a8713-123">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8713-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="a8713-124">Wartość domyślna to 524,288 bajtów (512 * 1024).</span><span class="sxs-lookup"><span data-stu-id="a8713-124">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="a8713-125">Bufory za pomocą wielu części programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a8713-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="a8713-126">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna.</span><span class="sxs-lookup"><span data-stu-id="a8713-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="a8713-127">Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="a8713-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="a8713-128">W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="a8713-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="a8713-129">wartość maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a8713-129">maxBufferSize</span></span>|<span data-ttu-id="a8713-130">Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach buforu używany do przechowywania wiadomości w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a8713-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="a8713-131">Jeśli bufor jest pełna, nadmiarowych danych pozostaje w podstawowej gniazda do momentu buforu ma miejsce ponownie.</span><span class="sxs-lookup"><span data-stu-id="a8713-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="a8713-132">Ta wartość nie może być mniejsza niż `maxReceivedMessageSize` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a8713-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="a8713-133">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="a8713-133">The default is 65536.</span></span> <span data-ttu-id="a8713-134">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8713-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="a8713-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="a8713-135">maxConnections</span></span>|<span data-ttu-id="a8713-136">Liczba całkowita określająca maksymalną liczbę połączeń wychodzące i przychodzące usługi Utwórz/akceptuje.</span><span class="sxs-lookup"><span data-stu-id="a8713-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="a8713-137">Połączenia przychodzące i wychodzące są uwzględniane w oddzielnych określonym przez atrybut.</span><span class="sxs-lookup"><span data-stu-id="a8713-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="a8713-138">Połączenia przychodzące poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="a8713-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="a8713-139">Połączenia wychodzące poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="a8713-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="a8713-140">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="a8713-140">The default is 10.</span></span>|  
|<span data-ttu-id="a8713-141">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a8713-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="a8713-142">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="a8713-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a8713-143">Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a8713-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="a8713-144">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a8713-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a8713-145">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="a8713-145">The default is 65536.</span></span>|  
|<span data-ttu-id="a8713-146">nazwa</span><span class="sxs-lookup"><span data-stu-id="a8713-146">name</span></span>|<span data-ttu-id="a8713-147">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8713-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a8713-148">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8713-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a8713-149">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="a8713-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a8713-150">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8713-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="a8713-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="a8713-151">openTimeout</span></span>|<span data-ttu-id="a8713-152">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="a8713-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a8713-153">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8713-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8713-154">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8713-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a8713-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a8713-155">receiveTimeout</span></span>|<span data-ttu-id="a8713-156">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="a8713-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a8713-157">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8713-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8713-158">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a8713-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="a8713-159">właściwości sendTimeout</span><span class="sxs-lookup"><span data-stu-id="a8713-159">sendTimeout</span></span>|<span data-ttu-id="a8713-160">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="a8713-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a8713-161">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a8713-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a8713-162">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a8713-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a8713-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="a8713-163">transactionFlow</span></span>|<span data-ttu-id="a8713-164">Wartość logiczna określająca, czy wiązanie obsługuje przechodzenia WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="a8713-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="a8713-165">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a8713-165">The default is `false`.</span></span>|  
|<span data-ttu-id="a8713-166">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="a8713-166">transactionProtocol</span></span>|<span data-ttu-id="a8713-167">Określa protokół transakcji do użycia z tym powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="a8713-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="a8713-168">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="a8713-168">Valid values are</span></span><br /><br /> <span data-ttu-id="a8713-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="a8713-169">-   OleTransactions</span></span><br /><span data-ttu-id="a8713-170">WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="a8713-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="a8713-171">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="a8713-171">The default is OleTransactions.</span></span> <span data-ttu-id="a8713-172">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="a8713-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="a8713-173">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="a8713-173">transferMode</span></span>|<span data-ttu-id="a8713-174">A <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a8713-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8713-175">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a8713-175">Child Elements</span></span>  
  
|<span data-ttu-id="a8713-176">Element</span><span class="sxs-lookup"><span data-stu-id="a8713-176">Element</span></span>|<span data-ttu-id="a8713-177">Opis</span><span class="sxs-lookup"><span data-stu-id="a8713-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8713-178">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="a8713-178">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="a8713-179">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8713-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="a8713-180">Ten element jest typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="a8713-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="a8713-181">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="a8713-181">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="a8713-182">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="a8713-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a8713-183">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a8713-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8713-184">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a8713-184">Parent Elements</span></span>  
  
|<span data-ttu-id="a8713-185">Element</span><span class="sxs-lookup"><span data-stu-id="a8713-185">Element</span></span>|<span data-ttu-id="a8713-186">Opis</span><span class="sxs-lookup"><span data-stu-id="a8713-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8713-187">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a8713-187">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="a8713-188">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a8713-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8713-189">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a8713-189">Remarks</span></span>  
 <span data-ttu-id="a8713-190">`NetNamedPipeBinding` Generuje stosu komunikacji środowiska wykonawczego domyślnie korzysta z zabezpieczeń transportu, nazwanych potoków do dostarczanie komunikatów, a Kodowanie komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="a8713-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="a8713-191">To powiązanie jest właściwy Windows Communication Foundation (WCF) dostarczane przez system wybór komunikacji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a8713-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="a8713-192">Obsługuje ona również transakcji.</span><span class="sxs-lookup"><span data-stu-id="a8713-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="a8713-193">Konfigurację domyślną dla `NetNamedPipeBinding` jest podobna do konfiguracji udostępniane przez `NetTcpBinding`, ale jest łatwiejsze, ponieważ implementacja WCF jest przeznaczone tylko do użytku na komputerze i w związku z tym są mniej funkcji uwidocznione.</span><span class="sxs-lookup"><span data-stu-id="a8713-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="a8713-194">Najbardziej znacząca różnica jest to, że `securityMode` ustawienie tylko oferty `None` i `Transport` opcje.</span><span class="sxs-lookup"><span data-stu-id="a8713-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="a8713-195">Obsługi zabezpieczeń protokołu SOAP nie jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="a8713-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="a8713-196">Zachowania zabezpieczeń jest można skonfigurować za pomocą opcjonalnego `securityMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a8713-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8713-197">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8713-197">Example</span></span>  
 <span data-ttu-id="a8713-198">W poniższym przykładzie pokazano powiązanie netNamedPipeBinding, który zapewnia komunikację między procesami na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a8713-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="a8713-199">Nazwane potoki nie działają na komputerach.</span><span class="sxs-lookup"><span data-stu-id="a8713-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="a8713-200">Powiązanie jest określona w plikach konfiguracji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="a8713-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="a8713-201">Typ powiązania jest określona w `binding` atrybutu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a8713-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="a8713-202">Jeśli chcesz skonfigurować powiązanie netNamedPipeBinding i zmieniania jego ustawień, należy zdefiniować konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8713-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="a8713-203">Punkt końcowy musi odwoływać się Konfiguracja powiązania o nazwie z `bindingConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a8713-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="a8713-204">W tym przykładzie nosi nazwę konfiguracji powiązania Binding1.</span><span class="sxs-lookup"><span data-stu-id="a8713-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
        <binding   
                 closeTimeout="00:01:00"  
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
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8713-205">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8713-205">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [<span data-ttu-id="a8713-206">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a8713-206">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="a8713-207">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a8713-207">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a8713-208">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="a8713-208">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a8713-209">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="a8713-209">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
