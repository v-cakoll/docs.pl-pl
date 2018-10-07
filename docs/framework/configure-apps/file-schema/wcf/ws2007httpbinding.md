---
title: '&lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 95af699592492d4abfdf7867e8a207db7490ccdf
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845479"
---
# <a name="ltws2007httpbindinggt"></a><span data-ttu-id="8de46-102">&lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8de46-102">&lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="8de46-103">Definiuje interoperacyjne powiązanie, które zapewnia obsługę dla poprawnych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="8de46-103">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="8de46-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8de46-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8de46-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8de46-105">\<bindings></span></span>  
<span data-ttu-id="8de46-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="8de46-106">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de46-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8de46-107">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8de46-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8de46-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8de46-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8de46-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8de46-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8de46-110">Attributes</span></span>  
  
|<span data-ttu-id="8de46-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8de46-111">Attribute</span></span>|<span data-ttu-id="8de46-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8de46-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="8de46-113">Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="8de46-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="8de46-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="8de46-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="8de46-115">Można użyć tej właściwości, gdy wchodzisz w interakcję z usług sieci Web platformy ASP.NET (ASMX), które używają plików cookie.</span><span class="sxs-lookup"><span data-stu-id="8de46-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="8de46-116">Daje to gwarancję, że pliki cookie, które serwer zwraca są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.</span><span class="sxs-lookup"><span data-stu-id="8de46-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="8de46-117">Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8de46-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="8de46-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="8de46-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="8de46-119">A <xref:System.TimeSpan> wartość, która określa przedział czasu na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="8de46-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="8de46-120">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8de46-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8de46-121">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8de46-121">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="8de46-122">Określa tryb porównywania nazwy hosta HTTP używany do analizowania Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="8de46-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="8de46-123">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="8de46-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="8de46-124">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="8de46-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="8de46-125">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8de46-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="8de46-126">Wartość domyślna to 524,288 bajtów (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="8de46-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="8de46-127">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="8de46-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="8de46-128">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, podobnie jak wyrzucanie elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="8de46-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="8de46-129">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="8de46-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="8de46-130">Umożliwia to uniknięcie obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="8de46-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="8de46-131">Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które mogą odbierać kanał, który został skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="8de46-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="8de46-132">Nadawca wiadomości przekroczenie tego limitu otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8de46-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="8de46-133">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8de46-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8de46-134">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="8de46-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="8de46-135">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8de46-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="8de46-136">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="8de46-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8de46-137">-   `Text`: Służy koder komunikatu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="8de46-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="8de46-138">-   `Mtom`: Służy kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8de46-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="8de46-139">Wartość domyślna to `Text`.</span><span class="sxs-lookup"><span data-stu-id="8de46-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="8de46-140">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="8de46-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="8de46-141">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="8de46-141">The configuration name of the binding.</span></span> <span data-ttu-id="8de46-142">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="8de46-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8de46-143">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="8de46-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8de46-144">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8de46-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="8de46-145">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="8de46-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8de46-146">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8de46-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8de46-147">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8de46-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="8de46-148">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="8de46-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="8de46-149">Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="8de46-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="8de46-150">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="8de46-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="8de46-151">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="8de46-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8de46-152">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8de46-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8de46-153">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8de46-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="8de46-154">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="8de46-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8de46-155">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8de46-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8de46-156">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="8de46-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="8de46-157">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="8de46-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="8de46-158">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="8de46-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8de46-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian kodowania.</span><span class="sxs-lookup"><span data-stu-id="8de46-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="8de46-160">-   `Utf16TextEncoding`: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="8de46-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="8de46-161">-   `Utf8TextEncoding`: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="8de46-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="8de46-162">Wartość domyślna to `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="8de46-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="8de46-163">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="8de46-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="8de46-164">Wartość, która określa, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="8de46-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="8de46-165">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="8de46-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="8de46-166">Wartość, która określa, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="8de46-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="8de46-167">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="8de46-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8de46-168">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8de46-168">Child Elements</span></span>  
  
|<span data-ttu-id="8de46-169">Element</span><span class="sxs-lookup"><span data-stu-id="8de46-169">Element</span></span>|<span data-ttu-id="8de46-170">Opis</span><span class="sxs-lookup"><span data-stu-id="8de46-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8de46-171">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="8de46-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="8de46-172">Definiuje ustawienia zabezpieczeń dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="8de46-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="8de46-173">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="8de46-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="8de46-174">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="8de46-174">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="8de46-175">Definiuje ograniczenia złożoności wiadomości SOAP, które może przetworzyć punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="8de46-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="8de46-176">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8de46-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="8de46-177">reliableSession</span><span class="sxs-lookup"><span data-stu-id="8de46-177">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="8de46-178">Określa, czy niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="8de46-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8de46-179">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8de46-179">Parent Elements</span></span>  
  
|<span data-ttu-id="8de46-180">Element</span><span class="sxs-lookup"><span data-stu-id="8de46-180">Element</span></span>|<span data-ttu-id="8de46-181">Opis</span><span class="sxs-lookup"><span data-stu-id="8de46-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8de46-182">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8de46-182">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="8de46-183">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="8de46-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8de46-184">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8de46-184">Remarks</span></span>  
 <span data-ttu-id="8de46-185">`WS2007HttpBinding` Dodaje podobne do powiązania dostarczane przez system `WSHttpBinding` , ale organizacji dla wersji standardowa zawodowego of Structured Information Standards (OASIS) protokołów TransactionFlow, ReliableSession i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8de46-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="8de46-186">Brak zmian do obiektu modelu lub domyślne ustawienia są wymagane, gdy za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8de46-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8de46-187">Przykład</span><span class="sxs-lookup"><span data-stu-id="8de46-187">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8de46-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8de46-188">See Also</span></span>  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [<span data-ttu-id="8de46-189">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8de46-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8de46-190">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="8de46-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8de46-191">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8de46-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="8de46-192">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8de46-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
