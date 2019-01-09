---
title: '&lt;BasicHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: ac88a2dcb8a47876b7b8a54abc4615c851172a90
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149957"
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="97763-102">&lt;BasicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="97763-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="97763-103">Reprezentuje powiązanie, używanego przez usługi Windows Communication Foundation (WCF) do konfiguracji i ekspozycji punktów końcowych, które są w stanie komunikować się z usługami bazującymi na ASMX i klientami i innych usług, które odpowiadają WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="97763-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="97763-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="97763-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="97763-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="97763-105">\<bindings></span></span>  
<span data-ttu-id="97763-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="97763-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97763-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="97763-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           envelopeVersion="None/Soap11/Soap12"
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97763-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="97763-108">Attributes and Elements</span></span>  
 <span data-ttu-id="97763-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="97763-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97763-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="97763-110">Attributes</span></span>  
  
|<span data-ttu-id="97763-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="97763-111">Attribute</span></span>|<span data-ttu-id="97763-112">Opis</span><span class="sxs-lookup"><span data-stu-id="97763-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="97763-113">Wartość logiczna, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="97763-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="97763-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="97763-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="97763-115">Podczas interakcji z usługami sieci Web ASMX, które używają plików cookie, można użyć tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="97763-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="97763-116">W ten sposób można się upewnić, że pliki cookie, zwrócona z serwera są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.</span><span class="sxs-lookup"><span data-stu-id="97763-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="97763-117">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="97763-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="97763-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="97763-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="97763-119">Zasobu internetowego jest lokalny, jeśli ma on adresu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="97763-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="97763-120">Lokalny adres jest taki, który znajduje się na tym samym komputerze, lokalnej sieci LAN lub intranet i jest identyfikowany, składniowo, brak kropki (.) jak identyfikatory URI "http://webserver/" i "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="97763-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="97763-121">Ustawienie tego atrybutu określa, czy punkty końcowe skonfigurowane za pomocą BasicHttpBinding używać serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="97763-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="97763-122">Jeśli ten atrybut jest `true`, żądania skierowane do lokalnych zasobów Internetu należy używać serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="97763-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="97763-123">Nazwa hosta (a nie localhost), jeśli chcesz, aby klienci przechodzić przez serwer proxy, w przypadku usług na tym samym komputerze, gdy ten atrybut jest ustawiony na użycie `true`.</span><span class="sxs-lookup"><span data-stu-id="97763-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="97763-124">Jeśli ten atrybut jest `false`, wszystkie żądania internetowe są nawiązywane przy użyciu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="97763-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="97763-125">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="97763-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="97763-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97763-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97763-127">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="97763-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="97763-128">Określa wersję protokołu SOAP używaną dla komunikatów przetwarzanych przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="97763-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="97763-129">Jedyna prawidłowa wartość to Soap11.</span><span class="sxs-lookup"><span data-stu-id="97763-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="97763-130">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="97763-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="97763-131">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="97763-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="97763-132">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="97763-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="97763-133">Wartość całkowitą, która określa maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="97763-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="97763-134">Wartość domyślna to 524288 (0x80000) bajtów.</span><span class="sxs-lookup"><span data-stu-id="97763-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="97763-135">Menedżera buforów minimalizuje koszty za pomocą buforów przy użyciu puli buforów.</span><span class="sxs-lookup"><span data-stu-id="97763-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="97763-136">Bufory są wymagane do przetwarzania komunikatów przez usługę w przypadku, gdy pochodzą one z kanału.</span><span class="sxs-lookup"><span data-stu-id="97763-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="97763-137">Jeśli w puli buforów w celu przetworzenia obciążenia wiadomości nie jest wystarczająca ilość pamięci, menedżera buforów musi przydzielić dodatkową pamięć ze stosu CLR, co zwiększa wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97763-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="97763-138">Rozbudowane alokacji w stercie wyrzucania elementów CLR jest wskazanie, że rozmiar puli buforów jest za mały i że można poprawić wydajność z większych alokacji, zwiększając limit określony przez atrybut.</span><span class="sxs-lookup"><span data-stu-id="97763-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="97763-139">Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania na punkt końcowy skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="97763-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="97763-140">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="97763-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="97763-141">Dodatnia liczba całkowita określająca maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="97763-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="97763-142">Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="97763-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="97763-143">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="97763-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="97763-144">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="97763-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="97763-145">Definiuje encoder umożliwia kodowanie komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="97763-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="97763-146">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="97763-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="97763-147">-Tekst: Za pomocą kodera komunikatów tekstu.</span><span class="sxs-lookup"><span data-stu-id="97763-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="97763-148">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="97763-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="97763-149">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="97763-149">The default is Text.</span></span> <span data-ttu-id="97763-150">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="97763-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="97763-151">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="97763-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="97763-152">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="97763-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="97763-153">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="97763-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="97763-154">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="97763-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="97763-155">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="97763-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="97763-156">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="97763-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="97763-157">Określa przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="97763-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="97763-158">Wartość domyślna to "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="97763-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="97763-159">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="97763-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="97763-160">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="97763-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="97763-161">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97763-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97763-162">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="97763-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="97763-163">Identyfikator URI, który zawiera adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="97763-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="97763-164">Jeśli `useSystemWebProxy` ustawiono `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="97763-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="97763-165">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="97763-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="97763-166">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="97763-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="97763-167">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97763-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97763-168">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="97763-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="97763-169">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="97763-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="97763-170">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97763-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97763-171">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="97763-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="97763-172">Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="97763-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="97763-173">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="97763-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="97763-174">-BigEndianUnicode: Unicode BigEndian kodowania.</span><span class="sxs-lookup"><span data-stu-id="97763-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="97763-175">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="97763-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="97763-176">-UTF8: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="97763-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="97763-177">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="97763-177">The default is UTF8.</span></span> <span data-ttu-id="97763-178">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="97763-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="97763-179">Nieprawidłowy <xref:System.ServiceModel.TransferMode> wartość określającą, czy komunikaty są buforowane, czy strumieniowo na żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="97763-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="97763-180">Wartość logiczna określająca, czy automatycznie skonfigurowany serwer proxy HTTP systemu powinien być używany, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="97763-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="97763-181">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="97763-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97763-182">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="97763-182">Child Elements</span></span>  
  
|<span data-ttu-id="97763-183">Element</span><span class="sxs-lookup"><span data-stu-id="97763-183">Element</span></span>|<span data-ttu-id="97763-184">Opis</span><span class="sxs-lookup"><span data-stu-id="97763-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97763-185">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="97763-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="97763-186">Definiuje ustawienia zabezpieczeń dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="97763-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="97763-187">Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="97763-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="97763-188">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="97763-188">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="97763-189">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="97763-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="97763-190">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="97763-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97763-191">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="97763-191">Parent Elements</span></span>  
  
|<span data-ttu-id="97763-192">Element</span><span class="sxs-lookup"><span data-stu-id="97763-192">Element</span></span>|<span data-ttu-id="97763-193">Opis</span><span class="sxs-lookup"><span data-stu-id="97763-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97763-194">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="97763-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="97763-195">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="97763-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97763-196">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97763-196">Remarks</span></span>  
 <span data-ttu-id="97763-197">BasicHttpBinding korzysta z protokołu HTTP jako transportu do wysyłania wiadomości SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="97763-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="97763-198">Usługa może używać tego powiązania do uwidaczniają punkty końcowe, które odpowiadają WS-I najlepszych praktyk w zakresie 1.1, takich jak te, które zużywają ASMX klientów.</span><span class="sxs-lookup"><span data-stu-id="97763-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="97763-199">Podobnie, klient może używać BasicHttpBinding do komunikowania się z usługi ujawniające punktów końcowych, które odpowiadają WS-I najlepszych praktyk w zakresie 1.1, takich jak usługi sieci Web ASMX lub usługi, które skonfigurowano BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="97763-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="97763-200">Zabezpieczenia jest domyślnie wyłączona, ale można dodać ustawienie atrybutu tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) element podrzędny, wartość inną niż `None`.</span><span class="sxs-lookup"><span data-stu-id="97763-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="97763-201">Używa ona "Text" kodowania i UTF-8 tekst komunikatu kodowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="97763-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97763-202">Przykład</span><span class="sxs-lookup"><span data-stu-id="97763-202">Example</span></span>  
 <span data-ttu-id="97763-203">W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.BasicHttpBinding> zapewniający HTTP komunikacji i maksymalnie współdziałanie z pierwszym — i second - generation usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="97763-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="97763-204">Powiązanie jest określona w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="97763-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="97763-205">Typ powiązania jest określony, przy użyciu `binding` atrybutu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="97763-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="97763-206">Jeśli chcesz skonfigurować podstawowe powiązanie i zmienić niektóre z jego ustawienia, należy zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="97763-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="97763-207">Punkt końcowy musi odwoływać się do konfiguracji powiązania według nazwy przy użyciu `bindingConfiguration` atrybutu `<endpoint>` elementu, jak pokazano w poniższym kodzie konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="97763-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="97763-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="97763-208">Example</span></span>  
 <span data-ttu-id="97763-209">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="97763-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="97763-210">Funkcje z poprzedniego przykładu, można osiągnąć, usuwając bindingConfiguration z adresu punktu końcowego, a nazwa z wiązania.</span><span class="sxs-lookup"><span data-stu-id="97763-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="97763-211">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="97763-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97763-212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97763-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="97763-213">Powiązania</span><span class="sxs-lookup"><span data-stu-id="97763-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="97763-214">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="97763-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="97763-215">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="97763-215">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="97763-216">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="97763-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
