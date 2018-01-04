---
title: '&lt;ws2007HttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a92ab5b85a65793473dcafbd67ac710912a476f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltws2007httpbindinggt"></a><span data-ttu-id="44e32-102">&lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="44e32-102">&lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="44e32-103">Definiuje interoperacyjne powiązanie, które zapewnia obsługę dla poprawnych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-103">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="44e32-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="44e32-104">\<system.serviceModel></span></span>  
<span data-ttu-id="44e32-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="44e32-105">\<bindings></span></span>  
<span data-ttu-id="44e32-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="44e32-106">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e32-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="44e32-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44e32-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44e32-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44e32-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44e32-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44e32-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44e32-110">Attributes</span></span>  
  
|<span data-ttu-id="44e32-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="44e32-111">Attribute</span></span>|<span data-ttu-id="44e32-112">Opis</span><span class="sxs-lookup"><span data-stu-id="44e32-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="44e32-113">Wartość, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="44e32-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="44e32-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="44e32-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="44e32-115">Tej właściwości można użyć w przypadku interakcji z usługami sieci Web platformy ASP.NET (ASMX), które używają plików cookie.</span><span class="sxs-lookup"><span data-stu-id="44e32-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="44e32-116">Daje to pewność, że serwer zwraca pliki cookie są automatycznie kopiowane do wszystkich przyszłych żądań dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="44e32-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="44e32-117">Wartość, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="44e32-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="44e32-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="44e32-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="44e32-119">A <xref:System.TimeSpan> wartość, która określa przedział czasu dla na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="44e32-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="44e32-120">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="44e32-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44e32-121">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="44e32-121">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="44e32-122">Określa tryb porównania nazw hostów HTTP używany do analizowania Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="44e32-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="44e32-123">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="44e32-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="44e32-124">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.</span><span class="sxs-lookup"><span data-stu-id="44e32-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="44e32-125">Maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="44e32-126">Wartość domyślna to 524,288 bajtów (512 x 1024).</span><span class="sxs-lookup"><span data-stu-id="44e32-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="44e32-127">Wiele elementów [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] użyć buforów.</span><span class="sxs-lookup"><span data-stu-id="44e32-127">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="44e32-128">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, ponieważ jest pamięci dla buforów.</span><span class="sxs-lookup"><span data-stu-id="44e32-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="44e32-129">Używając puli buforów może potrwać buforu z puli, go używać i zwracać do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="44e32-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="44e32-130">Dzięki temu można uniknąć obciążenie związane z tworzeniem i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="44e32-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="44e32-131">Maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które mogą odbierać kanału skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="44e32-132">Nadawcy wiadomości przekracza ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="44e32-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="44e32-133">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="44e32-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="44e32-134">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="44e32-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="44e32-135">Definiuje koder używany do kodowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="44e32-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="44e32-136">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="44e32-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="44e32-137">-   `Text`: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="44e32-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="44e32-138">-   `Mtom`: Używać kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="44e32-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="44e32-139">Wartość domyślna to `Text`.</span><span class="sxs-lookup"><span data-stu-id="44e32-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="44e32-140">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="44e32-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="44e32-141">Nazwa konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-141">The configuration name of the binding.</span></span> <span data-ttu-id="44e32-142">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="44e32-143">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="44e32-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="44e32-144">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="44e32-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="44e32-145">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="44e32-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="44e32-146">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="44e32-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44e32-147">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="44e32-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="44e32-148">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="44e32-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="44e32-149">Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="44e32-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="44e32-150">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="44e32-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="44e32-151">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="44e32-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="44e32-152">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="44e32-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44e32-153">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="44e32-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="44e32-154">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="44e32-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="44e32-155">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="44e32-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44e32-156">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="44e32-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="44e32-157">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="44e32-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="44e32-158">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="44e32-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="44e32-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian kodowania.</span><span class="sxs-lookup"><span data-stu-id="44e32-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="44e32-160">-   `Utf16TextEncoding`: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="44e32-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="44e32-161">-   `Utf8TextEncoding`: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="44e32-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="44e32-162">Wartość domyślna to `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="44e32-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="44e32-163">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="44e32-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="44e32-164">Wartość, która określa, czy wiązanie obsługuje przechodzenia WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="44e32-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="44e32-165">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="44e32-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="44e32-166">Wartość, która określa, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="44e32-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="44e32-167">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="44e32-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44e32-168">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44e32-168">Child Elements</span></span>  
  
|<span data-ttu-id="44e32-169">Element</span><span class="sxs-lookup"><span data-stu-id="44e32-169">Element</span></span>|<span data-ttu-id="44e32-170">Opis</span><span class="sxs-lookup"><span data-stu-id="44e32-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44e32-171">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="44e32-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="44e32-172">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="44e32-173">Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="44e32-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="44e32-174">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="44e32-174">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="44e32-175">Definiuje ograniczenia złożoności wiadomości SOAP, które może przetworzyć punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="44e32-176">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="44e32-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="44e32-177">reliableSession</span><span class="sxs-lookup"><span data-stu-id="44e32-177">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="44e32-178">Określa, czy między punktami końcowymi kanału ustanowiono niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="44e32-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44e32-179">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44e32-179">Parent Elements</span></span>  
  
|<span data-ttu-id="44e32-180">Element</span><span class="sxs-lookup"><span data-stu-id="44e32-180">Element</span></span>|<span data-ttu-id="44e32-181">Opis</span><span class="sxs-lookup"><span data-stu-id="44e32-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44e32-182">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="44e32-182">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="44e32-183">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="44e32-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e32-184">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44e32-184">Remarks</span></span>  
 <span data-ttu-id="44e32-185">`WS2007HttpBinding` Dodaje podobne do powiązania dostarczane przez system `WSHttpBinding` , ale organizacji przejścia z Structured Information Standards (OASIS) wersje standardowe protokoły TransactionFlow, ReliableSession i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="44e32-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="44e32-186">Brak zmian do modelu lub wartość domyślną ustawienia obiektu są wymagane, korzystając z tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="44e32-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e32-187">Przykład</span><span class="sxs-lookup"><span data-stu-id="44e32-187">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44e32-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44e32-188">See Also</span></span>  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [<span data-ttu-id="44e32-189">Powiązania</span><span class="sxs-lookup"><span data-stu-id="44e32-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="44e32-190">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="44e32-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="44e32-191">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="44e32-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="44e32-192">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="44e32-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
