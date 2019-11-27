---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: f1be0997fc7b2b884c7ec90ea6a02ea0af96ab4c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431025"
---
# <a name="basichttpbinding"></a><span data-ttu-id="22394-101">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="22394-101">\<basicHttpBinding></span></span>
<span data-ttu-id="22394-102">Reprezentuje powiązanie, za pomocą którego usługa Windows Communication Foundation (WCF) może skonfigurować i uwidocznić punkty końcowe, które mogą komunikować się z usługami sieci Web opartymi na usłudze ASMX i klientami oraz innymi usługami, które są zgodne ze standardem WS-I Basic Profile 1,1.</span><span class="sxs-lookup"><span data-stu-id="22394-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
<span data-ttu-id="22394-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22394-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22394-104">&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="22394-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="22394-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="22394-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="22394-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<basicHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="22394-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22394-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="22394-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22394-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="22394-108">Attributes and Elements</span></span>  
 <span data-ttu-id="22394-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="22394-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22394-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="22394-110">Attributes</span></span>  
  
|<span data-ttu-id="22394-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="22394-111">Attribute</span></span>|<span data-ttu-id="22394-112">Opis</span><span class="sxs-lookup"><span data-stu-id="22394-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="22394-113">Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="22394-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="22394-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="22394-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="22394-115">Tej właściwości można użyć podczas współpracy z usługami sieci Web ASMX, które korzystają z plików cookie.</span><span class="sxs-lookup"><span data-stu-id="22394-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="22394-116">W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="22394-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="22394-117">Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="22394-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="22394-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="22394-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="22394-119">Zasób internetowy jest lokalny, jeśli ma adres lokalny.</span><span class="sxs-lookup"><span data-stu-id="22394-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="22394-120">Adres lokalny to taki, który znajduje się na tym samym komputerze, lokalna sieć LAN lub intranet i jest identyfikowany, syntaktycznie przez brak kropki (.), jak w identyfikatorach URI "http://webserver/" i "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="22394-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="22394-121">Ustawienie tego atrybutu określa, czy punkty końcowe skonfigurowane za pomocą BasicHttpBinding używają serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="22394-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="22394-122">Jeśli ten atrybut jest `true`, żądania do lokalnych zasobów internetowych nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="22394-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="22394-123">Jeśli klient ma przechodzić przez serwer proxy podczas rozmowy z usługami na tym samym komputerze, gdy ten atrybut jest ustawiony na `true`, należy użyć nazwy hosta (zamiast hosta lokalnego).</span><span class="sxs-lookup"><span data-stu-id="22394-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="22394-124">Gdy ten atrybut jest `false`, wszystkie żądania internetowe są nawiązywane za pomocą serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="22394-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="22394-125">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="22394-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="22394-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22394-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22394-127">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="22394-127">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="22394-128">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="22394-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="22394-129">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="22394-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="22394-130">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="22394-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="22394-131">Wartość całkowita określająca maksymalną ilość pamięci przydzieloną do użytku przez Menedżera buforów komunikatów, które odbierają komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="22394-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="22394-132">Wartość domyślna to 524288 (0x80000) b.</span><span class="sxs-lookup"><span data-stu-id="22394-132">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="22394-133">Menedżer buforów minimalizuje koszt używania buforów przy użyciu puli buforów.</span><span class="sxs-lookup"><span data-stu-id="22394-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="22394-134">Bufory są wymagane do przetwarzania komunikatów przez usługę, gdy wychodzą z kanału.</span><span class="sxs-lookup"><span data-stu-id="22394-134">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="22394-135">Jeśli w puli buforów nie ma wystarczającej ilości pamięci do przetworzenia ładowania komunikatów, Menedżer buforów musi przydzielić dodatkową pamięć ze sterty CLR, co spowoduje zwiększenie nakładu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="22394-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="22394-136">Rozbudowana alokacja ze sterty elementów bezużytecznych CLR wskazuje, że rozmiar puli buforów jest zbyt mały i można zwiększyć wydajność z większą alokacją przez zwiększenie limitu określonego przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="22394-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="22394-137">Wartość całkowita, która określa maksymalny rozmiar bufora, w bajtach, który przechowuje komunikaty podczas przetwarzania dla punktu końcowego skonfigurowanego za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="22394-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="22394-138">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="22394-138">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="22394-139">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, w tym nagłówki, dla wiadomości, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="22394-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="22394-140">Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="22394-140">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="22394-141">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="22394-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="22394-142">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="22394-142">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="22394-143">Definiuje koder używany do kodowania komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="22394-143">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="22394-144">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="22394-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22394-145">-Text: Użyj kodera wiadomości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="22394-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="22394-146">-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="22394-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="22394-147">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="22394-147">The default is Text.</span></span> <span data-ttu-id="22394-148">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="22394-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="22394-149">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="22394-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="22394-150">Ta wartość powinna być unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="22394-150">This value should be unique among bindings of the same type.</span></span> <span data-ttu-id="22394-151">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="22394-151">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="22394-152">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="22394-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="22394-153">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="22394-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="22394-154">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22394-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22394-155">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="22394-155">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="22394-156">Identyfikator URI, który zawiera adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="22394-156">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="22394-157">Jeśli `useSystemWebProxy` jest ustawiona na `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="22394-157">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="22394-158">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="22394-158">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="22394-159">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="22394-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="22394-160">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22394-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22394-161">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="22394-161">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="22394-162">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="22394-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="22394-163">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22394-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22394-164">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="22394-164">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="22394-165">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="22394-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="22394-166">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="22394-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22394-167">-BigEndianUnicode: kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="22394-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="22394-168">-Unicode: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="22394-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="22394-169">-UTF8: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="22394-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="22394-170">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="22394-170">The default is UTF8.</span></span> <span data-ttu-id="22394-171">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="22394-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="22394-172">Prawidłowa <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane, czy przesyłane strumieniowo na żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="22394-172">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="22394-173">Wartość logiczna określająca, czy ma być używany autokonfigurowany serwer proxy HTTP systemu, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="22394-173">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="22394-174">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="22394-174">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22394-175">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="22394-175">Child Elements</span></span>  
  
|<span data-ttu-id="22394-176">Element</span><span class="sxs-lookup"><span data-stu-id="22394-176">Element</span></span>|<span data-ttu-id="22394-177">Opis</span><span class="sxs-lookup"><span data-stu-id="22394-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22394-178">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="22394-178">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="22394-179">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="22394-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="22394-180">Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="22394-180">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="22394-181">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="22394-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="22394-182">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="22394-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="22394-183">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="22394-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22394-184">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22394-184">Parent Elements</span></span>  
  
|<span data-ttu-id="22394-185">Element</span><span class="sxs-lookup"><span data-stu-id="22394-185">Element</span></span>|<span data-ttu-id="22394-186">Opis</span><span class="sxs-lookup"><span data-stu-id="22394-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22394-187">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="22394-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="22394-188">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="22394-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22394-189">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22394-189">Remarks</span></span>  
 <span data-ttu-id="22394-190">BasicHttpBinding używa protokołu HTTP jako transportu do wysyłania komunikatów protokołu SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="22394-190">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="22394-191">Usługa może użyć tego powiązania, aby uwidocznić punkty końcowe, które są zgodne z usługą WS-I BP 1,1, taką jak te, które są używane przez klientów w ASMX.</span><span class="sxs-lookup"><span data-stu-id="22394-191">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="22394-192">Podobnie klient może używać BasicHttpBinding do komunikowania się z usługami, które udostępniają punkty końcowe, które są zgodne z usługą WS-I BP 1,1, na przykład w przypadku usług sieci Web, które są skonfigurowane z BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="22394-192">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="22394-193">Zabezpieczenia są domyślnie wyłączone, ale można dodać ustawienie atrybut Mode elementu podrzędnego [\<zabezpieczenia >](security-of-basichttpbinding.md) , do wartości innej niż `None`.</span><span class="sxs-lookup"><span data-stu-id="22394-193">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="22394-194">Domyślnie używa kodowania tekstu "text" i kodowania tekstu UTF-8.</span><span class="sxs-lookup"><span data-stu-id="22394-194">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22394-195">Przykład</span><span class="sxs-lookup"><span data-stu-id="22394-195">Example</span></span>  
 <span data-ttu-id="22394-196">Poniższy przykład ilustruje użycie <xref:System.ServiceModel.BasicHttpBinding>, który zapewnia komunikację HTTP i maksymalną współdziałanie z usługami sieci Web pierwszej i drugiej generacji.</span><span class="sxs-lookup"><span data-stu-id="22394-196">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="22394-197">Powiązanie jest określone w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="22394-197">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="22394-198">Typ powiązania jest określony przy użyciu atrybutu `binding` elementu `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="22394-198">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="22394-199">Jeśli chcesz skonfigurować powiązanie podstawowe i zmienić niektóre z jego ustawień, musisz zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="22394-199">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="22394-200">Punkt końcowy musi odwoływać się do konfiguracji powiązania przez nazwę przy użyciu atrybutu `bindingConfiguration` elementu `<endpoint>`, jak pokazano w poniższym kodzie konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="22394-200">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="22394-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="22394-201">Example</span></span>  
 <span data-ttu-id="22394-202">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="22394-202">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="22394-203">Funkcję z poprzedniego przykładu można osiągnąć, usuwając bindingConfiguration z adresu punktu końcowego i nazwę z powiązania.</span><span class="sxs-lookup"><span data-stu-id="22394-203">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="22394-204">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="22394-204">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22394-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22394-205">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="22394-206">Powiązania</span><span class="sxs-lookup"><span data-stu-id="22394-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="22394-207">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="22394-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="22394-208">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="22394-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="22394-209">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="22394-209">\<binding></span></span>](bindings.md)
