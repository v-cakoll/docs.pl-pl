---
title: '&lt;customBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 267bf183e40c8647959e97ae479d78cfe41367b2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustombindinggt"></a>&lt;customBinding&gt;
Zapewnia użytkownikowi pełną kontrolę nad stosem obsługi wiadomości.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość jest ciągiem zdefiniowane przez użytkownika pełniącym rolę ciągu identyfikacyjnego niestandardowego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|właściwości sendTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<compositeDuplex >](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|Określa dwukierunkowej wiadomości do niestandardowego powiązania. Jest ona używana z transportu, które nie zezwalają na komunikacji dupleksowej natywnie, na przykład HTTP. TCP, natomiast natywnie umożliwia komunikacji dupleksowej i nie wymaga użycia tego elementu powiązania dla usługi wysłać wiadomości zwrotnie do klienta.<br /><br /> Klient musi ujawniać adres usługi upewnić się, skontaktuj się z pomocą i nawiązania połączenia. Ten adres klienta jest zapewniana przez `ClientBaseAddress` atrybutu.<br /><br /> Ten element jest typu <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.|  
|[\<pnrpPeerResolver >](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|Określa nazwę elementu równorzędnego rozpoznawania protokołu PNRP (Peer Name) program rozpoznawania nazw. Ten element jest typu <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.|  
|[\<reliableSession >](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|Określa ustawienie dla WS-Reliable Messaging. Gdy ten element jest dodawany do niestandardowego powiązania, wynikowy kanał obsługuje dokładnie — raz gwarancje dostarczenia. Ten element jest typu <xref:System.ServiceModel.Configuration.ReliableSessionElement>.|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń niestandardowego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.SecurityElement>.|  
|[\<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|Określa ustawienia zabezpieczeń dla powiązania strumienia SSL. Ten element jest typu <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.|  
|[\<transactionFlow >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|Określa, czy wiązanie obsługuje przepływu transakcji i Protokół do użycia przez `transactionProtocol` atrybutu. Ten element jest typu <xref:System.ServiceModel.Configuration.TransactionFlowElement>.|  
|[\<Obiekt windowsStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|Określa opcje do przesyłania strumieniowego zabezpieczeń niestandardowego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązania|Zawiera wszystkie powiązania dla aplikacji Windows Communication Foundation.|  
  
## <a name="remarks"></a>Uwagi  
 Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości WCF. Można utworzyć specjalne powiązania dopasowane Moje Dodawanie elementów konfiguracji dla określonej jednostki. Na przykład użytkownik może łączyć `httpsTransport` sekcji `reliableSession` sekcji i `security` sekcji, aby utworzyć https i niezawodności na podstawie powiązania.  
  
 Powiązanie poszczególnych definiuje stosu wiadomości, określając elementy konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie. Każdy element definiuje i konfiguruje jeden element stosu. W każdym niestandardowego powiązania musi istnieć jeden i tylko jeden element transportu. Bez tego elementu stosem obsługi wiadomości jest niekompletna.  
  
 Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacji są stosowane do wiadomości. Zalecana kolejność elementów stosu jest następujący:  
  
1.  Transakcje (opcjonalnie)  
  
2.  Niezawodnej obsługi komunikatów (opcjonalnie)  
  
3.  Zabezpieczeń (opcjonalnie)  
  
4.  Transportu  
  
5.  Koder (opcjonalnie)  
  
 Jeśli jedno z powiązań dostarczane przez system nie spełnia wymagania dotyczące usługi, należy użyć niestandardowego powiązania. Niestandardowego powiązania można, na przykład, aby umożliwić użycie nowego transportu lub nowe koder na punkt końcowy usługi.  
  
 Wiązanie niestandardowe jest tworzony przy użyciu jednej z <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:  
  
-   U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> umożliwiająca przepływu transakcji.  
  
-   Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> zapewnia sesji i kolejność mechanizmu zgodnie z definicją w specyfikacji WS-ReliableMessaging. To pojęcie sesji mogą przechodzić pośredników SOAP i transportu.  
  
-   Następnie jest elementu powiązania zabezpieczeń opcjonalne, która udostępnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufności. Następujące elementy powiązania zabezpieczeń są dostarczane przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   Obok opcjonalne wzorce wiadomości są określone przez elementy powiązania:  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   Obok są opcjonalne transportu uaktualnień/pomocników elementy powiązania:  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   Obok jest element powiązania kodowania komunikatu wymagane. Można użyć własnych transportu lub użyj jednej z poniższych kodowanie powiązań:  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   W dolnej części jest element wymagany transportu. Można użyć własnych transportu lub użyj jednej z elementami pochodzącymi powiązania transportu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 W poniższej tabeli przedstawiono opcje dla każdej warstwy.  
  
|Warstwy|Opcje|Wymagane|  
|-----------|-------------|--------------|  
|Przepływ transakcji|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Nie|  
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Nie|  
|Zabezpieczenia|Symetryczne, asymetrycznego, poziomu transportu|Nie|  
|Zmiana kształtu|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Nie|  
|Transport uaktualnień|Strumień protokołu SSL, strumienia systemu Windows, program rozpoznawania elementów równorzędnych|Nie|  
|Kodowanie|Tekst, Binary, MTOM, niestandardowe|Tak|  
|Transportu|TCP i nazwane potoki, HTTP i HTTPS, odmian usługi MSMQ, niestandardowe|Tak|  
  
 Ponadto można definiować własne elementy powiązania i wstawione między dowolnymi z poprzednim zdefiniowane warstwy.  
  
 Aby uzyskać informacje dotyczące sposobu używania niestandardowego powiązania, aby zmodyfikować powiązania dostarczane przez system, zobacz [porady: dostosowywanie powiązania System-Provided](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
1.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [customBinding — Element](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez System](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
