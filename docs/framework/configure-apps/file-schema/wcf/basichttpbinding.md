---
title: '&lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7842efe074d5487a5917e7ee669027a420d9d713
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="537da-102">&lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="537da-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="537da-103">Reprezentuje powiązanie, które [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi można użyć do konfiguracji i ekspozycji punktów końcowych, które są w stanie komunikować się z usługami sieciowymi bazującymi na ASMX i klientami i innych usług, które odpowiadają WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="537da-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="537da-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="537da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="537da-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="537da-105">\<bindings></span></span>  
<span data-ttu-id="537da-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="537da-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="537da-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="537da-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
              name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="537da-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="537da-108">Attributes and Elements</span></span>  
 <span data-ttu-id="537da-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="537da-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="537da-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="537da-110">Attributes</span></span>  
  
|<span data-ttu-id="537da-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="537da-111">Attribute</span></span>|<span data-ttu-id="537da-112">Opis</span><span class="sxs-lookup"><span data-stu-id="537da-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="537da-113">Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="537da-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="537da-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="537da-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="537da-115">Tej właściwości można użyć w przypadku interakcji z usługami sieci Web ASMX, które używają plików cookie.</span><span class="sxs-lookup"><span data-stu-id="537da-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="537da-116">W ten sposób można się upewnić, że pliki cookie zwrócony z serwera, automatycznie są kopiowane do wszystkich przyszłych żądań dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="537da-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="537da-117">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="537da-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="537da-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="537da-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="537da-119">Zasobu internetowego jest lokalny, jeśli ma ona adresu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="537da-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="537da-120">Lokalny adres jest taki, który znajduje się na tym samym komputerze, lokalnej sieci LAN lub intranet i jest identyfikowany, składniowo, brak kropki (.) jak identyfikatory URI "http://webserver/" i "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="537da-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="537da-121">Ustawienie ten atrybut określa, czy punkty końcowe skonfigurowane z BasicHttpBinding Użyj serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="537da-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="537da-122">Jeśli ten atrybut jest `true`, żądań lokalnych zasobów w Internecie, nie należy używać serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="537da-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="537da-123">Użyj hosta nazw (zamiast localhost), jeśli klienci mają przechodzić przez serwer proxy po rozmowie z usługi na tym samym komputerze, gdy ten atrybut ma ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="537da-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="537da-124">Jeśli ten atrybut jest `false`, wszystkie żądania internetowe są nawiązywane przy użyciu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="537da-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="537da-125">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="537da-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="537da-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="537da-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="537da-127">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="537da-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="537da-128">Określa wersję SOAP używaną dla komunikatów przetwarzanych przez to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="537da-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="537da-129">Jedyne prawidłowe wartości to Soap11.</span><span class="sxs-lookup"><span data-stu-id="537da-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="537da-130">Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="537da-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="537da-131">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="537da-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="537da-132">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.</span><span class="sxs-lookup"><span data-stu-id="537da-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="537da-133">Wartość całkowita określająca maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="537da-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="537da-134">Wartość domyślna to 524288 (0x80000) bajtów.</span><span class="sxs-lookup"><span data-stu-id="537da-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="537da-135">Menedżera buforów minimalizację kosztów bufory przy użyciu puli bufora.</span><span class="sxs-lookup"><span data-stu-id="537da-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="537da-136">Bufory są wymagane do przetwarzania komunikatów przez usługę, po znalezieniu poza kanału.</span><span class="sxs-lookup"><span data-stu-id="537da-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="537da-137">Jeśli w puli buforów do przetworzenia obciążenia komunikat nie ma wystarczającej ilości pamięci, menedżera buforów musi przydzielić dodatkową pamięć sterty CLR, co zwiększa obciążenie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="537da-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="537da-138">Rozbudowana alokacji sterty pamięci CLR jest wskazanie, że rozmiar puli buforów jest za mały, i że można poprawić wydajność z alokacją większych przez odpowiednie zwiększenie limitu określonego przez tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="537da-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="537da-139">Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania dla punkt końcowy skonfigurowany dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="537da-140">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="537da-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="537da-141">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="537da-142">Nadawca otrzymuje błędu protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="537da-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="537da-143">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="537da-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="537da-144">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="537da-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="537da-145">Definiuje koder używany do kodowania komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="537da-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="537da-146">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="537da-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="537da-147">-Tekst: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="537da-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="537da-148">-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="537da-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="537da-149">Wartość domyślna to tekst.</span><span class="sxs-lookup"><span data-stu-id="537da-149">The default is Text.</span></span> <span data-ttu-id="537da-150">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="537da-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="537da-151">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="537da-152">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="537da-153">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="537da-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="537da-154">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="537da-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="537da-155">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="537da-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="537da-156">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="537da-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="537da-157">Określa przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="537da-158">Wartość domyślna to "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="537da-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="537da-159">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="537da-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="537da-160">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="537da-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="537da-161">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="537da-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="537da-162">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="537da-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="537da-163">Identyfikator URI zawierający adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="537da-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="537da-164">Jeśli `useSystemWebProxy` ustawiono `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="537da-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="537da-165">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="537da-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="537da-166">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="537da-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="537da-167">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="537da-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="537da-168">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="537da-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="537da-169">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="537da-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="537da-170">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="537da-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="537da-171">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="537da-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="537da-172">Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="537da-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="537da-173">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="537da-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="537da-174">-BigEndianUnicode: Unicode BigEndian kodowanie.</span><span class="sxs-lookup"><span data-stu-id="537da-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="537da-175">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="537da-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="537da-176">-UTF8: 8-bitowego kodowania o</span><span class="sxs-lookup"><span data-stu-id="537da-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="537da-177">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="537da-177">The default is UTF8.</span></span> <span data-ttu-id="537da-178">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="537da-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="537da-179">Prawidłowy <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane, czy strumieniowego na żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="537da-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="537da-180">Wartość logiczna określająca, czy ma być używane automatycznie skonfigurowany serwer proxy HTTP systemu, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="537da-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="537da-181">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="537da-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="537da-182">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="537da-182">Child Elements</span></span>  
  
|<span data-ttu-id="537da-183">Element</span><span class="sxs-lookup"><span data-stu-id="537da-183">Element</span></span>|<span data-ttu-id="537da-184">Opis</span><span class="sxs-lookup"><span data-stu-id="537da-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="537da-185">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="537da-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="537da-186">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="537da-187">Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="537da-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="537da-188">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="537da-188">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="537da-189">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="537da-190">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="537da-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="537da-191">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="537da-191">Parent Elements</span></span>  
  
|<span data-ttu-id="537da-192">Element</span><span class="sxs-lookup"><span data-stu-id="537da-192">Element</span></span>|<span data-ttu-id="537da-193">Opis</span><span class="sxs-lookup"><span data-stu-id="537da-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="537da-194">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="537da-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="537da-195">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="537da-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="537da-196">Uwagi</span><span class="sxs-lookup"><span data-stu-id="537da-196">Remarks</span></span>  
 <span data-ttu-id="537da-197">BasicHttpBinding korzysta z protokołu HTTP jako transportu do wysyłania wiadomości SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="537da-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="537da-198">Usługa może używać tego powiązania do udostępnienia punktów końcowych, które są zgodne ze standardem WS-I BP 1.1, takimi jak korzystać z klientów ASMX.</span><span class="sxs-lookup"><span data-stu-id="537da-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="537da-199">Podobnie, klient może używać BasicHttpBinding do komunikowania się z usługami Udostępnianie punktów końcowych, które są zgodne ze standardem WS-I BP 1.1, takich jak usługi sieci Web ASMX lub usługi skonfigurowano BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="537da-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="537da-200">Zabezpieczenia jest domyślnie wyłączona, ale można dodać ustawienie atrybutu tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) element podrzędny, wartość inną niż `None`.</span><span class="sxs-lookup"><span data-stu-id="537da-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="537da-201">Używa tekst kodowania i UTF-8 komunikatu "Text" kodowaniu.</span><span class="sxs-lookup"><span data-stu-id="537da-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="537da-202">Przykład</span><span class="sxs-lookup"><span data-stu-id="537da-202">Example</span></span>  
 <span data-ttu-id="537da-203">W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.BasicHttpBinding> zapewnia współdziałanie komunikacji i maksymalnie HTTP z pierwszej - i second - generation usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="537da-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="537da-204">Powiązanie jest określona w plikach konfiguracji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="537da-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="537da-205">Typ powiązania jest określona za pomocą `binding` atrybutu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="537da-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="537da-206">Jeśli chcesz skonfigurować podstawowe powiązanie i zmieniania jego ustawień należy zdefiniować konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="537da-207">Punkt końcowy musi odwoływać się Konfiguracja powiązania o nazwie przy użyciu `bindingConfiguration` atrybutu `<endpoint>` element, jak pokazano w poniższym kodzie konfiguracji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="537da-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
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
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="537da-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="537da-208">Example</span></span>  
 <span data-ttu-id="537da-209">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="537da-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="537da-210">Funkcje z poprzednim przykładzie można osiągnąć przez usunięcie bindingConfiguration z adres punktu końcowego i frm nazwę powiązania.</span><span class="sxs-lookup"><span data-stu-id="537da-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
        <binding   
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
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="537da-211">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="537da-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537da-212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="537da-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="537da-213">Powiązania</span><span class="sxs-lookup"><span data-stu-id="537da-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="537da-214">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="537da-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="537da-215">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="537da-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="537da-216">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="537da-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
