---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 48d7e10eddbf3ed2e2bfe3d04566d37ead5a1e04
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400146"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="f6975-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f6975-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="f6975-102">Definiuje powiązanie dla obsługi komunikatów TCP określonego kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f6975-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
<span data-ttu-id="f6975-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f6975-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f6975-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f6975-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f6975-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f6975-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f6975-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netPeerTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="f6975-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6975-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6975-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6975-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6975-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f6975-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f6975-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6975-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6975-110">Attributes</span></span>  
  
|<span data-ttu-id="f6975-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6975-111">Attribute</span></span>|<span data-ttu-id="f6975-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f6975-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6975-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f6975-113">closeTimeout</span></span>|<span data-ttu-id="f6975-114"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="f6975-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f6975-115">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6975-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6975-116">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6975-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f6975-117">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="f6975-117">listenIPAddress</span></span>|<span data-ttu-id="f6975-118">Ciąg określający adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="f6975-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="f6975-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="f6975-119">The default is `null`.</span></span>|  
|<span data-ttu-id="f6975-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f6975-120">maxBufferPoolSize</span></span>|<span data-ttu-id="f6975-121">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6975-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="f6975-122">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="f6975-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="f6975-123">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="f6975-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="f6975-124">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="f6975-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f6975-125">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f6975-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f6975-126">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="f6975-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="f6975-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f6975-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="f6975-128">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6975-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f6975-129">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f6975-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="f6975-130">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f6975-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f6975-131">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="f6975-131">The default is 65536.</span></span>|  
|<span data-ttu-id="f6975-132">nazwa</span><span class="sxs-lookup"><span data-stu-id="f6975-132">name</span></span>|<span data-ttu-id="f6975-133">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6975-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f6975-134">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6975-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f6975-135">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="f6975-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f6975-136">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6975-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="f6975-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f6975-137">openTimeout</span></span>|<span data-ttu-id="f6975-138"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="f6975-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f6975-139">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6975-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6975-140">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6975-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f6975-141">port</span><span class="sxs-lookup"><span data-stu-id="f6975-141">port</span></span>|<span data-ttu-id="f6975-142">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzać komunikaty protokołu TCP kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f6975-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="f6975-143">Ta wartość musi należeć <xref:System.Net.IPEndPoint.MinPort> do <xref:System.Net.IPEndPoint.MaxPort>zakresu od do.</span><span class="sxs-lookup"><span data-stu-id="f6975-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="f6975-144">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="f6975-144">The default is 0.</span></span>|  
|<span data-ttu-id="f6975-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f6975-145">receiveTimeout</span></span>|<span data-ttu-id="f6975-146"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="f6975-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f6975-147">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6975-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6975-148">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f6975-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="f6975-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f6975-149">sendTimeout</span></span>|<span data-ttu-id="f6975-150"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="f6975-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f6975-151">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6975-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6975-152">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6975-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6975-153">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6975-153">Child Elements</span></span>  
  
|<span data-ttu-id="f6975-154">Element</span><span class="sxs-lookup"><span data-stu-id="f6975-154">Element</span></span>|<span data-ttu-id="f6975-155">Opis</span><span class="sxs-lookup"><span data-stu-id="f6975-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6975-156">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f6975-156">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="f6975-157">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6975-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f6975-158">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f6975-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="f6975-159">\<resolver></span><span class="sxs-lookup"><span data-stu-id="f6975-159">\<resolver></span></span>](resolver.md)|<span data-ttu-id="f6975-160">Określa równorzędny program rozpoznawania używany przez to powiązanie do rozpoznawania identyfikatora siatki równorzędnej do adresów IP węzłów w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="f6975-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="f6975-161">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f6975-161">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="f6975-162">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f6975-162">Defines the security settings for the message.</span></span> <span data-ttu-id="f6975-163">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f6975-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6975-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6975-164">Parent Elements</span></span>  
  
|<span data-ttu-id="f6975-165">Element</span><span class="sxs-lookup"><span data-stu-id="f6975-165">Element</span></span>|<span data-ttu-id="f6975-166">Opis</span><span class="sxs-lookup"><span data-stu-id="f6975-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6975-167">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="f6975-167">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f6975-168">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f6975-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6975-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6975-169">Remarks</span></span>  
 <span data-ttu-id="f6975-170">To powiązanie zapewnia obsługę tworzenia aplikacji równorzędnych lub wieloczęściowych przy użyciu funkcji transportu równorzędnego za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="f6975-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="f6975-171">Każdy węzeł równorzędny może hostować wiele kanałów równorzędnych zdefiniowanych przy użyciu tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6975-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6975-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6975-172">Example</span></span>  
 <span data-ttu-id="f6975-173">Poniższy przykład ilustruje użycie powiązania NetPeerTcpBinding, które zapewnia komunikację wieloczęściową przy użyciu kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f6975-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="f6975-174">Aby zapoznać się ze szczegółowym scenariuszem korzystania z tego powiązania, zobacz [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f6975-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6975-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6975-175">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="f6975-176">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f6975-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f6975-177">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f6975-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f6975-178">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f6975-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f6975-179">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f6975-179">\<binding></span></span>](../../../misc/binding.md)
- <span data-ttu-id="f6975-180">[NET peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f6975-180">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="f6975-181">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="f6975-181">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
