---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 842f2acb3be03be8171bcf7312f230fc06754511
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201045"
---
# \<netHttpsBinding>
<span data-ttu-id="442be-101">Reprezentuje powiązanie, za pomocą którego usługa Windows Communication Foundation (WCF) może skonfigurować i uwidocznić punkty końcowe, które mogą komunikować się za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="442be-101">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="442be-102">W przypadku użycia z umową dupleksową będą używane gniazda sieci Web, w przeciwnym razie będą używane połączenia HTTPS.</span><span class="sxs-lookup"><span data-stu-id="442be-102">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpsBinding>**  

## <a name="syntax"></a><span data-ttu-id="442be-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="442be-103">Syntax</span></span>  
  
```xml  
<netHttpsBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="string"
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
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a><span data-ttu-id="442be-104">Typ</span><span class="sxs-lookup"><span data-stu-id="442be-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="442be-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="442be-105">Attributes and Elements</span></span>  
 <span data-ttu-id="442be-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="442be-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="442be-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="442be-107">Attributes</span></span>  
  
|<span data-ttu-id="442be-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="442be-108">Attribute</span></span>|<span data-ttu-id="442be-109">Opis</span><span class="sxs-lookup"><span data-stu-id="442be-109">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="442be-110">Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="442be-110">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="442be-111">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="442be-111">The default is `false`.</span></span><br /><br /> <span data-ttu-id="442be-112">Tej właściwości można użyć podczas współpracy z usługami sieci Web ASMX, które korzystają z plików cookie.</span><span class="sxs-lookup"><span data-stu-id="442be-112">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="442be-113">W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="442be-113">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="442be-114">Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="442be-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="442be-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="442be-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="442be-116">Zasób internetowy jest lokalny, jeśli ma adres lokalny.</span><span class="sxs-lookup"><span data-stu-id="442be-116">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="442be-117">Adres lokalny to taki, który znajduje się na tym samym komputerze, w lokalnej sieci LAN lub intranecie i jest identyfikowany, syntaktycznie przez brak kropki (.), jak w identyfikatorach URI `http://webserver/` i `http://localhost/` .</span><span class="sxs-lookup"><span data-stu-id="442be-117">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="442be-118">Ustawienie tego atrybutu określa, czy punkty końcowe skonfigurowane za pomocą BasicHttpBinding używają serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="442be-118">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="442be-119">Jeśli ten atrybut jest `true` , żądania do lokalnych zasobów internetowych nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="442be-119">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="442be-120">Jeśli klient ma przechodzić przez serwer proxy podczas rozmowy z usługami na tym samym komputerze, gdy ten atrybut jest ustawiony na, należy użyć nazwy hosta (zamiast hosta lokalnego) `true` .</span><span class="sxs-lookup"><span data-stu-id="442be-120">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="442be-121">Gdy ten atrybut ma wartość `false` , wszystkie żądania internetowe są nawiązywane za pomocą serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="442be-121">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="442be-122"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="442be-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="442be-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="442be-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="442be-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="442be-124">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="442be-125">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="442be-125">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="442be-126">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="442be-126">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="442be-127">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="442be-127">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="442be-128">Wartość całkowita określająca maksymalną ilość pamięci przydzieloną do użytku przez Menedżera buforów komunikatów, które odbierają komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="442be-128">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="442be-129">Wartość domyślna to 524288 (0x80000) b.</span><span class="sxs-lookup"><span data-stu-id="442be-129">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="442be-130">Menedżer buforów minimalizuje koszt używania buforów przy użyciu puli buforów.</span><span class="sxs-lookup"><span data-stu-id="442be-130">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="442be-131">Bufory są wymagane do przetwarzania komunikatów przez usługę, gdy wychodzą z kanału.</span><span class="sxs-lookup"><span data-stu-id="442be-131">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="442be-132">Jeśli w puli buforów nie ma wystarczającej ilości pamięci do przetworzenia ładowania komunikatów, Menedżer buforów musi przydzielić dodatkową pamięć ze sterty CLR, co spowoduje zwiększenie nakładu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="442be-132">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="442be-133">Rozbudowana alokacja ze sterty elementów bezużytecznych CLR wskazuje, że rozmiar puli buforów jest zbyt mały i można zwiększyć wydajność z większą alokacją przez zwiększenie limitu określonego przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="442be-133">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="442be-134">Wartość całkowita, która określa maksymalny rozmiar bufora, w bajtach, który przechowuje komunikaty podczas przetwarzania dla punktu końcowego skonfigurowanego za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-134">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="442be-135">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="442be-135">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="442be-136">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, w tym nagłówki, dla wiadomości, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-136">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="442be-137">Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="442be-137">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="442be-138">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="442be-138">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="442be-139">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="442be-139">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="442be-140">Definiuje koder używany do kodowania komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="442be-140">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="442be-141">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="442be-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="442be-142">-Text: Użyj kodera wiadomości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="442be-142">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="442be-143">-MTOM: Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="442be-143">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="442be-144">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="442be-144">The default is Text.</span></span> <span data-ttu-id="442be-145">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="442be-145">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="442be-146">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="442be-147">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="442be-148">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="442be-148">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="442be-149">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="442be-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="442be-150"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="442be-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="442be-151">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="442be-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="442be-152">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="442be-152">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="442be-153">Identyfikator URI, który zawiera adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="442be-153">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="442be-154">Jeśli `useSystemWebProxy` jest ustawiona na `true` , to ustawienie musi być `null` .</span><span class="sxs-lookup"><span data-stu-id="442be-154">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="442be-155">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="442be-155">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="442be-156">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="442be-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="442be-157">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="442be-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="442be-158">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="442be-158">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="442be-159"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="442be-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="442be-160">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="442be-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="442be-161">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="442be-161">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="442be-162">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="442be-162">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="442be-163">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="442be-163">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="442be-164">-BigEndianUnicode: kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="442be-164">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="442be-165">-Unicode: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="442be-165">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="442be-166">-UTF8: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="442be-166">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="442be-167">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="442be-167">The default is UTF8.</span></span> <span data-ttu-id="442be-168">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="442be-168">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="442be-169">Prawidłowa wartość określająca <xref:System.ServiceModel.TransferMode> , czy komunikaty są buforowane, czy przesyłane strumieniowo na żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="442be-169">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="442be-170">Wartość logiczna określająca, czy ma być używany autokonfigurowany serwer proxy HTTP systemu, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="442be-170">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="442be-171">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="442be-171">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="442be-172">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="442be-172">Child Elements</span></span>  
  
|<span data-ttu-id="442be-173">Element</span><span class="sxs-lookup"><span data-stu-id="442be-173">Element</span></span>|<span data-ttu-id="442be-174">Opis</span><span class="sxs-lookup"><span data-stu-id="442be-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="442be-175">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-175">Defines the security settings for the binding.</span></span> <span data-ttu-id="442be-176">Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="442be-176">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="442be-177">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-177">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="442be-178">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="442be-178">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="442be-179">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="442be-179">Parent Elements</span></span>  
  
|<span data-ttu-id="442be-180">Element</span><span class="sxs-lookup"><span data-stu-id="442be-180">Element</span></span>|<span data-ttu-id="442be-181">Opis</span><span class="sxs-lookup"><span data-stu-id="442be-181">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="442be-182">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="442be-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="442be-183">Uwagi</span><span class="sxs-lookup"><span data-stu-id="442be-183">Remarks</span></span>  
 <span data-ttu-id="442be-184">Protokół Httpsbinding używa protokołu HTTPS jako transportu do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="442be-184">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="442be-185">W przypadku użycia z umową dupleksową będą używane gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="442be-185">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="442be-186">W przypadku użycia z kontraktem typu żądanie-odpowiedź element Httpsbinding będzie zachowywać się jak BasicHttpsBinding z koderem binarnym.</span><span class="sxs-lookup"><span data-stu-id="442be-186">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="442be-187">Zabezpieczenia są domyślnie wyłączone, ale można je dodać, ustawiając atrybut mode [\<security>](security-of-basichttpbinding.md) elementu podrzędnego na wartość inną niż `None` .</span><span class="sxs-lookup"><span data-stu-id="442be-187">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="442be-188">Domyślnie używa kodowania tekstu "text" i kodowania tekstu UTF-8.</span><span class="sxs-lookup"><span data-stu-id="442be-188">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="442be-189">Przykład</span><span class="sxs-lookup"><span data-stu-id="442be-189">Example</span></span>  
 <span data-ttu-id="442be-190">Poniższy przykład ilustruje użycie programu <xref:System.ServiceModel.NetHttpBinding> , który zapewnia komunikację https i maksymalną współdziałanie z usługami sieci Web pierwszej i drugiej generacji.</span><span class="sxs-lookup"><span data-stu-id="442be-190">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="442be-191">Powiązanie jest określone w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="442be-191">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="442be-192">Typ powiązania jest określany przy użyciu `binding` atrybutu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="442be-192">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="442be-193">Jeśli chcesz skonfigurować powiązanie podstawowe i zmienić niektóre z jego ustawień, musisz zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-193">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="442be-194">Punkt końcowy musi odwoływać się do konfiguracji powiązania przez nazwę przy użyciu `bindingConfiguration` atrybutu `<endpoint>` elementu, jak pokazano w poniższym kodzie konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="442be-194">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
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
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="442be-195">Przykład</span><span class="sxs-lookup"><span data-stu-id="442be-195">Example</span></span>  
 <span data-ttu-id="442be-196">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="442be-196">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="442be-197">Funkcję z poprzedniego przykładu można osiągnąć, usuwając bindingConfiguration z adresu punktu końcowego i nazwę z powiązania.</span><span class="sxs-lookup"><span data-stu-id="442be-197">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="442be-198">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="442be-198">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442be-199">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="442be-199">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="442be-200">Powiązania</span><span class="sxs-lookup"><span data-stu-id="442be-200">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="442be-201">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="442be-201">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="442be-202">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="442be-202">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
