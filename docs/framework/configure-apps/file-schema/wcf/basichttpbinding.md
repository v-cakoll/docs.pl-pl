---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 861840f574c80f282198775272eff149b84c6fca
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289734"
---
# <a name="basichttpbinding"></a><span data-ttu-id="b9820-101">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b9820-101">\<basicHttpBinding></span></span>
<span data-ttu-id="b9820-102">Reprezentuje powiązanie, używanego przez usługi Windows Communication Foundation (WCF) do konfiguracji i ekspozycji punktów końcowych, które są w stanie komunikować się z usługami bazującymi na ASMX i klientami i innych usług, które odpowiadają WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="b9820-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="b9820-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b9820-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9820-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b9820-104">\<bindings></span></span>  
<span data-ttu-id="b9820-105">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b9820-105">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9820-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9820-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9820-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b9820-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b9820-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b9820-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9820-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9820-109">Attributes</span></span>  
  
|<span data-ttu-id="b9820-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b9820-110">Attribute</span></span>|<span data-ttu-id="b9820-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b9820-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="b9820-112">Wartość logiczna, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="b9820-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="b9820-113">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b9820-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b9820-114">Podczas interakcji z usługami sieci Web ASMX, które używają plików cookie, można użyć tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="b9820-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="b9820-115">W ten sposób można się upewnić, że pliki cookie, zwrócona z serwera są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.</span><span class="sxs-lookup"><span data-stu-id="b9820-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="b9820-116">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="b9820-116">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b9820-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b9820-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b9820-118">Zasobu internetowego jest lokalny, jeśli ma on adresu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b9820-118">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="b9820-119">Lokalny adres jest taki, który znajduje się na tym samym komputerze, lokalnej sieci LAN lub intranet i jest identyfikowany, składniowo, brak kropki (.) jak identyfikatory URI "http://webserver/" i "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="b9820-119">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="b9820-120">Ustawienie tego atrybutu określa, czy punkty końcowe skonfigurowane za pomocą BasicHttpBinding używać serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="b9820-120">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="b9820-121">Jeśli ten atrybut jest `true`, żądania skierowane do lokalnych zasobów Internetu należy używać serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b9820-121">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="b9820-122">Nazwa hosta (a nie localhost), jeśli chcesz, aby klienci przechodzić przez serwer proxy, w przypadku usług na tym samym komputerze, gdy ten atrybut jest ustawiony na użycie `true`.</span><span class="sxs-lookup"><span data-stu-id="b9820-122">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="b9820-123">Jeśli ten atrybut jest `false`, wszystkie żądania internetowe są nawiązywane przy użyciu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b9820-123">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="b9820-124">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="b9820-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b9820-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b9820-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b9820-126">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b9820-126">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="b9820-127">Określa wersję protokołu SOAP używaną dla komunikatów przetwarzanych przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="b9820-127">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="b9820-128">Jedyna prawidłowa wartość to Soap11.</span><span class="sxs-lookup"><span data-stu-id="b9820-128">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="b9820-129">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="b9820-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="b9820-130">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="b9820-130">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b9820-131">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="b9820-131">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b9820-132">Wartość całkowitą, która określa maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="b9820-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="b9820-133">Wartość domyślna to 524288 (0x80000) bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9820-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="b9820-134">Menedżera buforów minimalizuje koszty za pomocą buforów przy użyciu puli buforów.</span><span class="sxs-lookup"><span data-stu-id="b9820-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="b9820-135">Bufory są wymagane do przetwarzania komunikatów przez usługę w przypadku, gdy pochodzą one z kanału.</span><span class="sxs-lookup"><span data-stu-id="b9820-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="b9820-136">Jeśli w puli buforów w celu przetworzenia obciążenia wiadomości nie jest wystarczająca ilość pamięci, menedżera buforów musi przydzielić dodatkową pamięć ze stosu CLR, co zwiększa wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b9820-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="b9820-137">Rozbudowane alokacji w stercie wyrzucania elementów CLR jest wskazanie, że rozmiar puli buforów jest za mały i że można poprawić wydajność z większych alokacji, zwiększając limit określony przez atrybut.</span><span class="sxs-lookup"><span data-stu-id="b9820-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="b9820-138">Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania na punkt końcowy skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="b9820-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="b9820-139">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9820-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b9820-140">Dodatnia liczba całkowita określająca maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="b9820-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b9820-141">Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="b9820-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="b9820-142">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b9820-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b9820-143">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9820-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="b9820-144">Definiuje encoder umożliwia kodowanie komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b9820-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="b9820-145">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="b9820-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b9820-146">-Tekst: Za pomocą kodera komunikatów tekstu.</span><span class="sxs-lookup"><span data-stu-id="b9820-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="b9820-147">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b9820-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b9820-148">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="b9820-148">The default is Text.</span></span> <span data-ttu-id="b9820-149">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="b9820-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="b9820-150">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="b9820-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b9820-151">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="b9820-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b9820-152">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="b9820-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="b9820-153">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="b9820-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="b9820-154">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="b9820-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b9820-155">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b9820-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="b9820-156">Określa przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="b9820-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="b9820-157">Wartość domyślna to "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="b9820-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="b9820-158">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="b9820-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="b9820-159">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="b9820-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b9820-160">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b9820-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b9820-161">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b9820-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="b9820-162">Identyfikator URI, który zawiera adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="b9820-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="b9820-163">Jeśli `useSystemWebProxy` ustawiono `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="b9820-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="b9820-164">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="b9820-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b9820-165">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="b9820-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b9820-166">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b9820-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b9820-167">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b9820-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b9820-168">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="b9820-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b9820-169">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b9820-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b9820-170">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b9820-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b9820-171">Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="b9820-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b9820-172">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="b9820-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b9820-173">-BigEndianUnicode: Unicode BigEndian kodowania.</span><span class="sxs-lookup"><span data-stu-id="b9820-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="b9820-174">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="b9820-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="b9820-175">-   UTF8: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="b9820-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b9820-176">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="b9820-176">The default is UTF8.</span></span> <span data-ttu-id="b9820-177">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b9820-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="b9820-178">Nieprawidłowy <xref:System.ServiceModel.TransferMode> wartość określającą, czy komunikaty są buforowane, czy strumieniowo na żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="b9820-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="b9820-179">Wartość logiczna określająca, czy automatycznie skonfigurowany serwer proxy HTTP systemu powinien być używany, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="b9820-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="b9820-180">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="b9820-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9820-181">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b9820-181">Child Elements</span></span>  
  
|<span data-ttu-id="b9820-182">Element</span><span class="sxs-lookup"><span data-stu-id="b9820-182">Element</span></span>|<span data-ttu-id="b9820-183">Opis</span><span class="sxs-lookup"><span data-stu-id="b9820-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9820-184">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="b9820-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="b9820-185">Definiuje ustawienia zabezpieczeń dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="b9820-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="b9820-186">Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b9820-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="b9820-187">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="b9820-187">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="b9820-188">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="b9820-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b9820-189">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b9820-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9820-190">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b9820-190">Parent Elements</span></span>  
  
|<span data-ttu-id="b9820-191">Element</span><span class="sxs-lookup"><span data-stu-id="b9820-191">Element</span></span>|<span data-ttu-id="b9820-192">Opis</span><span class="sxs-lookup"><span data-stu-id="b9820-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9820-193">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b9820-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b9820-194">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="b9820-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9820-195">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9820-195">Remarks</span></span>  
 <span data-ttu-id="b9820-196">BasicHttpBinding korzysta z protokołu HTTP jako transportu do wysyłania wiadomości SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="b9820-196">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="b9820-197">Usługa może używać tego powiązania do uwidaczniają punkty końcowe, które odpowiadają WS-I najlepszych praktyk w zakresie 1.1, takich jak te, które zużywają ASMX klientów.</span><span class="sxs-lookup"><span data-stu-id="b9820-197">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="b9820-198">Podobnie, klient może używać BasicHttpBinding do komunikowania się z usługi ujawniające punktów końcowych, które odpowiadają WS-I najlepszych praktyk w zakresie 1.1, takich jak usługi sieci Web ASMX lub usługi, które skonfigurowano BasicHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="b9820-198">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="b9820-199">Zabezpieczenia jest domyślnie wyłączona, ale można dodać ustawienie atrybutu tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) element podrzędny, wartość inną niż `None`.</span><span class="sxs-lookup"><span data-stu-id="b9820-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="b9820-200">Używa ona "Text" kodowania i UTF-8 tekst komunikatu kodowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="b9820-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9820-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9820-201">Example</span></span>  
 <span data-ttu-id="b9820-202">W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.BasicHttpBinding> zapewniający HTTP komunikacji i maksymalnie współdziałanie z pierwszym — i second - generation usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b9820-202">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="b9820-203">Powiązanie jest określona w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="b9820-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b9820-204">Typ powiązania jest określony, przy użyciu `binding` atrybutu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b9820-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="b9820-205">Jeśli chcesz skonfigurować podstawowe powiązanie i zmienić niektóre z jego ustawienia, należy zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="b9820-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="b9820-206">Punkt końcowy musi odwoływać się do konfiguracji powiązania według nazwy przy użyciu `bindingConfiguration` atrybutu `<endpoint>` elementu, jak pokazano w poniższym kodzie konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="b9820-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b9820-207">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9820-207">Example</span></span>  
 <span data-ttu-id="b9820-208">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="b9820-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b9820-209">Funkcje z poprzedniego przykładu, można osiągnąć, usuwając bindingConfiguration z adresu punktu końcowego, a nazwa z wiązania.</span><span class="sxs-lookup"><span data-stu-id="b9820-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="b9820-210">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b9820-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9820-211">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9820-211">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="b9820-212">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b9820-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b9820-213">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="b9820-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b9820-214">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="b9820-214">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b9820-215">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b9820-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
