---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 60ce3cdfd7c78d152c71cdd652532cc96a6be296
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481122"
---
# <a name="custombinding"></a><span data-ttu-id="b0f87-101">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b0f87-101">\<customBinding></span></span>

<span data-ttu-id="b0f87-102">Zapewnia użytkownikowi pełną kontrolę nad stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0f87-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="b0f87-103">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="b0f87-103">\<system.serviceModel>\\</span></span>
<span data-ttu-id="b0f87-104">\<powiązania > \\</span><span class="sxs-lookup"><span data-stu-id="b0f87-104">\<bindings>\\</span></span>
<span data-ttu-id="b0f87-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b0f87-105">\<customBinding></span></span>

## <a name="syntax"></a><span data-ttu-id="b0f87-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0f87-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b0f87-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b0f87-107">Attributes and Elements</span></span>

<span data-ttu-id="b0f87-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0f87-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="b0f87-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0f87-109">Attributes</span></span>

|<span data-ttu-id="b0f87-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b0f87-110">Attribute</span></span>|<span data-ttu-id="b0f87-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b0f87-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b0f87-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="b0f87-112">closeTimeout</span></span>|<span data-ttu-id="b0f87-113">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="b0f87-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b0f87-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0f87-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b0f87-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="b0f87-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="b0f87-116">name</span></span>|<span data-ttu-id="b0f87-117">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b0f87-118">Ta wartość jest ciągu zdefiniowany przez użytkownika, który działa jako ciąg identyfikacyjny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="b0f87-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="b0f87-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b0f87-120">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b0f87-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="b0f87-121">openTimeout</span><span class="sxs-lookup"><span data-stu-id="b0f87-121">openTimeout</span></span>|<span data-ttu-id="b0f87-122">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="b0f87-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b0f87-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0f87-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b0f87-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="b0f87-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="b0f87-125">receiveTimeout</span></span>|<span data-ttu-id="b0f87-126">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b0f87-127">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0f87-128">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b0f87-128">The default is 00:01:00.</span></span>|
|<span data-ttu-id="b0f87-129">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="b0f87-129">sendTimeout</span></span>|<span data-ttu-id="b0f87-130">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b0f87-131">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b0f87-132">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b0f87-132">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b0f87-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0f87-133">Child Elements</span></span>

|<span data-ttu-id="b0f87-134">Element</span><span class="sxs-lookup"><span data-stu-id="b0f87-134">Element</span></span>|<span data-ttu-id="b0f87-135">Opis</span><span class="sxs-lookup"><span data-stu-id="b0f87-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0f87-136">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="b0f87-136">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="b0f87-137">Określa dwukierunkowej wiadomości do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="b0f87-138">Jest używany przy użyciu transportu, które nie zezwalają na komunikację dwukierunkowego natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="b0f87-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="b0f87-139">TCP, z drugiej strony, natywnie umożliwia dwukierunkowe komunikacji i nie wymaga użycia tego elementu powiązania usługi można wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="b0f87-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="b0f87-140">Klient musi ujawniać adres korespondencyjny upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="b0f87-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="b0f87-141">Ten adres klienta są dostarczane przez `ClientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b0f87-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="b0f87-142">Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="b0f87-143">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="b0f87-143">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="b0f87-144">Określa nazwę elementu równorzędnego protokołu Instrumentacji zarządzania Windows (PNRP, Peer Name Resolution Protocol) program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="b0f87-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="b0f87-145">Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="b0f87-146">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="b0f87-146">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="b0f87-147">Określa ustawienie dla WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="b0f87-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="b0f87-148">Gdy ten element jest dodawany do niestandardowego powiązania, dokładnie obsługuje wynikowy kanału — gdy gwarancje dostarczenia.</span><span class="sxs-lookup"><span data-stu-id="b0f87-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="b0f87-149">Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="b0f87-150">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="b0f87-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="b0f87-151">Określa opcje zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="b0f87-152">Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="b0f87-153">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="b0f87-153">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="b0f87-154">Określa ustawienia zabezpieczeń dla powiązania strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="b0f87-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="b0f87-155">Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="b0f87-156">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="b0f87-156">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="b0f87-157">Określa, że powiązanie obsługuje przepływu transakcji i protokół, który będzie używany przez `transactionProtocol` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b0f87-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="b0f87-158">Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="b0f87-159">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="b0f87-159">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="b0f87-160">Określa opcje do przesyłania strumieniowego zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="b0f87-161">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b0f87-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b0f87-162">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0f87-162">Parent Elements</span></span>

|<span data-ttu-id="b0f87-163">Element</span><span class="sxs-lookup"><span data-stu-id="b0f87-163">Element</span></span>|<span data-ttu-id="b0f87-164">Opis</span><span class="sxs-lookup"><span data-stu-id="b0f87-164">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="b0f87-165">powiązania</span><span class="sxs-lookup"><span data-stu-id="b0f87-165">bindings</span></span>|<span data-ttu-id="b0f87-166">Zawiera wszystkie powiązania dla aplikacji Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="b0f87-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b0f87-167">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0f87-167">Remarks</span></span>

<span data-ttu-id="b0f87-168">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b0f87-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="b0f87-169">Moje Dodawanie elementów konfiguracji dla konkretnych jednostek można tworzyć specjalne powiązania dostosowanych do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="b0f87-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="b0f87-170">Na przykład użytkownik może łączyć `httpsTransport` sekcji `reliableSession` sekcji i `security` sekcję, aby utworzyć niezawodną i bezpieczną protokołu https na podstawie powiązania.</span><span class="sxs-lookup"><span data-stu-id="b0f87-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="b0f87-171">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementów konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="b0f87-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="b0f87-172">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="b0f87-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="b0f87-173">W każdym niestandardowego powiązania musi istnieć jeden i tylko jeden element transportu.</span><span class="sxs-lookup"><span data-stu-id="b0f87-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="b0f87-174">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="b0f87-174">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="b0f87-175">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0f87-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="b0f87-176">Zalecana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="b0f87-176">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="b0f87-177">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b0f87-177">Transactions (optional)</span></span>

2. <span data-ttu-id="b0f87-178">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b0f87-178">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="b0f87-179">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b0f87-179">Security (optional)</span></span>

4. <span data-ttu-id="b0f87-180">Transport</span><span class="sxs-lookup"><span data-stu-id="b0f87-180">Transport</span></span>

5. <span data-ttu-id="b0f87-181">Koder (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b0f87-181">Encoder (optional)</span></span>

<span data-ttu-id="b0f87-182">Użyj niestandardowego powiązania, gdy jedno z powiązań dostarczanych przez system nie spełnia wymagania dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="b0f87-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="b0f87-183">Powiązanie niestandardowe może służyć, na przykład, aby umożliwić użycie nowego transportu lub Nowa usługa encoder w punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="b0f87-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="b0f87-184">Powiązanie niestandardowe jest konstruowany przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:</span><span class="sxs-lookup"><span data-stu-id="b0f87-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="b0f87-185">U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> umożliwiająca przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="b0f87-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="b0f87-186">Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> zapewniający sesji i kolejność mechanizmu, zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="b0f87-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="b0f87-187">Pojęcie to sesji mogą przechodzić pośredników SOAP i mechanizm transportu.</span><span class="sxs-lookup"><span data-stu-id="b0f87-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="b0f87-188">Następnym ekranem jest elementu powiązania zabezpieczeń opcjonalne, która zapewnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufności.</span><span class="sxs-lookup"><span data-stu-id="b0f87-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="b0f87-189">Następujące elementy powiązania zabezpieczeń są dostarczane przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="b0f87-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="b0f87-190">Następnie opcjonalne wzorce wiadomości są określone przez powiązanie elementów:</span><span class="sxs-lookup"><span data-stu-id="b0f87-190">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="b0f87-191">Następnie są uaktualnienia opcjonalne transportu/pomocników elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="b0f87-191">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="b0f87-192">Następnym ekranem jest element powiązania z kodowania komunikatu wymagane.</span><span class="sxs-lookup"><span data-stu-id="b0f87-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="b0f87-193">Możesz użyć własnego transportu lub użyj jednej z następującym komunikatem kodowanie powiązań:</span><span class="sxs-lookup"><span data-stu-id="b0f87-193">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="b0f87-194">W dolnej części jest element wymagany transportu.</span><span class="sxs-lookup"><span data-stu-id="b0f87-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="b0f87-195">Można używać własnego transportu lub użyj jednego z dostarczonych przez Windows Communication Foundation (WCF) elementów powiązania transportu:</span><span class="sxs-lookup"><span data-stu-id="b0f87-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="b0f87-196">Poniższa tabela podsumowuje opcje dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="b0f87-196">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="b0f87-197">Warstwa</span><span class="sxs-lookup"><span data-stu-id="b0f87-197">Layer</span></span>|<span data-ttu-id="b0f87-198">Opcje</span><span class="sxs-lookup"><span data-stu-id="b0f87-198">Options</span></span>|<span data-ttu-id="b0f87-199">Wymagane</span><span class="sxs-lookup"><span data-stu-id="b0f87-199">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="b0f87-200">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="b0f87-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="b0f87-201">Nie</span><span class="sxs-lookup"><span data-stu-id="b0f87-201">No</span></span>|
|<span data-ttu-id="b0f87-202">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="b0f87-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="b0f87-203">Nie</span><span class="sxs-lookup"><span data-stu-id="b0f87-203">No</span></span>|
|<span data-ttu-id="b0f87-204">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="b0f87-204">Security</span></span>|<span data-ttu-id="b0f87-205">Symetryczne, asymetryczne i Transport niskiego poziomu</span><span class="sxs-lookup"><span data-stu-id="b0f87-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="b0f87-206">Nie</span><span class="sxs-lookup"><span data-stu-id="b0f87-206">No</span></span>|
|<span data-ttu-id="b0f87-207">Zmiana kształtu</span><span class="sxs-lookup"><span data-stu-id="b0f87-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="b0f87-208">Nie</span><span class="sxs-lookup"><span data-stu-id="b0f87-208">No</span></span>|
|<span data-ttu-id="b0f87-209">Transport uaktualnień</span><span class="sxs-lookup"><span data-stu-id="b0f87-209">Transport Upgrades</span></span>|<span data-ttu-id="b0f87-210">Strumień protokołu SSL, strumienia Windows elementu równorzędnego programu rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="b0f87-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="b0f87-211">Nie</span><span class="sxs-lookup"><span data-stu-id="b0f87-211">No</span></span>|
|<span data-ttu-id="b0f87-212">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="b0f87-212">Encoding</span></span>|<span data-ttu-id="b0f87-213">Tekst, Binary MTOM, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b0f87-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="b0f87-214">Tak</span><span class="sxs-lookup"><span data-stu-id="b0f87-214">Yes</span></span>|
|<span data-ttu-id="b0f87-215">Transport</span><span class="sxs-lookup"><span data-stu-id="b0f87-215">Transport</span></span>|<span data-ttu-id="b0f87-216">Odmian HTTP, HTTPS, TCP i nazwane potoki usługi MSMQ, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b0f87-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="b0f87-217">Tak</span><span class="sxs-lookup"><span data-stu-id="b0f87-217">Yes</span></span>|

<span data-ttu-id="b0f87-218">Ponadto można zdefiniować własne elementy powiązania i wstawione między dowolnymi poprzedniej warstwy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0f87-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="b0f87-219">Aby uzyskać informacje dotyczące sposobu używania niestandardowego powiązania, aby zmodyfikować powiązania dostarczane przez system, zobacz [jak: Dostosuj powiązania dostarczane przez System](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="b0f87-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0f87-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0f87-220">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b0f87-221">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b0f87-221">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="b0f87-222">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b0f87-222">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b0f87-223">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b0f87-223">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b0f87-224">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b0f87-224">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b0f87-225">customBinding — Element</span><span class="sxs-lookup"><span data-stu-id="b0f87-225">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="b0f87-226">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b0f87-226">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b0f87-227">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="b0f87-227">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b0f87-228">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="b0f87-228">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
