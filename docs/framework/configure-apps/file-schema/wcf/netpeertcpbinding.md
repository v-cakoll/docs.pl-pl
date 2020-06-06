---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140730"
---
# \<netPeerTcpBinding>
<span data-ttu-id="d0796-101">Definiuje powiązanie dla obsługi komunikatów TCP określonego kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="d0796-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="d0796-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0796-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0796-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d0796-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d0796-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0796-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0796-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0796-105">Attributes</span></span>  
  
|<span data-ttu-id="d0796-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d0796-106">Attribute</span></span>|<span data-ttu-id="d0796-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d0796-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0796-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="d0796-108">closeTimeout</span></span>|<span data-ttu-id="d0796-109"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="d0796-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d0796-110">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0796-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0796-111">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d0796-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d0796-112">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="d0796-112">listenIPAddress</span></span>|<span data-ttu-id="d0796-113">Ciąg określający adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="d0796-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="d0796-114">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="d0796-114">The default is `null`.</span></span>|  
|<span data-ttu-id="d0796-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d0796-115">maxBufferPoolSize</span></span>|<span data-ttu-id="d0796-116">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0796-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="d0796-117">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="d0796-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="d0796-118">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="d0796-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="d0796-119">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="d0796-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d0796-120">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="d0796-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d0796-121">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="d0796-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="d0796-122">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="d0796-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="d0796-123">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0796-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d0796-124">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d0796-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="d0796-125">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d0796-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d0796-126">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="d0796-126">The default is 65536.</span></span>|  
|<span data-ttu-id="d0796-127">name</span><span class="sxs-lookup"><span data-stu-id="d0796-127">name</span></span>|<span data-ttu-id="d0796-128">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0796-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d0796-129">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0796-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d0796-130">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="d0796-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d0796-131">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d0796-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="d0796-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="d0796-132">openTimeout</span></span>|<span data-ttu-id="d0796-133"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="d0796-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d0796-134">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0796-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0796-135">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d0796-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d0796-136">port</span><span class="sxs-lookup"><span data-stu-id="d0796-136">port</span></span>|<span data-ttu-id="d0796-137">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzać komunikaty protokołu TCP kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="d0796-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="d0796-138">Ta wartość musi należeć <xref:System.Net.IPEndPoint.MinPort> do zakresu od do <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="d0796-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="d0796-139">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="d0796-139">The default is 0.</span></span>|  
|<span data-ttu-id="d0796-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="d0796-140">receiveTimeout</span></span>|<span data-ttu-id="d0796-141">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="d0796-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d0796-142">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0796-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0796-143">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="d0796-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="d0796-144">Właściwości SendTimeout</span><span class="sxs-lookup"><span data-stu-id="d0796-144">sendTimeout</span></span>|<span data-ttu-id="d0796-145"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="d0796-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d0796-146">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="d0796-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0796-147">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d0796-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0796-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d0796-148">Child Elements</span></span>  
  
|<span data-ttu-id="d0796-149">Element</span><span class="sxs-lookup"><span data-stu-id="d0796-149">Element</span></span>|<span data-ttu-id="d0796-150">Opis</span><span class="sxs-lookup"><span data-stu-id="d0796-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="d0796-151">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0796-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d0796-152">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="d0796-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="d0796-153">Określa równorzędny program rozpoznawania używany przez to powiązanie do rozpoznawania identyfikatora siatki równorzędnej do adresów IP węzłów w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="d0796-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="d0796-154">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0796-154">Defines the security settings for the message.</span></span> <span data-ttu-id="d0796-155">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="d0796-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0796-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d0796-156">Parent Elements</span></span>  
  
|<span data-ttu-id="d0796-157">Element</span><span class="sxs-lookup"><span data-stu-id="d0796-157">Element</span></span>|<span data-ttu-id="d0796-158">Opis</span><span class="sxs-lookup"><span data-stu-id="d0796-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="d0796-159">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d0796-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0796-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0796-160">Remarks</span></span>  
 <span data-ttu-id="d0796-161">To powiązanie zapewnia obsługę tworzenia aplikacji równorzędnych lub wieloczęściowych przy użyciu funkcji transportu równorzędnego za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="d0796-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="d0796-162">Każdy węzeł równorzędny może hostować wiele kanałów równorzędnych zdefiniowanych przy użyciu tego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0796-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0796-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0796-163">Example</span></span>  
 <span data-ttu-id="d0796-164">Poniższy przykład ilustruje użycie powiązania NetPeerTcpBinding, które zapewnia komunikację wieloczęściową przy użyciu kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="d0796-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="d0796-165">Aby zapoznać się ze szczegółowym scenariuszem korzystania z tego powiązania, zobacz [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d0796-165">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0796-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0796-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="d0796-167">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d0796-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d0796-168">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d0796-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d0796-169">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d0796-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="d0796-170">[NET peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d0796-170">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="d0796-171">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="d0796-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
