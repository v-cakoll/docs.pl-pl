---
title: '&lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a890243ee12202efa9743a6151255525c7f78be2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="e962e-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e962e-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="e962e-103">Definiuje powiązanie dla równorzędnego kanału określonych dla obsługi wiadomości TCP.</span><span class="sxs-lookup"><span data-stu-id="e962e-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="e962e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e962e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e962e-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e962e-105">\<bindings></span></span>  
<span data-ttu-id="e962e-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="e962e-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e962e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e962e-107">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e962e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e962e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e962e-109">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e962e-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e962e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e962e-110">Attributes</span></span>  
  
|<span data-ttu-id="e962e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e962e-111">Attribute</span></span>|<span data-ttu-id="e962e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e962e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e962e-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="e962e-113">closeTimeout</span></span>|<span data-ttu-id="e962e-114">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="e962e-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e962e-115">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e962e-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e962e-116">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e962e-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e962e-117">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="e962e-117">listenIPAddress</span></span>|<span data-ttu-id="e962e-118">Ciąg, który określa adres IP, na którym węzeł elementu równorzędnego będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="e962e-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="e962e-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="e962e-119">The default is `null`.</span></span>|  
|<span data-ttu-id="e962e-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e962e-120">maxBufferPoolSize</span></span>|<span data-ttu-id="e962e-121">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e962e-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e962e-122">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="e962e-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="e962e-123">Bufory za pomocą wielu części programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e962e-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="e962e-124">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna.</span><span class="sxs-lookup"><span data-stu-id="e962e-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e962e-125">Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="e962e-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e962e-126">W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="e962e-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="e962e-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e962e-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="e962e-128">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="e962e-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e962e-129">Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e962e-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="e962e-130">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e962e-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e962e-131">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="e962e-131">The default is 65536.</span></span>|  
|<span data-ttu-id="e962e-132">nazwa</span><span class="sxs-lookup"><span data-stu-id="e962e-132">name</span></span>|<span data-ttu-id="e962e-133">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="e962e-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e962e-134">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e962e-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e962e-135">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="e962e-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e962e-136">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e962e-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="e962e-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="e962e-137">openTimeout</span></span>|<span data-ttu-id="e962e-138">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="e962e-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e962e-139">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e962e-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e962e-140">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e962e-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e962e-141">port</span><span class="sxs-lookup"><span data-stu-id="e962e-141">port</span></span>|<span data-ttu-id="e962e-142">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzało równorzędny kanał komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="e962e-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="e962e-143">Ta wartość musi należeć do zakresu od <xref:System.Net.IPEndPoint.MinPort> i <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="e962e-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="e962e-144">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="e962e-144">The default is 0.</span></span>|  
|<span data-ttu-id="e962e-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="e962e-145">receiveTimeout</span></span>|<span data-ttu-id="e962e-146">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="e962e-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e962e-147">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e962e-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e962e-148">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="e962e-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="e962e-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="e962e-149">sendTimeout</span></span>|<span data-ttu-id="e962e-150">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e962e-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e962e-151">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e962e-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e962e-152">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e962e-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e962e-153">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e962e-153">Child Elements</span></span>  
  
|<span data-ttu-id="e962e-154">Element</span><span class="sxs-lookup"><span data-stu-id="e962e-154">Element</span></span>|<span data-ttu-id="e962e-155">Opis</span><span class="sxs-lookup"><span data-stu-id="e962e-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e962e-156">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="e962e-156">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="e962e-157">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="e962e-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e962e-158">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e962e-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="e962e-159">\<resolver></span><span class="sxs-lookup"><span data-stu-id="e962e-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="e962e-160">Określa program rozpoznawania elementów równorzędnych używany przez to powiązanie do rozpoznawania elementu równorzędnego ID siatki adresy IP punktu końcowego węzłach w obrębie siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e962e-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="e962e-161">\<security></span><span class="sxs-lookup"><span data-stu-id="e962e-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="e962e-162">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e962e-162">Defines the security settings for the message.</span></span> <span data-ttu-id="e962e-163">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e962e-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e962e-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e962e-164">Parent Elements</span></span>  
  
|<span data-ttu-id="e962e-165">Element</span><span class="sxs-lookup"><span data-stu-id="e962e-165">Element</span></span>|<span data-ttu-id="e962e-166">Opis</span><span class="sxs-lookup"><span data-stu-id="e962e-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e962e-167">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e962e-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="e962e-168">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e962e-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e962e-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e962e-169">Remarks</span></span>  
 <span data-ttu-id="e962e-170">To powiązanie umożliwia tworzenie aplikacji peer-to-peer lub wielopartyjnej przy użyciu transportu elementu równorzędnego za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="e962e-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="e962e-171">Każdy węzeł równorzędny może obsługiwać wiele kanałów elementów równorzędnych zdefiniowane przy użyciu tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="e962e-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e962e-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="e962e-172">Example</span></span>  
 <span data-ttu-id="e962e-173">W poniższym przykładzie pokazano, za pomocą tego powiązania NetPeerTcpBinding, która zapewnia wielopartyjnej komunikacji przy użyciu kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="e962e-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="e962e-174">Szczegółowe scenariusz użycia tego powiązania, zobacz [Net TCP równorzędnej](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="e962e-174">For a detailed scenario of using this binding, see [Net Peer TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e962e-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e962e-175">See Also</span></span>  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [<span data-ttu-id="e962e-176">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e962e-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e962e-177">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e962e-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e962e-178">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e962e-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e962e-179">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e962e-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="e962e-180">NET elementów równorzędnych protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e962e-180">Net Peer TCP</span></span>](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [<span data-ttu-id="e962e-181">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="e962e-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
