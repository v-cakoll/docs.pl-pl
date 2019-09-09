---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 1fd0a12b62c416ce71946e59e7868abc7638a274
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398124"
---
# <a name="custombinding"></a><span data-ttu-id="7a0ae-101">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7a0ae-101">\<customBinding></span></span>

<span data-ttu-id="7a0ae-102">Zapewnia pełną kontrolę nad stosem obsługi komunikatów dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="7a0ae-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a0ae-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a0ae-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7a0ae-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7a0ae-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7a0ae-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7a0ae-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<niestandardowy >Binding**</span><span class="sxs-lookup"><span data-stu-id="7a0ae-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="7a0ae-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a0ae-107">Syntax</span></span>

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a0ae-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a0ae-108">Attributes and Elements</span></span>

<span data-ttu-id="7a0ae-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-109">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="7a0ae-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a0ae-110">Attributes</span></span>

|<span data-ttu-id="7a0ae-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7a0ae-111">Attribute</span></span>|<span data-ttu-id="7a0ae-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7a0ae-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7a0ae-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="7a0ae-113">closeTimeout</span></span>|<span data-ttu-id="7a0ae-114"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7a0ae-115">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a0ae-116">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-116">The default is 00:01:00.</span></span>|
|<span data-ttu-id="7a0ae-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="7a0ae-117">name</span></span>|<span data-ttu-id="7a0ae-118">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7a0ae-119">Ta wartość jest ciągiem zdefiniowanym przez użytkownika, który działa jako ciąg identyfikacyjny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="7a0ae-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7a0ae-121">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a0ae-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="7a0ae-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="7a0ae-122">openTimeout</span></span>|<span data-ttu-id="7a0ae-123"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7a0ae-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a0ae-125">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-125">The default is 00:01:00.</span></span>|
|<span data-ttu-id="7a0ae-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="7a0ae-126">receiveTimeout</span></span>|<span data-ttu-id="7a0ae-127"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7a0ae-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a0ae-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-129">The default is 00:01:00.</span></span>|
|<span data-ttu-id="7a0ae-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="7a0ae-130">sendTimeout</span></span>|<span data-ttu-id="7a0ae-131"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7a0ae-132">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a0ae-133">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-133">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7a0ae-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a0ae-134">Child Elements</span></span>

|<span data-ttu-id="7a0ae-135">Element</span><span class="sxs-lookup"><span data-stu-id="7a0ae-135">Element</span></span>|<span data-ttu-id="7a0ae-136">Opis</span><span class="sxs-lookup"><span data-stu-id="7a0ae-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a0ae-137">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="7a0ae-137">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="7a0ae-138">Określa komunikat dwukierunkowy dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="7a0ae-139">Jest on używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="7a0ae-140">Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="7a0ae-141">Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="7a0ae-142">Ten adres klienta jest dostarczany przez `ClientBaseAddress` atrybut.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="7a0ae-143">Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="7a0ae-144">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="7a0ae-144">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="7a0ae-145">Określa program rozpoznawania nazw elementów równorzędnych protokołu PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="7a0ae-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="7a0ae-146">Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="7a0ae-147">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="7a0ae-147">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="7a0ae-148">Określa ustawienie dla obsługi komunikatów w usłudze WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="7a0ae-149">Gdy ten element zostanie dodany do niestandardowego powiązania, otrzymany kanał może obsługiwać tylko jednokrotne gwarancje dostarczania.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="7a0ae-150">Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="7a0ae-151">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7a0ae-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="7a0ae-152">Określa opcje zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="7a0ae-153">Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="7a0ae-154">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="7a0ae-154">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="7a0ae-155">Określa ustawienia zabezpieczeń dla powiązania strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="7a0ae-156">Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="7a0ae-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="7a0ae-157">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="7a0ae-158">Określa, że powiązanie obsługuje przepływ transakcji, oraz protokołu, który ma być używany przez `transactionProtocol` atrybut.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="7a0ae-159">Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="7a0ae-160">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="7a0ae-160">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="7a0ae-161">Określa opcje zabezpieczeń przesyłania strumieniowego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="7a0ae-162">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7a0ae-163">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a0ae-163">Parent Elements</span></span>

|<span data-ttu-id="7a0ae-164">Element</span><span class="sxs-lookup"><span data-stu-id="7a0ae-164">Element</span></span>|<span data-ttu-id="7a0ae-165">Opis</span><span class="sxs-lookup"><span data-stu-id="7a0ae-165">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="7a0ae-166">powiązania</span><span class="sxs-lookup"><span data-stu-id="7a0ae-166">bindings</span></span>|<span data-ttu-id="7a0ae-167">Zawiera wszystkie powiązania dla Windows Communication Foundation aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7a0ae-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a0ae-168">Remarks</span></span>

<span data-ttu-id="7a0ae-169">Niestandardowe powiązania zapewniają pełną kontrolę nad stosem obsługi komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="7a0ae-170">Można utworzyć specjalne powiązania dostosowane, dodając elementy konfiguracji dla określonych jednostek.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="7a0ae-171">Na przykład użytkownik może połączyć `httpsTransport` sekcję, sekcję i `security` sekcję `reliableSession` , aby utworzyć niezawodne i bezpieczne powiązanie https.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="7a0ae-172">Pojedyncze powiązanie definiuje stos komunikatów przez określenie elementów konfiguracji dla elementów stosu w kolejności, w jakiej występują na stosie.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="7a0ae-173">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="7a0ae-174">W każdym powiązaniu niestandardowym musi istnieć jeden i tylko jeden element transportu.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="7a0ae-175">Bez tego elementu stos komunikatów jest niekompletny.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-175">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="7a0ae-176">Kolejność, w której elementy pojawiają się w kwestiach stosu, ponieważ jest to kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="7a0ae-177">Zalecana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="7a0ae-177">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="7a0ae-178">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="7a0ae-178">Transactions (optional)</span></span>

2. <span data-ttu-id="7a0ae-179">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="7a0ae-179">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="7a0ae-180">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="7a0ae-180">Security (optional)</span></span>

4. <span data-ttu-id="7a0ae-181">Transportu</span><span class="sxs-lookup"><span data-stu-id="7a0ae-181">Transport</span></span>

5. <span data-ttu-id="7a0ae-182">Koder (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="7a0ae-182">Encoder (optional)</span></span>

<span data-ttu-id="7a0ae-183">Użyj niestandardowego powiązania, gdy jedno z powiązań dostarczonych przez system nie spełnia wymagań usługi.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="7a0ae-184">Można na przykład użyć niestandardowego powiązania, aby umożliwić korzystanie z nowego lub nowego kodera w punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="7a0ae-185">Niestandardowe powiązanie jest konstruowane przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> kolekcji elementów powiązania, które są "ułożone" w określonej kolejności:</span><span class="sxs-lookup"><span data-stu-id="7a0ae-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="7a0ae-186">U góry jest opcjonalne <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , które umożliwia przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="7a0ae-187">Następnie jest opcjonalne <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> , które udostępnia mechanizm sesji i kolejności, zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="7a0ae-188">To pojęcie sesji może przekroczyć pośredniki SOAP i transportu.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="7a0ae-189">Dalej jest opcjonalny element powiązania zabezpieczeń, który zapewnia funkcje zabezpieczeń, takie jak autoryzacja, uwierzytelnianie, ochrona i poufność.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="7a0ae-190">Następujące elementy powiązań zabezpieczeń są udostępniane przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="7a0ae-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="7a0ae-191">Następnie są opcjonalne wzorce komunikatów określone przez elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="7a0ae-191">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="7a0ae-192">Poniżej przedstawiono opcjonalne elementy powiązania uaktualnienia/pomocnika transportu:</span><span class="sxs-lookup"><span data-stu-id="7a0ae-192">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="7a0ae-193">Następnie jest wymagany element powiązania kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="7a0ae-194">Możesz użyć własnego transportu lub użyć jednego z następujących powiązań kodowania komunikatów:</span><span class="sxs-lookup"><span data-stu-id="7a0ae-194">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="7a0ae-195">U dołu jest wymagany element transportu.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="7a0ae-196">Możesz użyć własnego transportu lub użyć jednego z elementów powiązania transportowego dostarczonych przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="7a0ae-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="7a0ae-197">Poniższa tabela zawiera podsumowanie opcji dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-197">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="7a0ae-198">Warstwa</span><span class="sxs-lookup"><span data-stu-id="7a0ae-198">Layer</span></span>|<span data-ttu-id="7a0ae-199">Opcje</span><span class="sxs-lookup"><span data-stu-id="7a0ae-199">Options</span></span>|<span data-ttu-id="7a0ae-200">Wymagane</span><span class="sxs-lookup"><span data-stu-id="7a0ae-200">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="7a0ae-201">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="7a0ae-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="7a0ae-202">Nie</span><span class="sxs-lookup"><span data-stu-id="7a0ae-202">No</span></span>|
|<span data-ttu-id="7a0ae-203">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="7a0ae-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="7a0ae-204">Nie</span><span class="sxs-lookup"><span data-stu-id="7a0ae-204">No</span></span>|
|<span data-ttu-id="7a0ae-205">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7a0ae-205">Security</span></span>|<span data-ttu-id="7a0ae-206">Symetryczne, asymetryczne, na poziomie transportu</span><span class="sxs-lookup"><span data-stu-id="7a0ae-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="7a0ae-207">Nie</span><span class="sxs-lookup"><span data-stu-id="7a0ae-207">No</span></span>|
|<span data-ttu-id="7a0ae-208">Zmiana kształtu</span><span class="sxs-lookup"><span data-stu-id="7a0ae-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="7a0ae-209">Nie</span><span class="sxs-lookup"><span data-stu-id="7a0ae-209">No</span></span>|
|<span data-ttu-id="7a0ae-210">Uaktualnienia transportu</span><span class="sxs-lookup"><span data-stu-id="7a0ae-210">Transport Upgrades</span></span>|<span data-ttu-id="7a0ae-211">Strumień SSL, strumień systemu Windows, program rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="7a0ae-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="7a0ae-212">Nie</span><span class="sxs-lookup"><span data-stu-id="7a0ae-212">No</span></span>|
|<span data-ttu-id="7a0ae-213">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="7a0ae-213">Encoding</span></span>|<span data-ttu-id="7a0ae-214">Tekst, dane binarne, MTOM, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7a0ae-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="7a0ae-215">Tak</span><span class="sxs-lookup"><span data-stu-id="7a0ae-215">Yes</span></span>|
|<span data-ttu-id="7a0ae-216">Transportu</span><span class="sxs-lookup"><span data-stu-id="7a0ae-216">Transport</span></span>|<span data-ttu-id="7a0ae-217">TCP, nazwane potoki, HTTP, HTTPS, typy usługi MSMQ, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7a0ae-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="7a0ae-218">Tak</span><span class="sxs-lookup"><span data-stu-id="7a0ae-218">Yes</span></span>|

<span data-ttu-id="7a0ae-219">Ponadto można definiować własne elementy powiązania i wstawiać je między wszystkimi wcześniej zdefiniowanymi warstwami.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="7a0ae-220">Aby uzyskać informacje na temat sposobu użycia niestandardowego powiązania do modyfikacji powiązania dostarczonego przez system, zobacz [How to: Dostosuj powiązanie](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)dostarczone przez system.</span><span class="sxs-lookup"><span data-stu-id="7a0ae-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a0ae-221">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a0ae-221">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7a0ae-222">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="7a0ae-222">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="7a0ae-223">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7a0ae-223">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7a0ae-224">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="7a0ae-224">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7a0ae-225">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7a0ae-225">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7a0ae-226">CustomBinding — element</span><span class="sxs-lookup"><span data-stu-id="7a0ae-226">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="7a0ae-227">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7a0ae-227">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7a0ae-228">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7a0ae-228">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7a0ae-229">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7a0ae-229">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
