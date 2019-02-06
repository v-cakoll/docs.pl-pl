---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 834f2830d4b9ab33b65b39c772790e8d45e4b111
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759652"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="c8cac-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c8cac-101">\<wsFederationHttpBinding></span></span>
<span data-ttu-id="c8cac-102">Definiuje powiązanie, które obsługuje WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c8cac-102">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="c8cac-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c8cac-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c8cac-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c8cac-104">\<bindings></span></span>  
<span data-ttu-id="c8cac-105">wsFederationBinding, element</span><span class="sxs-lookup"><span data-stu-id="c8cac-105">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8cac-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8cac-106">Syntax</span></span>  
  
```xml  
<wsFederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
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
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
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
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
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
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8cac-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c8cac-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c8cac-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c8cac-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8cac-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c8cac-109">Attributes</span></span>  
  
|<span data-ttu-id="c8cac-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c8cac-110">Attribute</span></span>|<span data-ttu-id="c8cac-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c8cac-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8cac-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="c8cac-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="c8cac-113">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="c8cac-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="c8cac-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c8cac-114">The default is `false`.</span></span>|  
|<span data-ttu-id="c8cac-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="c8cac-115">closeTimeout</span></span>|<span data-ttu-id="c8cac-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="c8cac-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c8cac-117">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c8cac-118">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c8cac-118">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c8cac-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c8cac-119">hostnameComparisonMode</span></span>|<span data-ttu-id="c8cac-120">Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="c8cac-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="c8cac-121">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="c8cac-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="c8cac-122">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="c8cac-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c8cac-123">maxBufferPoolSize</span></span>|<span data-ttu-id="c8cac-124">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="c8cac-125">Wartość domyślna to 524,288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="c8cac-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="c8cac-126">Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="c8cac-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="c8cac-127">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="c8cac-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c8cac-128">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="c8cac-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c8cac-129">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="c8cac-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="c8cac-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c8cac-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="c8cac-131">Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c8cac-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="c8cac-132">Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c8cac-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="c8cac-133">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c8cac-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c8cac-134">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="c8cac-134">The default is 65536.</span></span>|  
|<span data-ttu-id="c8cac-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="c8cac-135">messageEncoding</span></span>|<span data-ttu-id="c8cac-136">Definiuje encoder umożliwia kodowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c8cac-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="c8cac-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="c8cac-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c8cac-138">-Tekst: Za pomocą kodera komunikatów tekstu.</span><span class="sxs-lookup"><span data-stu-id="c8cac-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="c8cac-139">-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="c8cac-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="c8cac-140">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="c8cac-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="c8cac-141">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="c8cac-142">nazwa</span><span class="sxs-lookup"><span data-stu-id="c8cac-142">name</span></span>|<span data-ttu-id="c8cac-143">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c8cac-144">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c8cac-145">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="c8cac-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c8cac-146">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c8cac-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="c8cac-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="c8cac-147">openTimeout</span></span>|<span data-ttu-id="c8cac-148">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="c8cac-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c8cac-149">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c8cac-150">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c8cac-150">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c8cac-151">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="c8cac-151">privactyNoticeAt</span></span>|<span data-ttu-id="c8cac-152">Ciąg określający URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="c8cac-152">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="c8cac-153">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="c8cac-153">privactyNoticeVersion</span></span>|<span data-ttu-id="c8cac-154">Liczba całkowita określająca wersję bieżącego powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="c8cac-154">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="c8cac-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="c8cac-155">proxyAddress</span></span>|<span data-ttu-id="c8cac-156">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="c8cac-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="c8cac-157">Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="c8cac-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="c8cac-158">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="c8cac-158">The default is `null`.</span></span>|  
|<span data-ttu-id="c8cac-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c8cac-159">receiveTimeout</span></span>|<span data-ttu-id="c8cac-160">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c8cac-161">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c8cac-162">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="c8cac-162">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="c8cac-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c8cac-163">sendTimeout</span></span>|<span data-ttu-id="c8cac-164">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c8cac-165">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c8cac-166">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c8cac-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c8cac-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="c8cac-167">textEncoding</span></span>|<span data-ttu-id="c8cac-168">Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="c8cac-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c8cac-169">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="c8cac-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c8cac-170">-BigEndianUnicode: Unicode BigEndian kodowania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="c8cac-171">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="c8cac-172">-   UTF8: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="c8cac-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="c8cac-173">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="c8cac-173">The default is UTF8.</span></span> <span data-ttu-id="c8cac-174">Ten atrybut jest typu <xref:System.Text.Encoding>...</span><span class="sxs-lookup"><span data-stu-id="c8cac-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="c8cac-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="c8cac-175">transactionFlow</span></span>|<span data-ttu-id="c8cac-176">Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji.</span><span class="sxs-lookup"><span data-stu-id="c8cac-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="c8cac-177">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c8cac-177">The default is `false`.</span></span>|  
|<span data-ttu-id="c8cac-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="c8cac-178">useDefaultWebProxy</span></span>|<span data-ttu-id="c8cac-179">Wartość logiczna wskazująca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c8cac-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="c8cac-180">Adres serwera proxy musi być `null` (czyli nie ustawiono) Jeśli ten atrybut jest `true`.</span><span class="sxs-lookup"><span data-stu-id="c8cac-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="c8cac-181">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="c8cac-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8cac-182">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c8cac-182">Child Elements</span></span>  
  
|<span data-ttu-id="c8cac-183">Element</span><span class="sxs-lookup"><span data-stu-id="c8cac-183">Element</span></span>|<span data-ttu-id="c8cac-184">Opis</span><span class="sxs-lookup"><span data-stu-id="c8cac-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8cac-185">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c8cac-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="c8cac-186">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c8cac-186">Defines the security settings for the message.</span></span> <span data-ttu-id="c8cac-187">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="c8cac-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c8cac-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="c8cac-189">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c8cac-190">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="c8cac-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c8cac-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="c8cac-192">Określa, jeśli niezawodnej sesji są ustanawiane między punktami końcowymi kanału.</span><span class="sxs-lookup"><span data-stu-id="c8cac-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8cac-193">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c8cac-193">Parent Elements</span></span>  
  
|<span data-ttu-id="c8cac-194">Element</span><span class="sxs-lookup"><span data-stu-id="c8cac-194">Element</span></span>|<span data-ttu-id="c8cac-195">Opis</span><span class="sxs-lookup"><span data-stu-id="c8cac-195">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8cac-196">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c8cac-196">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="c8cac-197">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c8cac-197">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8cac-198">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8cac-198">Remarks</span></span>  
 <span data-ttu-id="c8cac-199">Federacja znajduje się możliwość udostępniania tożsamości w wielu systemach uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="c8cac-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="c8cac-200">Te tożsamości mogą odwoływać się do użytkowników lub komputerów.</span><span class="sxs-lookup"><span data-stu-id="c8cac-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="c8cac-201">Federacyjne HTTP obsługuje zabezpieczenia protokołu SOAP, a także trybu mieszanego zabezpieczeń, ale nie obsługuje wyłącznie za pomocą zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="c8cac-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="c8cac-202">To powiązanie zapewnia obsługę Windows Communication Foundation (WCF) dla protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c8cac-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="c8cac-203">Skonfigurowano z tym powiązaniem usług, należy użyć protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c8cac-203">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="c8cac-204">Powiązania składają się z stosu elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="c8cac-205">Stos elementów w wiązania</span><span class="sxs-lookup"><span data-stu-id="c8cac-205">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="c8cac-206">`wsFederationHttpBinding` jest taka sama, jak zawarte w `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="c8cac-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="c8cac-207">gdy [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) jest ustawiona na wartość domyślną <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="c8cac-207">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="c8cac-208">`wsFederationHttpBinding` Kontroluje szczegółowe informacje o ustawienia zabezpieczeń wiadomości w [ \<komunikatu >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c8cac-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="c8cac-209">Należy pamiętać, że [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element umożliwia uzyskiwanie dostępu tylko wtedy, gdy zabezpieczeń używanym przez wiązanie nie można zmienić po utworzeniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="c8cac-209">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="c8cac-210">`wsFederationHttpBinding` Także atrybutem privactyNoticeAt do ustawiania i pobierania identyfikatora URI, w której znajduje się powiadomienie dotyczące prywatności.</span><span class="sxs-lookup"><span data-stu-id="c8cac-210">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="c8cac-211">Zapewnienie zasad bezpieczeństwa jest szczególnie ważne w scenariuszach federacji.</span><span class="sxs-lookup"><span data-stu-id="c8cac-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="c8cac-212">Zaleca się użyć jakiegoś zabezpieczeń, takich jak HTTPS, do ochrony zasad ze strony złośliwych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="c8cac-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="c8cac-213">W scenariuszach Federacji za pomocą tego powiązania zasady usługi ma potencjalnie ważne informacje, takie jak klucza do użycia w celu zaszyfrowania wystawiony token (SAML), typ oświadczenia do umieszczania w tokenie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c8cac-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="c8cac-214">Jeśli zasada ta zostanie naruszony, osoba atakująca można wykryć klucz wystawiony token, co prowadzi do dalsze próby naruszenia, ujawnienia informacji i inne złośliwe działanie.</span><span class="sxs-lookup"><span data-stu-id="c8cac-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="c8cac-215">Aby temu zapobiec, zasady, należy uzyskać bezpieczne (na przykład przy użyciu protokołu HTTPS) z usługi.</span><span class="sxs-lookup"><span data-stu-id="c8cac-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="c8cac-216">Aby uzyskać więcej informacji na temat tego powiązania, zobacz [jak: Tworzenie elementu WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c8cac-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8cac-217">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8cac-217">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
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
  
## <a name="see-also"></a><span data-ttu-id="c8cac-218">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8cac-218">See also</span></span>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="c8cac-219">Instrukcje: Tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c8cac-219">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="c8cac-220">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c8cac-220">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c8cac-221">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c8cac-221">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c8cac-222">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c8cac-222">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c8cac-223">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c8cac-223">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
