---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: a605d3241ec62f5648e3439b327153f3fb4590df
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399033"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="0c2e8-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0c2e8-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="0c2e8-102">Definiuje powiązanie, które obsługuje WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="0c2e8-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c2e8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0c2e8-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0c2e8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0c2e8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0c2e8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0c2e8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsFederationHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="0c2e8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="0c2e8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c2e8-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="0c2e8-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0c2e8-108">Attributes and Elements</span></span>

<span data-ttu-id="0c2e8-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c2e8-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0c2e8-110">Attributes</span></span>

|<span data-ttu-id="0c2e8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0c2e8-111">Attribute</span></span>|<span data-ttu-id="0c2e8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0c2e8-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="0c2e8-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="0c2e8-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="0c2e8-114">Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="0c2e8-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-115">The default is `false`.</span></span>|
|<span data-ttu-id="0c2e8-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="0c2e8-116">closeTimeout</span></span>|<span data-ttu-id="0c2e8-117"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0c2e8-118">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0c2e8-119">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-119">The default is 00:01:00.</span></span>|
|<span data-ttu-id="0c2e8-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="0c2e8-120">hostnameComparisonMode</span></span>|<span data-ttu-id="0c2e8-121">Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0c2e8-122">Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0c2e8-123">Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, co powoduje ignorowanie nazwy hosta w dopasowaniu.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="0c2e8-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0c2e8-124">maxBufferPoolSize</span></span>|<span data-ttu-id="0c2e8-125">Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="0c2e8-126">Wartość domyślna to 524 288 bajtów (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="0c2e8-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="0c2e8-127">Wiele części Windows Communication Foundation (WCF) używa buforów.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="0c2e8-128">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0c2e8-129">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0c2e8-130">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="0c2e8-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0c2e8-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="0c2e8-132">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0c2e8-133">Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="0c2e8-134">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0c2e8-135">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-135">The default is 65536.</span></span>|
|<span data-ttu-id="0c2e8-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="0c2e8-136">messageEncoding</span></span>|<span data-ttu-id="0c2e8-137">Definiuje koder używany do kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="0c2e8-138">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="0c2e8-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0c2e8-139">Opis Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="0c2e8-140">MTOM Użyj mechanizmu organizacji przesyłania komunikatów 1,0 (MTOM) kodera.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="0c2e8-141">Wartość domyślna to Text.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="0c2e8-142">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="0c2e8-143">nazwa</span><span class="sxs-lookup"><span data-stu-id="0c2e8-143">name</span></span>|<span data-ttu-id="0c2e8-144">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0c2e8-145">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0c2e8-146">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0c2e8-147">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0c2e8-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="0c2e8-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="0c2e8-148">openTimeout</span></span>|<span data-ttu-id="0c2e8-149"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0c2e8-150">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0c2e8-151">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-151">The default is 00:01:00.</span></span>|
|<span data-ttu-id="0c2e8-152">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="0c2e8-152">privacyNoticeAt</span></span>|<span data-ttu-id="0c2e8-153">Ciąg określający identyfikator URI, w którym znajduje się powiadomienie o prywatności.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-153">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="0c2e8-154">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="0c2e8-154">privacyNoticeVersion</span></span>|<span data-ttu-id="0c2e8-155">Liczba całkowita, która określa wersję bieżącego powiadomienia o ochronie prywatności.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-155">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="0c2e8-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="0c2e8-156">proxyAddress</span></span>|<span data-ttu-id="0c2e8-157">Identyfikator URI, który określa adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="0c2e8-158">Jeśli `useDefaultWebProxy` `null`jest `true`, to ustawienie musi być.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="0c2e8-159">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-159">The default is `null`.</span></span>|
|<span data-ttu-id="0c2e8-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="0c2e8-160">receiveTimeout</span></span>|<span data-ttu-id="0c2e8-161"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0c2e8-162">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0c2e8-163">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-163">The default is 00:10:00.</span></span>|
|<span data-ttu-id="0c2e8-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="0c2e8-164">sendTimeout</span></span>|<span data-ttu-id="0c2e8-165"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0c2e8-166">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0c2e8-167">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-167">The default is 00:01:00.</span></span>|
|<span data-ttu-id="0c2e8-168">TextEncoding</span><span class="sxs-lookup"><span data-stu-id="0c2e8-168">textEncoding</span></span>|<span data-ttu-id="0c2e8-169">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0c2e8-170">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="0c2e8-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0c2e8-171">- BigEndianUnicode: Kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0c2e8-172">Unicode kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0c2e8-173">-   UTF8: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="0c2e8-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0c2e8-174">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-174">The default is UTF8.</span></span> <span data-ttu-id="0c2e8-175">Ten atrybut jest typu <xref:System.Text.Encoding>..</span><span class="sxs-lookup"><span data-stu-id="0c2e8-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="0c2e8-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="0c2e8-176">transactionFlow</span></span>|<span data-ttu-id="0c2e8-177">Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="0c2e8-178">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-178">The default is `false`.</span></span>|
|<span data-ttu-id="0c2e8-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="0c2e8-179">useDefaultWebProxy</span></span>|<span data-ttu-id="0c2e8-180">Wartość logiczna wskazująca, czy jest używany konfigurowany przez system serwer proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="0c2e8-181">Jeśli ten atrybut ma `null` `true`wartość, adres serwera proxy musi mieć wartość (czyli nie jest ustawiony).</span><span class="sxs-lookup"><span data-stu-id="0c2e8-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="0c2e8-182">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-182">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0c2e8-183">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0c2e8-183">Child Elements</span></span>

|<span data-ttu-id="0c2e8-184">Element</span><span class="sxs-lookup"><span data-stu-id="0c2e8-184">Element</span></span>|<span data-ttu-id="0c2e8-185">Opis</span><span class="sxs-lookup"><span data-stu-id="0c2e8-185">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c2e8-186">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0c2e8-186">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="0c2e8-187">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-187">Defines the security settings for the message.</span></span> <span data-ttu-id="0c2e8-188">Ten element jest typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="0c2e8-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0c2e8-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="0c2e8-190">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0c2e8-191">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="0c2e8-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0c2e8-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="0c2e8-193">Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0c2e8-194">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0c2e8-194">Parent Elements</span></span>

|<span data-ttu-id="0c2e8-195">Element</span><span class="sxs-lookup"><span data-stu-id="0c2e8-195">Element</span></span>|<span data-ttu-id="0c2e8-196">Opis</span><span class="sxs-lookup"><span data-stu-id="0c2e8-196">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c2e8-197">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="0c2e8-197">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0c2e8-198">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-198">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0c2e8-199">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c2e8-199">Remarks</span></span>

<span data-ttu-id="0c2e8-200">Federacja jest możliwością udostępniania tożsamości w wielu systemach na potrzeby uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="0c2e8-201">Te tożsamości mogą odwoływać się do użytkowników lub do maszyn.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="0c2e8-202">Federacyjny protokół HTTP obsługuje zabezpieczenia protokołu SOAP, a także zabezpieczenia w trybie mieszanym, ale nie obsługuje wyłącznie zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="0c2e8-203">To powiązanie zapewnia obsługę Windows Communication Foundation (WCF) dla protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-203">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="0c2e8-204">Usługi skonfigurowane przy użyciu tego powiązania muszą korzystać z transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-204">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="0c2e8-205">Powiązania składają się ze stosu elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="0c2e8-206">Stos elementów powiązania w</span><span class="sxs-lookup"><span data-stu-id="0c2e8-206">The stack of binding elements in</span></span>

<span data-ttu-id="0c2e8-207">`wsFederationHttpBinding`jest taka sama jak zawarte w`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="0c2e8-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="0c2e8-208"><xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> [ gdy\<> zabezpieczeń](security-of-wsfederationhttpbinding.md) ma ustawioną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-208">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="0c2e8-209">Kontroluje szczegóły ustawień zabezpieczeń wiadomości w [ \<> komunikatów.](message-element-of-wsfederationhttpbinding.md) `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="0c2e8-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="0c2e8-210">Należy zauważyć, że [ \<element Security >](security-of-wsfederationhttpbinding.md) zapewnia dostęp tylko wtedy, gdy nie można zmienić zabezpieczeń używanych przez powiązanie w momencie utworzenia powiązania.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-210">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="0c2e8-211">Udostępnia `wsFederationHttpBinding` również atrybut privacyNoticeAt do ustawiania i pobierania identyfikatora URI, w którym znajduje się powiadomienie o prywatności.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-211">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="0c2e8-212">Ochrona zasad jest szczególnie ważna w scenariuszach federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="0c2e8-213">Zalecenie polega na użyciu jakiejś formy zabezpieczeń, na przykład protokołu HTTPS, w celu ochrony zasad przed złośliwymi użytkownikami.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="0c2e8-214">W scenariuszach federacyjnych przy użyciu tego powiązania zasady usługi mogą mieć ważne informacje, takie jak klucz używany do szyfrowania tokenu wystawionego (SAML), typ oświadczeń do umieszczenia w tokenie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="0c2e8-215">Jeśli te zasady zostaną naruszone, osoba atakująca może odnaleźć klucz wystawionego tokenu prowadzący do dalszej manipulacji, ujawnienia informacji i innych złośliwych zachowań.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="0c2e8-216">Aby temu zapobiec, zasady muszą być pobierane bezpiecznie (na przykład przy użyciu protokołu HTTPS) z usługi.</span><span class="sxs-lookup"><span data-stu-id="0c2e8-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="0c2e8-217">Aby uzyskać więcej informacji na temat tego powiązania [, zobacz How to: Utwórz element WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0c2e8-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c2e8-218">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c2e8-218">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0c2e8-219">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c2e8-219">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="0c2e8-220">Instrukcje: Utwórz WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0c2e8-220">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="0c2e8-221">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0c2e8-221">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0c2e8-222">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="0c2e8-222">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0c2e8-223">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="0c2e8-223">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0c2e8-224">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="0c2e8-224">\<binding></span></span>](../../../misc/binding.md)
