---
title: "Protokoły zabezpieczeń wersja 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a>Protokoły zabezpieczeń wersja 1.0
Protokoły zabezpieczeń usług sieci Web zapewniają mechanizmy zabezpieczeń usług sieci Web, które obejmują wszystkie istniejącym w przedsiębiorstwie wiadomości wymagania dotyczące zabezpieczeń. W tej sekcji opisano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] szczegółów w wersji 1.0 (w <xref:System.ServiceModel.Channels.SecurityBindingElement>) dla następujących sieci Web usług protokołów zabezpieczeń.  
  
|Specyfikacja/dokumentu|Łącze|  
|-|-|  
|WSS: Zabezpieczenia komunikatów SOAP 1.0|http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-SOAP-Message-Security-1.0.PDF|  
|Programu WSS: Profil Token nazwy użytkownika 1.0|http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-username-token-profile-1.0.PDF|  
|WSS: X509 Token profilu 1.0|http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-x509-token-profile-1.0.PDF|  
|Programu WSS: SAML 1.1 Token profilu 1.0|http://docs.oasis-open.org/WSS/oasis-WSS-SAML-token-profile-1.0.PDF|  
|Programu WSS: Zabezpieczenia komunikatów SOAP 1.1|http://www.oasis-open.org/committees/Download.php/16790/WSS-V1.1-spec-OS-SOAPMessageSecurity.PDF|  
|1.1 tokenu profilu programu WSS nazwy użytkownika|http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-username-token-profile-1.0.PDF|  
|Programu WSS: Profil tokenu X.509 1.1|http://www.oasis-open.org/committees/Download.php/16785/WSS-V1.1-spec-OS-x509TokenProfile.PDF|  
|WSS: 1.1 profilu Token protokołu Kerberos|http://www.oasis-open.org/committees/Download.php/16788/WSS-V1.1-spec-OS-KerberosTokenProfile.PDF|  
|Programu WSS: SAML 1.1 Token 1.1 profilu|http://www.oasis-open.org/committees/Download.php/16768/WSS-V1.1-spec-OS-SAMLTokenProfile.PDF|  
|Zabezpieczenia WS konwersacji|http://msdn.microsoft.com/ws/2005/02/ws-Secure-Conversation/|  
|WS-Trust|http://msdn.microsoft.com/ws/2005/02/WS-Trust/|  
|Uwaga aplikacji:<br /><br /> Za pomocą protokołu WS-Trust na uzgadnianie protokołu TLS|Do opublikowania|  
|Uwaga aplikacji:<br /><br /> Za pomocą protokołu WS-Trust dla SPNEGO|Do opublikowania|  
|Uwaga aplikacji:<br /><br /> Usługi sieci Web adresowanie odwołania do punktu końcowego i tożsamość|Do opublikowania|  
|WS-SecurityPolicy 1.1<br /><br /> (2005/07)|http://msdn.microsoft.com/ws/2005/07/WS-Security-Policy/<br /><br /> zmienione erracie przesłane do http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html Komitet Techniczny WS-SX OASIS|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], wersja 1, zapewnia 17 tryby uwierzytelniania, które mogą służyć jako podstawa dla konfiguracji zabezpieczeń usług sieci Web. Każdego trybu jest zoptymalizowana pod kątem wspólny zbiór wymagania dotyczące wdrażania, takie jak:  
  
-   Poświadczenia używane do uwierzytelniania klienta i usługi.  
  
-   Mechanizmy ochrony zabezpieczeń transportu lub wiadomości.  
  
-   Wzorce wymiany wiadomości.  
  
|Tryb uwierzytelniania|Uwierzytelnianie klienta|Uwierzytelnianie serwera|Tryb|  
|-------------------------|---------------------------|---------------------------|----------|  
|UserNameOverTransport|Nazwa użytkownika/hasło|X509|Transportu|  
|CertificateOverTransport|X509|X509|Transportu|  
|KerberosOverTransport|Windows|X509|Transportu|  
|IssuedTokenOverTransport|Federacyjna|X509|Transportu|  
|SspiNegotiatedOverTransport|Wynegocjowane interfejsu Sspi systemu Windows|Wynegocjowane interfejsu Sspi systemu Windows|Transportu|  
|AnonymousForCertificate|Brak|X509|Komunikat|  
|UserNameForCertificate|Nazwa użytkownika/hasło|X509|Komunikat|  
|MutualCertificate|X509|X509|Komunikat|  
|MutualCertificateDuplex|X509|X509|Komunikat|  
|IssuedTokenForCertificate|Federacyjna|X509|Komunikat|  
|Kerberos|Windows|Windows|Komunikat|  
|IssuedToken|Federacyjna|Federacyjna|Komunikat|  
|SspiNegotiated|Wynegocjowane interfejsu Sspi systemu Windows|Wynegocjowane interfejsu Sspi systemu Windows|Komunikat|  
|AnonymousForSslNegotiated|Brak|X509, TLS Nego|Komunikat|  
|UserNameForSslNegotiated|Nazwa użytkownika/hasło|X509, TLS Nego|Komunikat|  
|MutualSslNegotiated|X509|X509, TLS Nego|Komunikat|  
|IssuedTokenForSslNegotiated|Federacyjna|X509, TLS Nego|Komunikat|  
  
 Punktów końcowych przy użyciu tych trybach uwierzytelniania można wyrazić ich wymagania dotyczące zabezpieczeń przy użyciu usługi WS-SecurityPolicy (WS-SP). Ten dokument zawiera opis struktury nagłówka zabezpieczeń i infrastruktury komunikaty dla każdego trybu uwierzytelniania oraz przykłady zasad i komunikatów.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wykorzystuje WS-SecureConversation, aby zapewnić obsługę bezpiecznej sesji do ochrony wymiany wielu komunikatów między aplikacjami.  Aby uzyskać szczegóły implementacji, zobacz "Secure sesji" poniżej.  
  
 Oprócz tryby uwierzytelniania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera ustawienia, aby kontrolować typowych mechanizmów ochrony, które są stosowane do większości tryby uwierzytelniania zabezpieczeń wiadomości, na przykład: kolejność podpisywania lub szyfrowania, mechanizmy algorytmu wyprowadzania klucza, a potwierdzenia podpisu.  
  
 Następujące prefiksy i przestrzenie nazw są używane w tym dokumencie.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|s|http://www.w3.org/2003/05/SOAP-Envelope|  
|SP|http://schemas.xmlsoap.org/ws/2005/07/SECURITYPOLICY|  
|A|http://www.w3.org/2005/08/Addressing|  
|wsse|DO USTALENIA — IDENTYFIKATOR URI PROGRAMU WSS 1.0 JĘZYKA OASIS|  
|wsse11|DO USTALENIA — IDENTYFIKATOR URI PROGRAMU WSS 1.1 JĘZYKA OASIS|  
|wsu|Do ustalenia — narzędzie identyfikatora URI OASIS WSS 1.0|  
|ds|Do ustalenia — identyfikator URI XMLDSig W3C|  
|Wst|Do ustalenia — identyfikator URI protokołu WS-Trust 2005/02|  
|wssc|Do ustalenia — WS-SecureConversation 2005/02 identyfikatora URI|  
|wsaw|Do ustalenia - WS-Addressing przestrzeni nazw zasad|  
|WSP|http://schemas.xmlsoap.org/ws/2004/09/Policy|  
|Mssp|http://schemas.microsoft.com/ws/2005/07/SECURITYPOLICY|  
  
## <a name="1-token-profiles"></a>1. Profile tokenu  
 Specyfikacje zabezpieczenia usług sieci Web reprezentować poświadczeń tokenów zabezpieczających. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje następujące typy tokenów:  
  
### <a name="11-usernametoken"></a>1.1 UsernameToken  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]następujące profile UsernameToken10 i UsernameToken11 z następującymi ograniczeniami:  
  
 Atrybut R1101 PasswordType w elemencie UsernameToken\Password albo pominięcia ani mieć wartości #PasswordText (ustawienie domyślne).  
  
 Co można zaimplementować #PasswordDigest przy użyciu rozszerzeń. Zaobserwowano, że #PasswordDigest został często pomylone jako mechanizm ochrony dostatecznie bezpieczne hasło. Ale #PasswordDigest nie może służyć jako zamiennik szyfrowania UsernameToken. Podstawowym celem #PasswordDigest jest ochrona przed atakami powtarzania. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tryby uwierzytelniania, zagrożenia atakiem polegającym na odtwarzaniu, zostały skorygowane przy użyciu sygnatury komunikatów.  
  
 B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nigdy nie emituje identyfikator jednorazowy i utworzono elementy podrzędne UsernameToken.  
  
 Te elementy podrzędne mają na celu pomoc wykrywania powtarzania. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]użyje sygnatury komunikatów.  
  
 OASIS WSS SOAP komunikatów zabezpieczeń UsernameToken Profile 1.1 (UsernameToken11) wprowadzono wyprowadzania klucza z hasła funkcji.  
  
 Hasło B1103 UsernameToken nie mogą być używane dla klucza pochodnego i w związku z tym dla operacji kryptograficznych.  
  
 Uzasadnienie: hasła są zazwyczaj uznane za zbyt słabe do użycia dla operacji kryptograficznych.  
  
### <a name="12-x509-token"></a>1.2 x 509 tokenu  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje certyfikaty X509v3 jako typ poświadczeń i X509TokenProfile1.0 i X509TokenProfile1.1 jest zgodny z następującymi ograniczeniami:  
  
 Atrybut R1201 ValueType w elemencie BinarySecurityToken musi mieć wartość #X509v3, gdy zawiera certyfikat X509v3.  
  
 WSS X509 Token profilu 1.0 i 1.1 zdefiniuj również #X509PKIPathv1 oraz PKCS&#7; jako typów wartości. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nie obsługuje tego typu.  
  
 R1202 czy rozszerzenia SubjectKeyIdentifier (SKI) znajduje się w X509 certyfikat, wsse:KeyIdentifier powinien być używany dla zewnętrznych odwołań do tokenu, z Właściwość ValueType atrybutu jako #X509SubjectKeyIdentifier i jego zawartości wartość algorytmem Base64 rozszerzenie SKI certyfikatu.  
  
 Odwołania SKI powszechnie implementowanych i sprawdzone na typ wysokiej interoperacyjne odwołania zewnętrznego.  
  
 R1203 Odwołanie zewnętrzne do X509 zabezpieczeń tokenu nie powinien używać ds:X509IssuerSerial.  
  
 R1204 X509TokenProfile1.1 Jeśli jest używany, odwołanie zewnętrzne do X509 zabezpieczeń tokenów należy używać odcisk palca wprowadzone przez 1.1 WS-Security.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje X509IssuerSerial. Istnieją jednak współdziałanie z X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa ciągu do porównywania dwóch wartości X509IssuerSerial. W związku z tym jeśli jedna zmienia kolejność składników nazwa podmiotu i wysyła do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi odwołanie do certyfikatu, nie można odnaleźć.  
  
### <a name="13-kerberos-token"></a>1.3 Token protokołu Kerberos  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje KerberosTokenProfile1.1 na potrzeby uwierzytelniania systemu Windows z następującymi ograniczeniami:  
  
 R1301 A Kerberos tokenu musi zawierać wartość GSS opakowana AP_REQ v4 protokołu Kerberos, zgodnie z definicją w GSS_API i specyfikacja protokołu Kerberos, a musi mieć atrybut ValueType o wartości GSS_Kerberosv5_AP_REQ #.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa GSS opakowana Kerberos uwierzytelniania Kerberos, nie systemu od zera region-REQ. Jest to najlepsze rozwiązanie bezpieczeństwa.  
  
### <a name="14-saml-v11-token"></a>1.4 SAML Token w wersji 1.1  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje profile tokenu SAML programu WSS 1.0 i 1.1 tokeny SAML w wersji 1.1. Istnieje możliwość wykonania innych wersji formatów tokenu SAML.  
  
### <a name="15-security-context-token"></a>W wersji 1.5 Token kontekstu zabezpieczeń  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje zabezpieczenia kontekstu tokenu (SCT) wprowadzone w WS SecureCoversation. SCT jest używana do reprezentowania w kontekście zabezpieczeń określonych w SecureConversation również jako negocjacji binarnej protokoły TLS i SSPI, opisane poniżej.  
  
## <a name="2-common-message-security-parameters"></a>2. Wspólne parametry zabezpieczeń komunikatów  
  
### <a name="21-timestamp"></a>2.1 Sygnatura czasowa  
 Obecności znacznika czasu jest kontrolowany przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zawsze serializuje wsse:TimeStamp z wsse: utworzyć i wsse: wygasa pól. Wsse:TimeStamp są zawsze podpisane podczas podpisywania jest używany.  
  
### <a name="22-protection-order"></a>2.2 kolejność ochrony  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje porządku ochrony wiadomości "Znak przed szyfrowania" i "Szyfrowania przed znak" (1.1 zasad zabezpieczeń). "Zaloguj się przed Szyfruj" zaleca się powodów takich jak: komunikaty chronione przy użyciu szyfrowania przed logowania są otwarte na ataki podstawienia podpisu, chyba że jest używany mechanizm WS-Security 1.1 SignatureConfirmation i sprawia, że podpis za pośrednictwem zaszyfrowaną zawartość Inspekcja trudniej.  
  
### <a name="23-signature-protection"></a>2.3 Podpis ochrony  
 Podczas szyfrowania przed znak jest używany, zalecane jest ochrona podpisu przed atakami ukierunkowany na odgadnięcie zaszyfrowaną zawartość lub klucza podpisywania (szczególnie, gdy token niestandardowy jest używany z słabe materiału klucza).  
  
### <a name="24-algorithm-suite"></a>2.4 pakiet algorytmów  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje wszystkie pakiety algorytm 1.1 zasad zabezpieczeń na liście.  
  
### <a name="25-key-derivation"></a>2.5 klucza pochodnego  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa "Klucza pochodnego dla kluczy symetrycznych", zgodnie z opisem w WS-SecureConversation.  
  
### <a name="26-signature-confirmation"></a>2.6 potwierdzenie podpisu  
 Potwierdzenie podpisu może być jako ochronę przed atakami środkowej man chronić zbiór podpisów.  
  
### <a name="27-security-header-layout"></a>2.7 układ nagłówka zabezpieczeń  
 Każdy tryb uwierzytelniania opisano niektóre układ nagłówka zabezpieczeń. Elementy w nagłówku zabezpieczeń są uporządkowane częściowo. Aby zdefiniować kolejność elementów podrzędnych nagłówka zabezpieczeń, polityki WS-Security definiuje następujące tryby układ nagłówka zabezpieczeń:  
  
|||  
|-|-|  
|Ograniczeniami|Elementy są dodawane do następującego nagłówka zabezpieczeń się, że reguły numerowane układu opisanego w zasady zabezpieczeń sekcji 7.7.1 zgodnie z ogólną zasadą "deklaruje przed użyciem".|  
|Swobodny|Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, która odpowiada programu WSS: zabezpieczenia wiadomości protokołu SOAP.|  
|LaxTimestampFirst|Tym samym Lax z tą różnicą, że pierwszy element w nagłówku zabezpieczeń muszą być wsse:Timestamp|  
|LaxTimestampLast|Identyczny swobodny z tą różnicą, że ostatni element w nagłówku zabezpieczeń muszą być wsse:Timestamp|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje wszystkie cztery tryby układzie nagłówka zabezpieczeń. Zabezpieczenia nagłówka struktury i komunikat dla tryby uwierzytelniania poniżej przykładów trybu "Strict".  
  
## <a name="2-common-message-security-parameters"></a>2. Wspólne parametry zabezpieczeń komunikatów  
 Ta sekcja zawiera przykładowe zasady dla każdego trybu uwierzytelniania wraz z przykładami przedstawiający Struktura nagłówka zabezpieczeń w wiadomości wymieniane przez klienta i usługi.  
  
### <a name="61-transport-protection"></a>6.1 ochrony transportu  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zawiera pięć tryby uwierzytelniania, korzystających z bezpiecznego transportu do ochrony wiadomości. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport i SspiNegotiatedOverTransport.  
  
 Te tryby uwierzytelniania są konstruowane przy użyciu opisanego w SecurityPolicy powiązania transportu. W przypadku UserNameOverTransport tryb uwierzytelniania UsernameToken jest podpisany token pomocniczy. W trybach uwierzytelniania tokenu jest wyświetlany jako podpisany token zatwierdzania. Dodatek C.1.2 i C.1.3 SecurityPolicy opisują szczegółowo układ nagłówka zabezpieczeń. Następujące nagłówki zabezpieczeń przykład Pokaż Strict układu dla trybu danego uwierzytelniania.  
  
 Wartość właściwości "Kluczy pochodnych" tokenów we wszystkich przypadkach jest "false".  
  
 Wartości różnych właściwości powiązania transportu są następujące:  
  
 Sygnatura czasowa: true  
  
 Układ nagłówka zabezpieczeń: Strict  
  
 Pakiet algorytmów: Basic256  
  
#### <a name="611-usernameovertransport"></a>6.1.1 UsernameOverTransport  
 Z tego trybu uwierzytelniania klienta jest uwierzytelniany w usłudze Token nazwy użytkownika, który znajduje się na warstwie SOAP jako podpisanego tokenu pomocniczego zawsze wysyłany z inicjatora do adresata. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Wiązanie używane jest powiązania transportu.  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Układ nagłówka zabezpieczeń  
  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a>6.1.2 CertificateOverTransport  
 Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Wiązanie używane jest powiązania transportu.  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Układ nagłówka zabezpieczeń  
  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a>6.1.3 IssuedTokenOverTransport  
 W ten tryb uwierzytelniania klienta nie uwierzytelniania w usłudze, w związku, ale raczej wyświetlany token wystawiony przez zabezpieczenia tokenu usługi (STS) oraz okaże się wiedzę na temat klucza wspólnego. Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Powiązanie jest powiązania transportu.  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Układ nagłówka zabezpieczeń  
  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a>6.1.4 KerberosOverTransport  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos. Token protokołu Kerberos jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Powiązanie jest powiązania transportu.  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Układ nagłówka zabezpieczeń  
  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a>6.1.5 SspiNegotiatedOverTransport  
 W tym trybie protokół negocjacji służy do uwierzytelniania klienta i serwera. Protokół Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM. Wynikowa SCT pojawia się w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata. Usługa Ponadto jest uwierzytelniany w przypadku warstwy transportu za pomocą certyfikatu X.509. Wiązanie używane jest powiązania transportu. W tym artykule opisano "SPNEGO" (negocjacji) jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wykorzystuje protokół negocjacji binarnej SSPI z protokołu WS-Trust. Przykłady nagłówka zabezpieczeń w tej sekcji są po nawiązaniu SCT za pośrednictwem uzgadnianie SPNEGO.  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a>Przykłady nagłówka zabezpieczeń  
 Po Token kontekstu zabezpieczeń za pomocą uzgadniania SPNEGO przy użyciu protokołu WS-Trust negocjacji binarnej komunikatów aplikacji ma nagłówki zabezpieczeń o następującej strukturze.  
  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a>6.2 za pomocą certyfikatów X.509 do usługi uwierzytelniania  
 W tej sekcji opisano następujące tryby uwierzytelniania: MutualCertificate WSS1.0, wzajemne CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate i IssuedTokenForCertificate.  
  
#### <a name="621-mutualcertificate-wss10"></a>6.2.1 MutualCertificate WSS1.0  
 Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako token inicjatora. Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.  
  
 Wiązanie używane jest powiązanie asymetrycznego z następujących wartości właściwości:  
  
 Token inicjatora: certyfikat X.509 klienta, z ustawioną .../IncludeToken/AlwaysToRecipient tryb dołączania  
  
 Odbiorcy tokenu: Serwer do certyfikatu X.509, włączenia trybu ustawiono .../IncludeToken/Never  
  
 Token ochrony: False  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność Protection: SignBeforeEncrypt  
  
 Szyfrowanie podpisów: True  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a>6.2.2 MutualCertificateDuplex  
 Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako token inicjatora. Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.  
  
 Wiązanie używane jest powiązanie asymetrycznego z następujących wartości właściwości:  
  
 Token inicjatora: X509 klienta certyfikatu, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient  
  
 Odbiorcy tokenu: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToInitiator  
  
 Token ochrony: False  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność Protection: SignBeforeEncrypt  
  
 Szyfrowanie podpisów: True  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie i odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie i odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a>6.2.3 przy użyciu SymmetricBinding X.509 usługi uwierzytelniania  
 "WSS10" przewidzianych ograniczoną obsługę scenariuszy z X509 tokenów. Na przykład nie było możliwości wykonania w celu zapewnienia ochrony podpis i szyfrowanie wiadomości za pomocą tylko usługi X509 tokenu. "WSS11" wprowadzono użycie EncryptedKey jako tokenu symetrycznego. Teraz tymczasowego klucza zaszyfrowanego dla certyfikatu X.509 usługi można użyć do ochrony wiadomości zarówno żądań i odpowiedzi. Tryby uwierzytelniania opisanego w sekcji 6.4 poniżej użycia tego wzorca.  
  
 WS-SecurityPolicy opisuje tego wzorca z usługą za pomocą SymmetricBinding X509 token jako token ochrony.  
  
 Tryby uwierzytelniania AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 i IssuedTokenForCertificate wszystkich za pomocą podobnego wystąpienia sp:SymmetricBinding wartości następujących właściwości:  
  
 Token ochrony: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/Never  
Token ochrony: False  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność Protection: SignBeforeEncrypt  
  
 Szyfrowanie podpisów: True  
  
 Powyżej tryby uwierzytelniania różnią się tylko przez pomocnicze tokeny, których używają. AnonymousForCertificate nie ma żadnych tokenów pomocniczych, MutualCertificate WSS 1.1 ma klienta X509 certyfikatów jako wprowadzająca tokenami pomocniczymi, UserNameForCertificate ma Token nazwy użytkownika jako podpisanego tokenu pomocniczego i IssuedTokenForCertificate został wystawiony token jako tokenu pomocniczego.  
  
 Zasady  
  
 Powiązanie symetryczne  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a>6.2.4 AnonymousForCertificate  
 Z tego trybu uwierzytelniania anonimowego jest klient i Usługa uwierzytelniania za pomocą certyfikatu X.509. Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w 6.4.2.  
  
 Zasady  
  
 Zobacz "Policy" w 6.2.3 powyżej dla powiązania szczegóły  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a>6.2.5 UserNameForCertificate  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego. Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509. Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.  
  
 Zasady  
  
 Zobacz "Policy" w 6.2.3 powyżej dla powiązania szczegóły  
  
 Podpisany Token pomocniczy  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a>6.2.6 MutualCertificate (WSS 1.1)  
 Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako tokenu pomocniczego. Usługa jest również uwierzytelniony za pomocą certyfikatu X.509. Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.  
  
 Zasady  
  
 Zobacz zasady w 6.2.3 dla powiązania szczegóły  
  
 Wprowadzająca Obsługa tokenu  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a>6.2.7 IssuedTokenForCertificate  
 To uwierzytelnianie trybu tak, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i okaże się wiedzę na temat klucza wspólnego. Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego. Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509. Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.  
  
 Zasady  
  
 Zobacz zasady w 6.2.3 powyżej szczegółowe powiązania  
  
 Wprowadzająca Obsługa tokenu  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a>6.3 protokołu Kerberos  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos. Korzystając z tego samego biletu także uwierzytelniania serwera. Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;  
  
 Token ochrony: Biletu Kerberos, tryb dołączania ustawiono .../IncludeToken/Once  
Token ochrony: False  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność Protection: SignBeforeEncrypt  
  
 Szyfrowanie podpisów: True  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a>6.4 IssuedToken  
 W ten tryb uwierzytelniania, które klient nie uwierzytelniania w usłudze, zamiast klienta wyświetlany token wystawiony przez usługę STS oraz okaże się wiedzę na temat klucza wspólnego. Usługa nie jest uwierzytelniony do klienta tak, zamiast niego usługi STS szyfruje klucz udostępniony jako część wystawionego tokenu tak, aby tylko usługa może odszyfrować klucza. Wiązanie używane jest jako symetrycznego powiązania z następującymi właściwościami;  
  
 Token ochrony: Wystawiony Token, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient  
Token ochrony: False  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność Protection: SignBeforeEncrypt  
  
 Szyfrowanie podpisów: True  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a>6.5 przy użyciu SslNegotiated dla usługi uwierzytelniania  
 W tej sekcji opisano grupę tryby uwierzytelniania, które symetrycznego powiązania za pomocą tokenu ochrony jest kontekst tokenu zabezpieczeń na WS-SecureConversation (WS-SC), wykonując protokół TLS za pośrednictwem protokołu WS-Trust (WS-T) RST negocjowane jest którego wartość klucza / Odpowiedź RSTR wiadomości. Szczegóły implementacji uzgadniania TLS za pomocą protokołu WS-Trust są opisane w TLSNEGO. W tym miejscu w przykładach komunikat możemy przyjmie założenie, że SCT z kontekstem zabezpieczeń skojarzony jest już ustalone przez uzgadniania.  
  
 Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;  
  
 Token ochrony: SslContextToken, tryb dołączania ustawiono .../IncludeToken/Never  
Token ochrony: False  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność Protection: SignBeforeEncrypt  
  
 Szyfrowanie podpisów: True  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a>6.5.1 zasady SslNegotiated usługi uwierzytelniania  
 Zasady dla wszystkich metod uwierzytelniania w tej sekcji są podobne i różnią się tylko przez określonych podpisanych obsługi lub potwierdzania tokenów używanych.  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a>6.5.2 AnonymousForSslNegotiated  
 Z tego trybu uwierzytelniania anonimowego jest klient i Usługa uwierzytelniania za pomocą certyfikatu X.509. Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.  
  
 Zasady  
  
 Zobacz zasady w 6.5.1 powyżej szczegółowe powiązania.  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a>6.5.3 UserNameForSslNegotiated  
 Z tego uwierzytelnienia jest tryb, który klient jest uwierzytelniany przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509. Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w 6.5.1.  
  
 Zasady  
  
 W sekcji 6.5.1 powyżej powiązanie szczegóły  
  
 Podpisany Token pomocniczy  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a>6.5.4 IssuedTokenForSslNegotiated  
 To uwierzytelnianie trybu tak, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i okaże się wiedzę na temat klucza wspólnego. Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509. Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.  
  
 Zasady  
  
 W sekcji 6.5.1 powyżej powiązanie szczegóły  
  
 Wprowadzająca Obsługa tokenu  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a>6.5.5 MutualSslNegotiated  
 Z tego trybu uwierzytelniania klient i Usługa uwierzytelniania za pomocą certyfikatów X.509. Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.  
  
 Zasady  
  
 W sekcji 6.5.1 powyżej powiązanie szczegóły  
  
 Wprowadzająca Obsługa tokenu  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a>6.6 SspiNegotiated  
 Z tego trybu uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera. Protokół Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM. Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;  
  
 Token ochrony: SpnegoContextToken, tryb dołączania ustawiono .../IncludeToken/AlwaysToRecipient  
Token ochrony: False  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność Protection: SignBeforeEncrypt  
  
 Szyfrowanie podpisów: True  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a>6.7 SecureConversation  
 Wiązanie używane jest symetrycznego powiązania z tokenem ochrony trwa SCT na WS-SecureConversation (WS-SC). SCT negocjowane jest za pomocą protokołu WS-Trust (WS-Trust) lub protokołu WS-SecureConversation (WS-SC) zgodnie z zagnieżdżonych powiązania, który sam jest powiązanie symetrycznego, które wykorzystuje protokół negocjacji. Protokół negocjacji będzie korzystać z protokołu Kerberos do uwierzytelniania klienta i serwera, jeśli to możliwe. Jeśli nie można użyć protokołu Kerberos, jego powróci do uwierzytelniania NTLM.  
  
 Zasady  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature  
 Żądanie  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Przykłady nagłówka zabezpieczeń: EncryptBeforeSign  
 Żądanie  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Odpowiedź  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
