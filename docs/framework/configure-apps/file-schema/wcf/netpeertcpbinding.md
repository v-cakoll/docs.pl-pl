---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: a039e805bc4378582d7a7bcf6ef84591ec3d2b6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261441"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="0fbd7-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="0fbd7-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="0fbd7-102">Definiuje powiązanie dla równorzędnego kanału określonych dla obsługi wiadomości TCP.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="0fbd7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0fbd7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0fbd7-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0fbd7-104">\<bindings></span></span>  
<span data-ttu-id="0fbd7-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="0fbd7-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fbd7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fbd7-106">Syntax</span></span>  
  
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
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fbd7-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0fbd7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0fbd7-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0fbd7-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fbd7-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0fbd7-109">Attributes</span></span>  
  
|<span data-ttu-id="0fbd7-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0fbd7-110">Attribute</span></span>|<span data-ttu-id="0fbd7-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0fbd7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fbd7-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="0fbd7-112">closeTimeout</span></span>|<span data-ttu-id="0fbd7-113">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0fbd7-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0fbd7-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0fbd7-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="0fbd7-116">listenIPAddress</span></span>|<span data-ttu-id="0fbd7-117">Ciąg, który określa adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="0fbd7-118">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-118">The default is `null`.</span></span>|  
|<span data-ttu-id="0fbd7-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0fbd7-119">maxBufferPoolSize</span></span>|<span data-ttu-id="0fbd7-120">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="0fbd7-121">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="0fbd7-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="0fbd7-122">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="0fbd7-123">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0fbd7-124">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0fbd7-125">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="0fbd7-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0fbd7-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="0fbd7-127">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0fbd7-128">Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="0fbd7-129">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0fbd7-130">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-130">The default is 65536.</span></span>|  
|<span data-ttu-id="0fbd7-131">nazwa</span><span class="sxs-lookup"><span data-stu-id="0fbd7-131">name</span></span>|<span data-ttu-id="0fbd7-132">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0fbd7-133">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0fbd7-134">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0fbd7-135">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0fbd7-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="0fbd7-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="0fbd7-136">openTimeout</span></span>|<span data-ttu-id="0fbd7-137">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0fbd7-138">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0fbd7-139">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0fbd7-140">port</span><span class="sxs-lookup"><span data-stu-id="0fbd7-140">port</span></span>|<span data-ttu-id="0fbd7-141">Liczba całkowita określająca port interfejsu sieciowego, w którym to powiązanie będzie przetwarzało równorzędny kanał komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="0fbd7-142">Ta wartość musi należeć do zakresu od <xref:System.Net.IPEndPoint.MinPort> i <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="0fbd7-143">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-143">The default is 0.</span></span>|  
|<span data-ttu-id="0fbd7-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="0fbd7-144">receiveTimeout</span></span>|<span data-ttu-id="0fbd7-145">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0fbd7-146">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0fbd7-147">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="0fbd7-148">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="0fbd7-148">sendTimeout</span></span>|<span data-ttu-id="0fbd7-149">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0fbd7-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0fbd7-151">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fbd7-152">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0fbd7-152">Child Elements</span></span>  
  
|<span data-ttu-id="0fbd7-153">Element</span><span class="sxs-lookup"><span data-stu-id="0fbd7-153">Element</span></span>|<span data-ttu-id="0fbd7-154">Opis</span><span class="sxs-lookup"><span data-stu-id="0fbd7-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fbd7-155">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="0fbd7-155">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="0fbd7-156">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0fbd7-157">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="0fbd7-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="0fbd7-158">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="0fbd7-159">Określa program rozpoznawania nazw równorzędnych używane przez to wiązanie można rozpoznać elementu równorzędnego siatki identyfikator na adresy IP punktów końcowych węzłów w obrębie siatki elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="0fbd7-160">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="0fbd7-160">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="0fbd7-161">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-161">Defines the security settings for the message.</span></span> <span data-ttu-id="0fbd7-162">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fbd7-163">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0fbd7-163">Parent Elements</span></span>  
  
|<span data-ttu-id="0fbd7-164">Element</span><span class="sxs-lookup"><span data-stu-id="0fbd7-164">Element</span></span>|<span data-ttu-id="0fbd7-165">Opis</span><span class="sxs-lookup"><span data-stu-id="0fbd7-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fbd7-166">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0fbd7-166">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="0fbd7-167">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fbd7-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fbd7-168">Remarks</span></span>  
 <span data-ttu-id="0fbd7-169">To powiązanie zapewnia obsługę tworzenia aplikacji peer-to-peer lub wielostronnej za pomocą transportu elementu równorzędnego za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="0fbd7-170">Każdy węzeł równorzędny umożliwia hostowanie wielu kanałów równorzędnych zdefiniowane przy użyciu tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fbd7-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fbd7-171">Example</span></span>  
 <span data-ttu-id="0fbd7-172">Poniższy przykład pokazuje, za pomocą powiązania NetPeerTcpBinding, co zapewnia wielostronnej komunikację z wykorzystaniem kanał elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="0fbd7-173">Szczegółowe scenariusz użycia tego powiązania można znaleźć [sieci elementów równorzędnych protokołu TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="0fbd7-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
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
  
## <a name="see-also"></a><span data-ttu-id="0fbd7-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fbd7-174">See also</span></span>
- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="0fbd7-175">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0fbd7-175">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0fbd7-176">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="0fbd7-176">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0fbd7-177">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="0fbd7-177">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0fbd7-178">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0fbd7-178">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="0fbd7-179">NET elementu równorzędnego protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="0fbd7-179">Net Peer TCP</span></span>](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)
- [<span data-ttu-id="0fbd7-180">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="0fbd7-180">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
