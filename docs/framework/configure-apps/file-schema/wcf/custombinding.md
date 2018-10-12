---
title: '&lt;customBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 741f195a78c1716b95d8d4d88594207708ce6289
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123829"
---
# <a name="ltcustombindinggt"></a><span data-ttu-id="384b3-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="384b3-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="384b3-103">Zapewnia użytkownikowi pełną kontrolę nad stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="384b3-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="384b3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="384b3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="384b3-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="384b3-105">\<bindings></span></span>  
<span data-ttu-id="384b3-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="384b3-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384b3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="384b3-107">Syntax</span></span>  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="384b3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="384b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="384b3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="384b3-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="384b3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="384b3-110">Attributes</span></span>  
  
|<span data-ttu-id="384b3-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="384b3-111">Attribute</span></span>|<span data-ttu-id="384b3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="384b3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="384b3-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="384b3-113">closeTimeout</span></span>|<span data-ttu-id="384b3-114">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="384b3-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="384b3-115">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="384b3-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="384b3-116">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="384b3-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="384b3-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="384b3-117">name</span></span>|<span data-ttu-id="384b3-118">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="384b3-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="384b3-119">Ta wartość jest ciągu zdefiniowany przez użytkownika, który działa jako ciąg identyfikacyjny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="384b3-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="384b3-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="384b3-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="384b3-121">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="384b3-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="384b3-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="384b3-122">openTimeout</span></span>|<span data-ttu-id="384b3-123">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="384b3-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="384b3-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="384b3-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="384b3-125">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="384b3-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="384b3-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="384b3-126">receiveTimeout</span></span>|<span data-ttu-id="384b3-127">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="384b3-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="384b3-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="384b3-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="384b3-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="384b3-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="384b3-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="384b3-130">sendTimeout</span></span>|<span data-ttu-id="384b3-131">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="384b3-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="384b3-132">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="384b3-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="384b3-133">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="384b3-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="384b3-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="384b3-134">Child Elements</span></span>  
  
|<span data-ttu-id="384b3-135">Element</span><span class="sxs-lookup"><span data-stu-id="384b3-135">Element</span></span>|<span data-ttu-id="384b3-136">Opis</span><span class="sxs-lookup"><span data-stu-id="384b3-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="384b3-137">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="384b3-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="384b3-138">Określa dwukierunkowej wiadomości do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="384b3-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="384b3-139">Jest używany przy użyciu transportu, które nie zezwalają na komunikację dwukierunkowego natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="384b3-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="384b3-140">TCP, z drugiej strony, natywnie umożliwia dwukierunkowe komunikacji i nie wymaga użycia tego elementu powiązania usługi można wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="384b3-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="384b3-141">Klient musi ujawniać adres korespondencyjny upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="384b3-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="384b3-142">Ten adres klienta są dostarczane przez `ClientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="384b3-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="384b3-143">Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="384b3-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="384b3-144">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="384b3-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="384b3-145">Określa nazwę elementu równorzędnego protokołu Instrumentacji zarządzania Windows (PNRP, Peer Name Resolution Protocol) program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="384b3-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="384b3-146">Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="384b3-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="384b3-147">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="384b3-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="384b3-148">Określa ustawienie dla WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="384b3-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="384b3-149">Gdy ten element jest dodawany do niestandardowego powiązania, dokładnie obsługuje wynikowy kanału — gdy gwarancje dostarczenia.</span><span class="sxs-lookup"><span data-stu-id="384b3-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="384b3-150">Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="384b3-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="384b3-151">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="384b3-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="384b3-152">Określa opcje zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="384b3-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="384b3-153">Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="384b3-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="384b3-154">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="384b3-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="384b3-155">Określa ustawienia zabezpieczeń dla powiązania strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="384b3-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="384b3-156">Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="384b3-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="384b3-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="384b3-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="384b3-158">Określa, że powiązanie obsługuje przepływu transakcji i protokół, który będzie używany przez `transactionProtocol` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="384b3-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="384b3-159">Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="384b3-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="384b3-160">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="384b3-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="384b3-161">Określa opcje do przesyłania strumieniowego zabezpieczeń niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="384b3-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="384b3-162">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="384b3-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="384b3-163">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="384b3-163">Parent Elements</span></span>  
  
|<span data-ttu-id="384b3-164">Element</span><span class="sxs-lookup"><span data-stu-id="384b3-164">Element</span></span>|<span data-ttu-id="384b3-165">Opis</span><span class="sxs-lookup"><span data-stu-id="384b3-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="384b3-166">powiązania</span><span class="sxs-lookup"><span data-stu-id="384b3-166">bindings</span></span>|<span data-ttu-id="384b3-167">Zawiera wszystkie powiązania dla aplikacji Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="384b3-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="384b3-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="384b3-168">Remarks</span></span>  
 <span data-ttu-id="384b3-169">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="384b3-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="384b3-170">Moje Dodawanie elementów konfiguracji dla konkretnych jednostek można tworzyć specjalne powiązania dostosowanych do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="384b3-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="384b3-171">Na przykład użytkownik może łączyć `httpsTransport` sekcji `reliableSession` sekcji i `security` sekcję, aby utworzyć niezawodną i bezpieczną protokołu https na podstawie powiązania.</span><span class="sxs-lookup"><span data-stu-id="384b3-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="384b3-172">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementów konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="384b3-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="384b3-173">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="384b3-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="384b3-174">W każdym niestandardowego powiązania musi istnieć jeden i tylko jeden element transportu.</span><span class="sxs-lookup"><span data-stu-id="384b3-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="384b3-175">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="384b3-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="384b3-176">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="384b3-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="384b3-177">Zalecana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="384b3-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="384b3-178">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="384b3-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="384b3-179">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="384b3-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="384b3-180">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="384b3-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="384b3-181">Transportu</span><span class="sxs-lookup"><span data-stu-id="384b3-181">Transport</span></span>  
  
5.  <span data-ttu-id="384b3-182">Koder (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="384b3-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="384b3-183">Użyj niestandardowego powiązania, gdy jedno z powiązań dostarczanych przez system nie spełnia wymagania dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="384b3-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="384b3-184">Powiązanie niestandardowe może służyć, na przykład, aby umożliwić użycie nowego transportu lub Nowa usługa encoder w punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="384b3-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="384b3-185">Powiązanie niestandardowe jest konstruowany przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:</span><span class="sxs-lookup"><span data-stu-id="384b3-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="384b3-186">U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> umożliwiająca przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="384b3-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="384b3-187">Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> zapewniający sesji i kolejność mechanizmu, zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="384b3-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="384b3-188">Pojęcie to sesji mogą przechodzić pośredników SOAP i mechanizm transportu.</span><span class="sxs-lookup"><span data-stu-id="384b3-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="384b3-189">Następnym ekranem jest elementu powiązania zabezpieczeń opcjonalne, która zapewnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufności.</span><span class="sxs-lookup"><span data-stu-id="384b3-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="384b3-190">Następujące elementy powiązania zabezpieczeń są dostarczane przez Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="384b3-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="384b3-191">Następnie opcjonalne wzorce wiadomości są określone przez powiązanie elementów:</span><span class="sxs-lookup"><span data-stu-id="384b3-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="384b3-192">Następnie są uaktualnienia opcjonalne transportu/pomocników elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="384b3-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="384b3-193">Następnym ekranem jest element powiązania z kodowania komunikatu wymagane.</span><span class="sxs-lookup"><span data-stu-id="384b3-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="384b3-194">Możesz użyć własnego transportu lub użyj jednej z następującym komunikatem kodowanie powiązań:</span><span class="sxs-lookup"><span data-stu-id="384b3-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="384b3-195">W dolnej części jest element wymagany transportu.</span><span class="sxs-lookup"><span data-stu-id="384b3-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="384b3-196">Można używać własnego transportu lub użyj jednego z dostarczonych przez Windows Communication Foundation (WCF) elementów powiązania transportu:</span><span class="sxs-lookup"><span data-stu-id="384b3-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="384b3-197">Poniższa tabela podsumowuje opcje dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="384b3-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="384b3-198">Warstwa</span><span class="sxs-lookup"><span data-stu-id="384b3-198">Layer</span></span>|<span data-ttu-id="384b3-199">Opcje</span><span class="sxs-lookup"><span data-stu-id="384b3-199">Options</span></span>|<span data-ttu-id="384b3-200">Wymagane</span><span class="sxs-lookup"><span data-stu-id="384b3-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="384b3-201">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="384b3-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="384b3-202">Nie</span><span class="sxs-lookup"><span data-stu-id="384b3-202">No</span></span>|  
|<span data-ttu-id="384b3-203">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="384b3-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="384b3-204">Nie</span><span class="sxs-lookup"><span data-stu-id="384b3-204">No</span></span>|  
|<span data-ttu-id="384b3-205">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="384b3-205">Security</span></span>|<span data-ttu-id="384b3-206">Symetryczne, asymetryczne i Transport niskiego poziomu</span><span class="sxs-lookup"><span data-stu-id="384b3-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="384b3-207">Nie</span><span class="sxs-lookup"><span data-stu-id="384b3-207">No</span></span>|  
|<span data-ttu-id="384b3-208">Zmiana kształtu</span><span class="sxs-lookup"><span data-stu-id="384b3-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="384b3-209">Nie</span><span class="sxs-lookup"><span data-stu-id="384b3-209">No</span></span>|  
|<span data-ttu-id="384b3-210">Transport uaktualnień</span><span class="sxs-lookup"><span data-stu-id="384b3-210">Transport Upgrades</span></span>|<span data-ttu-id="384b3-211">Strumień protokołu SSL, strumienia Windows elementu równorzędnego programu rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="384b3-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="384b3-212">Nie</span><span class="sxs-lookup"><span data-stu-id="384b3-212">No</span></span>|  
|<span data-ttu-id="384b3-213">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="384b3-213">Encoding</span></span>|<span data-ttu-id="384b3-214">Tekst, Binary MTOM, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="384b3-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="384b3-215">Tak</span><span class="sxs-lookup"><span data-stu-id="384b3-215">Yes</span></span>|  
|<span data-ttu-id="384b3-216">Transportu</span><span class="sxs-lookup"><span data-stu-id="384b3-216">Transport</span></span>|<span data-ttu-id="384b3-217">Odmian HTTP, HTTPS, TCP i nazwane potoki usługi MSMQ, niestandardowe</span><span class="sxs-lookup"><span data-stu-id="384b3-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="384b3-218">Tak</span><span class="sxs-lookup"><span data-stu-id="384b3-218">Yes</span></span>|  
  
 <span data-ttu-id="384b3-219">Ponadto można zdefiniować własne elementy powiązania i wstawione między dowolnymi poprzedniej warstwy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="384b3-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="384b3-220">Aby uzyskać informacje dotyczące sposobu używania niestandardowego powiązania, aby zmodyfikować powiązania dostarczane przez system, zobacz [porady: dostosowywanie powiązania System-Provided](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="384b3-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
1.  
  
## <a name="see-also"></a><span data-ttu-id="384b3-221">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="384b3-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="384b3-222">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="384b3-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="384b3-223">Powiązania</span><span class="sxs-lookup"><span data-stu-id="384b3-223">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="384b3-224">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="384b3-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="384b3-225">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="384b3-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="384b3-226">customBinding — Element</span><span class="sxs-lookup"><span data-stu-id="384b3-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="384b3-227">Powiązania</span><span class="sxs-lookup"><span data-stu-id="384b3-227">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="384b3-228">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="384b3-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="384b3-229">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="384b3-229">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
