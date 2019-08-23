---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: fc1930889235805d68d88aa8080f8f9fb3235612
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933037"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="1ef50-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1ef50-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="1ef50-102">Definiuje powiązanie dla obsługi komunikatów TCP określonego kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="1ef50-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="1ef50-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ef50-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ef50-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="1ef50-104">\<bindings></span></span>  
<span data-ttu-id="1ef50-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1ef50-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef50-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ef50-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ef50-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1ef50-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1ef50-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1ef50-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ef50-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1ef50-109">Attributes</span></span>  
  
|<span data-ttu-id="1ef50-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1ef50-110">Attribute</span></span>|<span data-ttu-id="1ef50-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1ef50-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ef50-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="1ef50-112">closeTimeout</span></span>|<span data-ttu-id="1ef50-113"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1ef50-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1ef50-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ef50-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ef50-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1ef50-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="1ef50-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="1ef50-116">listenIPAddress</span></span>|<span data-ttu-id="1ef50-117">Ciąg określający adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="1ef50-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="1ef50-118">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="1ef50-118">The default is `null`.</span></span>|  
|<span data-ttu-id="1ef50-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="1ef50-119">maxBufferPoolSize</span></span>|<span data-ttu-id="1ef50-120">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ef50-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="1ef50-121">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="1ef50-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="1ef50-122">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="1ef50-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="1ef50-123">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="1ef50-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="1ef50-124">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="1ef50-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="1ef50-125">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="1ef50-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="1ef50-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="1ef50-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="1ef50-127">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ef50-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1ef50-128">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="1ef50-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="1ef50-129">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1ef50-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1ef50-130">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="1ef50-130">The default is 65536.</span></span>|  
|<span data-ttu-id="1ef50-131">nazwa</span><span class="sxs-lookup"><span data-stu-id="1ef50-131">name</span></span>|<span data-ttu-id="1ef50-132">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ef50-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1ef50-133">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ef50-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1ef50-134">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ef50-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1ef50-135">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1ef50-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="1ef50-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="1ef50-136">openTimeout</span></span>|<span data-ttu-id="1ef50-137"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="1ef50-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1ef50-138">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ef50-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ef50-139">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1ef50-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="1ef50-140">port</span><span class="sxs-lookup"><span data-stu-id="1ef50-140">port</span></span>|<span data-ttu-id="1ef50-141">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzać komunikaty protokołu TCP kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="1ef50-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="1ef50-142">Ta wartość musi należeć <xref:System.Net.IPEndPoint.MinPort> do <xref:System.Net.IPEndPoint.MaxPort>zakresu od do.</span><span class="sxs-lookup"><span data-stu-id="1ef50-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="1ef50-143">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="1ef50-143">The default is 0.</span></span>|  
|<span data-ttu-id="1ef50-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="1ef50-144">receiveTimeout</span></span>|<span data-ttu-id="1ef50-145"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="1ef50-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1ef50-146">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ef50-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ef50-147">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1ef50-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="1ef50-148">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="1ef50-148">sendTimeout</span></span>|<span data-ttu-id="1ef50-149"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1ef50-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1ef50-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1ef50-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ef50-151">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1ef50-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ef50-152">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1ef50-152">Child Elements</span></span>  
  
|<span data-ttu-id="1ef50-153">Element</span><span class="sxs-lookup"><span data-stu-id="1ef50-153">Element</span></span>|<span data-ttu-id="1ef50-154">Opis</span><span class="sxs-lookup"><span data-stu-id="1ef50-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ef50-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1ef50-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="1ef50-156">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ef50-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1ef50-157">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1ef50-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="1ef50-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="1ef50-158">\<resolver></span></span>](resolver.md)|<span data-ttu-id="1ef50-159">Określa równorzędny program rozpoznawania używany przez to powiązanie do rozpoznawania identyfikatora siatki równorzędnej do adresów IP węzłów w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="1ef50-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="1ef50-160">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1ef50-160">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="1ef50-161">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1ef50-161">Defines the security settings for the message.</span></span> <span data-ttu-id="1ef50-162">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1ef50-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ef50-163">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1ef50-163">Parent Elements</span></span>  
  
|<span data-ttu-id="1ef50-164">Element</span><span class="sxs-lookup"><span data-stu-id="1ef50-164">Element</span></span>|<span data-ttu-id="1ef50-165">Opis</span><span class="sxs-lookup"><span data-stu-id="1ef50-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ef50-166">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="1ef50-166">\<bindings></span></span>](bindings.md)|<span data-ttu-id="1ef50-167">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1ef50-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ef50-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ef50-168">Remarks</span></span>  
 <span data-ttu-id="1ef50-169">To powiązanie zapewnia obsługę tworzenia aplikacji równorzędnych lub wieloczęściowych przy użyciu funkcji transportu równorzędnego za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="1ef50-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="1ef50-170">Każdy węzeł równorzędny może hostować wiele kanałów równorzędnych zdefiniowanych przy użyciu tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ef50-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef50-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ef50-171">Example</span></span>  
 <span data-ttu-id="1ef50-172">Poniższy przykład ilustruje użycie powiązania NetPeerTcpBinding, które zapewnia komunikację wieloczęściową przy użyciu kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="1ef50-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="1ef50-173">Aby zapoznać się ze szczegółowym scenariuszem korzystania z tego powiązania, zobacz [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1ef50-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ef50-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ef50-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="1ef50-175">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1ef50-175">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ef50-176">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1ef50-176">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1ef50-177">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1ef50-177">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1ef50-178">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="1ef50-178">\<binding></span></span>](../../../misc/binding.md)
- <span data-ttu-id="1ef50-179">[NET peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1ef50-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="1ef50-180">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="1ef50-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
