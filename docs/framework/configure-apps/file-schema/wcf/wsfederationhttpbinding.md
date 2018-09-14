---
title: '&lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 943887dd2bf3b309c0663a9eb06e658ee5957844
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "44757149"
---
# <a name="ltwsfederationhttpbindinggt"></a><span data-ttu-id="441a9-102">&lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="441a9-102">&lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="441a9-103">Definiuje powiązanie, które obsługuje WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="441a9-103">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="441a9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="441a9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="441a9-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="441a9-105">\<bindings></span></span>  
<span data-ttu-id="441a9-106">wsFederationBinding, element</span><span class="sxs-lookup"><span data-stu-id="441a9-106">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="441a9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="441a9-107">Syntax</span></span>  
  
```xml  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="441a9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="441a9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="441a9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="441a9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="441a9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="441a9-110">Attributes</span></span>  
  
|<span data-ttu-id="441a9-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="441a9-111">Attribute</span></span>|<span data-ttu-id="441a9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="441a9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="441a9-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="441a9-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="441a9-114">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="441a9-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="441a9-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="441a9-115">The default is `false`.</span></span>|  
|<span data-ttu-id="441a9-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="441a9-116">closeTimeout</span></span>|<span data-ttu-id="441a9-117">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="441a9-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="441a9-118">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="441a9-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="441a9-119">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="441a9-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="441a9-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="441a9-120">hostnameComparisonMode</span></span>|<span data-ttu-id="441a9-121">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="441a9-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="441a9-122">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="441a9-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="441a9-123">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="441a9-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="441a9-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="441a9-124">maxBufferPoolSize</span></span>|<span data-ttu-id="441a9-125">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="441a9-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="441a9-126">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="441a9-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="441a9-127">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="441a9-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="441a9-128">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="441a9-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="441a9-129">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="441a9-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="441a9-130">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="441a9-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="441a9-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="441a9-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="441a9-132">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="441a9-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="441a9-133">Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="441a9-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="441a9-134">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="441a9-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="441a9-135">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="441a9-135">The default is 65536.</span></span>|  
|<span data-ttu-id="441a9-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="441a9-136">messageEncoding</span></span>|<span data-ttu-id="441a9-137">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="441a9-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="441a9-138">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="441a9-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="441a9-139">-Text: Użyj koder komunikatu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="441a9-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="441a9-140">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="441a9-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="441a9-141">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="441a9-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="441a9-142">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="441a9-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="441a9-143">nazwa</span><span class="sxs-lookup"><span data-stu-id="441a9-143">name</span></span>|<span data-ttu-id="441a9-144">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="441a9-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="441a9-145">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="441a9-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="441a9-146">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="441a9-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="441a9-147">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="441a9-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="441a9-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="441a9-148">openTimeout</span></span>|<span data-ttu-id="441a9-149">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="441a9-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="441a9-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="441a9-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="441a9-151">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="441a9-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="441a9-152">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="441a9-152">privactyNoticeAt</span></span>|<span data-ttu-id="441a9-153">Ciąg określający URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="441a9-153">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="441a9-154">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="441a9-154">privactyNoticeVersion</span></span>|<span data-ttu-id="441a9-155">Liczba całkowita określająca wersję bieżącego powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="441a9-155">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="441a9-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="441a9-156">proxyAddress</span></span>|<span data-ttu-id="441a9-157">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="441a9-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="441a9-158">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="441a9-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="441a9-159">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="441a9-159">The default is `null`.</span></span>|  
|<span data-ttu-id="441a9-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="441a9-160">receiveTimeout</span></span>|<span data-ttu-id="441a9-161">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="441a9-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="441a9-162">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="441a9-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="441a9-163">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="441a9-163">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="441a9-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="441a9-164">sendTimeout</span></span>|<span data-ttu-id="441a9-165">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="441a9-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="441a9-166">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="441a9-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="441a9-167">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="441a9-167">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="441a9-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="441a9-168">textEncoding</span></span>|<span data-ttu-id="441a9-169">Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="441a9-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="441a9-170">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="441a9-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="441a9-171">-BigEndianUnicode: Unicode BigEndian kodowanie.</span><span class="sxs-lookup"><span data-stu-id="441a9-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="441a9-172">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="441a9-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="441a9-173">-UTF8: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="441a9-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="441a9-174">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="441a9-174">The default is UTF8.</span></span> <span data-ttu-id="441a9-175">Ten atrybut jest typu <xref:System.Text.Encoding>...</span><span class="sxs-lookup"><span data-stu-id="441a9-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="441a9-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="441a9-176">transactionFlow</span></span>|<span data-ttu-id="441a9-177">Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="441a9-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="441a9-178">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="441a9-178">The default is `false`.</span></span>|  
|<span data-ttu-id="441a9-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="441a9-179">useDefaultWebProxy</span></span>|<span data-ttu-id="441a9-180">Wartość logiczna wskazująca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="441a9-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="441a9-181">Adres serwera proxy musi być `null` (czyli nie ustawiono) Jeśli ten atrybut jest `true`.</span><span class="sxs-lookup"><span data-stu-id="441a9-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="441a9-182">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="441a9-182">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="441a9-183">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="441a9-183">Child Elements</span></span>  
  
|<span data-ttu-id="441a9-184">Element</span><span class="sxs-lookup"><span data-stu-id="441a9-184">Element</span></span>|<span data-ttu-id="441a9-185">Opis</span><span class="sxs-lookup"><span data-stu-id="441a9-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="441a9-186">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="441a9-186">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="441a9-187">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="441a9-187">Defines the security settings for the message.</span></span> <span data-ttu-id="441a9-188">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="441a9-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="441a9-189">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="441a9-189">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="441a9-190">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="441a9-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="441a9-191">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="441a9-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="441a9-192">reliableSession</span><span class="sxs-lookup"><span data-stu-id="441a9-192">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="441a9-193">Określa, jeśli niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="441a9-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="441a9-194">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="441a9-194">Parent Elements</span></span>  
  
|<span data-ttu-id="441a9-195">Element</span><span class="sxs-lookup"><span data-stu-id="441a9-195">Element</span></span>|<span data-ttu-id="441a9-196">Opis</span><span class="sxs-lookup"><span data-stu-id="441a9-196">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="441a9-197">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="441a9-197">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="441a9-198">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="441a9-198">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="441a9-199">Uwagi</span><span class="sxs-lookup"><span data-stu-id="441a9-199">Remarks</span></span>  
 <span data-ttu-id="441a9-200">Federacja znajduje się możliwość udostępniania tożsamości w wielu systemach uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="441a9-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="441a9-201">Te tożsamości mogą odwoływać się do użytkowników lub komputerów.</span><span class="sxs-lookup"><span data-stu-id="441a9-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="441a9-202">Federacyjne HTTP obsługuje zabezpieczenia protokołu SOAP, a także trybu mieszanego zabezpieczeń, ale nie obsługuje wyłącznie za pomocą zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="441a9-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="441a9-203">To powiązanie zapewnia obsługę Windows Communication Foundation (WCF) dla protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="441a9-203">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="441a9-204">Skonfigurowano z tym powiązaniem usług, należy użyć protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="441a9-204">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="441a9-205">Powiązania składają się z stosu elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="441a9-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="441a9-206">Stos elementów w wiązania</span><span class="sxs-lookup"><span data-stu-id="441a9-206">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="441a9-207">`wsFederationHttpBinding` jest taka sama, jak zawarte w `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="441a9-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="441a9-208">gdy [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) jest ustawiona na wartość domyślną <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="441a9-208">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="441a9-209">`wsFederationHttpBinding` Kontroluje szczegółowe informacje o ustawienia zabezpieczeń wiadomości w [ \<komunikatu >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="441a9-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="441a9-210">Należy pamiętać, że [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element umożliwia uzyskiwanie dostępu tylko wtedy, gdy zabezpieczeń używanym przez wiązanie nie można zmienić po utworzeniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="441a9-210">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="441a9-211">`wsFederationHttpBinding` Także atrybutem privactyNoticeAt do ustawiania i pobierania identyfikatora URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="441a9-211">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="441a9-212">Zapewnienie zasad bezpieczeństwa jest szczególnie ważne w scenariuszach federacji.</span><span class="sxs-lookup"><span data-stu-id="441a9-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="441a9-213">Zaleca się użyć jakiegoś zabezpieczeń, takich jak HTTPS, do ochrony zasad ze strony złośliwych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="441a9-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="441a9-214">W scenariuszach Federacji za pomocą tego powiązania zasady usługi ma potencjalnie ważne informacje, takie jak klucza do użycia w celu zaszyfrowania wystawiony token (SAML), typ oświadczenia do umieszczania w tokenie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="441a9-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="441a9-215">Jeśli zasada ta zostanie naruszony, osoba atakująca można wykryć klucz wystawiony token, co prowadzi do dalsze próby naruszenia, ujawnienia informacji i inne złośliwe działanie.</span><span class="sxs-lookup"><span data-stu-id="441a9-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="441a9-216">Aby temu zapobiec, zasady, należy uzyskać bezpieczne (na przykład przy użyciu protokołu HTTPS) z usługi.</span><span class="sxs-lookup"><span data-stu-id="441a9-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="441a9-217">Aby uzyskać więcej informacji na temat tego powiązania, zobacz [porady: Tworzenie elementu WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="441a9-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="441a9-218">Przykład</span><span class="sxs-lookup"><span data-stu-id="441a9-218">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="saml"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</wsFederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="441a9-219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="441a9-219">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [<span data-ttu-id="441a9-220">Instrukcje: tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="441a9-220">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="441a9-221">Powiązania</span><span class="sxs-lookup"><span data-stu-id="441a9-221">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="441a9-222">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="441a9-222">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="441a9-223">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="441a9-223">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="441a9-224">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="441a9-224">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
