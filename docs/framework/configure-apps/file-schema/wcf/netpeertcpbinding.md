---
title: '&lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 9032372f8e3344e9b1021be19a32230986b328a2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467393"
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="2a5b9-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2a5b9-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="2a5b9-103">Definiuje powiązanie dla równorzędnego kanału określonych dla obsługi wiadomości TCP.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="2a5b9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a5b9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a5b9-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="2a5b9-105">\<bindings></span></span>  
<span data-ttu-id="2a5b9-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="2a5b9-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5b9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a5b9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a5b9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2a5b9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2a5b9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a5b9-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a5b9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2a5b9-110">Attributes</span></span>  
  
|<span data-ttu-id="2a5b9-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2a5b9-111">Attribute</span></span>|<span data-ttu-id="2a5b9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2a5b9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a5b9-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="2a5b9-113">closeTimeout</span></span>|<span data-ttu-id="2a5b9-114">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2a5b9-115">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2a5b9-116">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2a5b9-117">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="2a5b9-117">listenIPAddress</span></span>|<span data-ttu-id="2a5b9-118">Ciąg, który określa adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="2a5b9-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-119">The default is `null`.</span></span>|  
|<span data-ttu-id="2a5b9-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="2a5b9-120">maxBufferPoolSize</span></span>|<span data-ttu-id="2a5b9-121">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="2a5b9-122">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="2a5b9-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="2a5b9-123">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="2a5b9-124">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="2a5b9-125">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="2a5b9-126">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="2a5b9-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="2a5b9-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="2a5b9-128">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="2a5b9-129">Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="2a5b9-130">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="2a5b9-131">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-131">The default is 65536.</span></span>|  
|<span data-ttu-id="2a5b9-132">nazwa</span><span class="sxs-lookup"><span data-stu-id="2a5b9-132">name</span></span>|<span data-ttu-id="2a5b9-133">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2a5b9-134">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="2a5b9-135">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2a5b9-136">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2a5b9-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="2a5b9-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="2a5b9-137">openTimeout</span></span>|<span data-ttu-id="2a5b9-138">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2a5b9-139">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2a5b9-140">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2a5b9-141">port</span><span class="sxs-lookup"><span data-stu-id="2a5b9-141">port</span></span>|<span data-ttu-id="2a5b9-142">Liczba całkowita określająca port interfejsu sieciowego, w którym to powiązanie będzie przetwarzało równorzędny kanał komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="2a5b9-143">Ta wartość musi należeć do zakresu od <xref:System.Net.IPEndPoint.MinPort> i <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="2a5b9-144">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-144">The default is 0.</span></span>|  
|<span data-ttu-id="2a5b9-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="2a5b9-145">receiveTimeout</span></span>|<span data-ttu-id="2a5b9-146">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2a5b9-147">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2a5b9-148">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="2a5b9-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="2a5b9-149">sendTimeout</span></span>|<span data-ttu-id="2a5b9-150">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2a5b9-151">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2a5b9-152">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a5b9-153">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2a5b9-153">Child Elements</span></span>  
  
|<span data-ttu-id="2a5b9-154">Element</span><span class="sxs-lookup"><span data-stu-id="2a5b9-154">Element</span></span>|<span data-ttu-id="2a5b9-155">Opis</span><span class="sxs-lookup"><span data-stu-id="2a5b9-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a5b9-156">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="2a5b9-156">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="2a5b9-157">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2a5b9-158">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="2a5b9-159">\<resolver></span><span class="sxs-lookup"><span data-stu-id="2a5b9-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="2a5b9-160">Określa program rozpoznawania nazw równorzędnych używane przez to wiązanie można rozpoznać elementu równorzędnego siatki identyfikator na adresy IP punktów końcowych węzłów w obrębie siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="2a5b9-161">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="2a5b9-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="2a5b9-162">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-162">Defines the security settings for the message.</span></span> <span data-ttu-id="2a5b9-163">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a5b9-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a5b9-164">Parent Elements</span></span>  
  
|<span data-ttu-id="2a5b9-165">Element</span><span class="sxs-lookup"><span data-stu-id="2a5b9-165">Element</span></span>|<span data-ttu-id="2a5b9-166">Opis</span><span class="sxs-lookup"><span data-stu-id="2a5b9-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a5b9-167">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="2a5b9-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="2a5b9-168">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a5b9-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a5b9-169">Remarks</span></span>  
 <span data-ttu-id="2a5b9-170">To powiązanie zapewnia obsługę tworzenia aplikacji peer-to-peer lub wielostronnej za pomocą transportu elementu równorzędnego za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="2a5b9-171">Każdy węzeł równorzędny umożliwia hostowanie wielu kanałów równorzędnych zdefiniowane przy użyciu tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5b9-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a5b9-172">Example</span></span>  
 <span data-ttu-id="2a5b9-173">Poniższy przykład pokazuje, za pomocą powiązania NetPeerTcpBinding, co zapewnia wielostronnej komunikację z wykorzystaniem kanał elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="2a5b9-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="2a5b9-174">Szczegółowe scenariusz użycia tego powiązania można znaleźć [sieci elementów równorzędnych protokołu TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="2a5b9-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a5b9-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a5b9-175">See Also</span></span>  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [<span data-ttu-id="2a5b9-176">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2a5b9-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2a5b9-177">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="2a5b9-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2a5b9-178">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="2a5b9-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2a5b9-179">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2a5b9-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="2a5b9-180">NET elementu równorzędnego protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="2a5b9-180">Net Peer TCP</span></span>](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [<span data-ttu-id="2a5b9-181">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="2a5b9-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
