---
title: Protokoły zabezpieczeń wersja 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 2014e1f6f8fefa89ed44bd820c3712617ff51470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184524"
---
# <a name="security-protocols-version-10"></a>Protokoły zabezpieczeń wersja 1.0
Protokoły zabezpieczeń usług sieci Web zapewniają mechanizmy zabezpieczeń usług sieci Web, które obejmują wszystkie istniejące wymagania dotyczące zabezpieczeń obsługi wiadomości w przedsiębiorstwie. W tej sekcji opisano szczegóły programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Channels.SecurityBindingElement>w wersji 1.0 (zaimplementowane w ) dla następujących protokołów zabezpieczeń usług sieci Web.  
  
|Specyfikacja/dokument|Link|  
|-|-|  
|WSS: Zabezpieczenia wiadomości SOAP 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|WSS: Profil tokenu użytkownika 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: Profil tokenu X509 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|WSS: SAML 1.1 Profil tokenu 1.0|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|WSS: Zabezpieczenia wiadomości SOAP 1.1|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|Profil tokenu nazwy użytkownika WSS 1.1|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: Profil tokenu X.509 1.1|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|WSS: Profil tokenu Protokołu Kerberos 1.1|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|WSS: SAML 1.1 Profil tokenu 1.1|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|Rozmowa w zabezpieczeniu WS|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|WS-Trust|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|Uwaga aplikacji:<br /><br /> Korzystanie z funkcji zaufania WS dla uzgadniania TLS|Do opublikowania|  
|Uwaga aplikacji:<br /><br /> Korzystanie z funkcji WS-Trust dla usługi SPNEGO|Do opublikowania|  
|Uwaga aplikacji:<br /><br /> Usługi sieci Web adresujące odwołania do punktów końcowych i tożsamość|Do opublikowania|  
|WS-SecurityPolicy 1.1<br /><br /> (2005/07)|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> zmieniona [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) przedłożona Komitetowi Techniczneemu OASIS WS-SX |  
  
 WCF, wersja 1, zawiera 17 trybów uwierzytelniania, które mogą być używane jako podstawa konfiguracji zabezpieczeń usług sieci Web. Każdy tryb jest zoptymalizowany pod kątem wspólnego zestawu wymagań dotyczących wdrażania, takich jak:  
  
- Poświadczenia używane do uwierzytelniania klienta i usługi.  
  
- Mechanizmy ochrony bezpieczeństwa wiadomości lub transportu.  
  
- Wzorce wymiany wiadomości.  
  
|Tryb uwierzytelniania|Uwierzytelnianie klienta|Uwierzytelnianie serwera|Tryb|  
|-------------------------|---------------------------|---------------------------|----------|  
|Nazwa użytkownikaTransportuTransport|Nazwa użytkownika/hasło|X509|Transport|  
|CertificateOverTransport|X509|X509|Transport|  
|Protokół KerberosOverTransport|Windows|X509|Transport|  
|IssuedTokenOverTransport|Federacyjni|X509|Transport|  
|SspiNegotiatedOverTransport|Wynegocjowane SSPI systemu Windows|Wynegocjowane SSPI systemu Windows|Transport|  
|AnonymousForCertificate|Brak|X509|Komunikat|  
|Certyfikat UserNameForCertificate|Nazwa użytkownika/hasło|X509|Komunikat|  
|Certyfikat MutualCertificate|X509|X509|Komunikat|  
|Wzajemne CertyfikatyOdlot|X509|X509|Komunikat|  
|Certyfikat IssuedTokenForCertificate|Federacyjni|X509|Komunikat|  
|Kerberos|Windows|Windows|Komunikat|  
|Issuedtoken|Federacyjni|Federacyjni|Komunikat|  
|SspiNegotiated|Wynegocjowane SSPI systemu Windows|Wynegocjowane SSPI systemu Windows|Komunikat|  
|AnonymousForSslNegotiated|Brak|X509, TLS-Nego|Komunikat|  
|Nazwa użytkownikaForSslNegotiated|Nazwa użytkownika/hasło|X509, TLS-Nego|Komunikat|  
|MutualSslNegotowany|X509|X509, TLS-Nego|Komunikat|  
|WydanaTokenForSslNegotiated|Federacyjni|X509, TLS-Nego|Komunikat|  
  
 Punkty końcowe przy użyciu takich trybów uwierzytelniania można wyrazić swoje wymagania dotyczące zabezpieczeń przy użyciu WS-SecurityPolicy (WS-SP). W tym dokumencie opisano strukturę nagłówka zabezpieczeń i komunikatów infrastruktury dla każdego trybu uwierzytelniania i przedstawiono przykłady zasad i komunikatów.  
  
 WCF wykorzystuje WS-SecureConversation do zapewnienia bezpiecznej obsługi sesji w celu ochrony wymiany wielu komunikatów między aplikacjami.  Zobacz "Bezpieczne sesje" poniżej, aby uzyskać szczegółowe informacje na temat implementacji.  
  
 Oprócz trybów uwierzytelniania WCF udostępnia ustawienia do kontrolowania typowych mechanizmów ochrony, które mają zastosowanie do większości trybów uwierzytelniania opartych na zabezpieczeniach wiadomości, na przykład: kolejność podpisu i operacje szyfrowania, zestawy algorytmów, wyprowadzanie kluczy i potwierdzenie podpisu.  
  
 W tym dokumencie są używane następujące prefiksy i przestrzenie nazw.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|s|<http://www.w3.org/2003/05/soap-envelope/>|
|sp|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|a|<http://www.w3.org/2005/08/addressing>|  
|wsse|TBD – OASIS WSS 1.0 URI|  
|wsse11|TBD – OASIS WSS 1.1 URI|  
|wsu|TBD – OASIS WSS 1.0 Narzędzie URI|  
|ds|TBD – W3C XMLDSig URI|  
|Wst|TBD – WS-Trust 2005/02 URI|  
|wssc|TBD – WS-SecureConversation 2005/02 URI|  
|wsaw|TBD — obszar nazw zasad adresowania WS|  
|wsp.|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|mssp|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a>1. Profile tokenów  
 Specyfikacje zabezpieczeń usług sieci Web reprezentują poświadczenia jako tokeny zabezpieczające. WCF obsługuje następujące typy tokenów:  
  
### <a name="11-usernametoken"></a>1.1 Nazwa użytkownikaDoken  
 WCF następuje UsernameToken10 i UsernameToken11 profile z następujących ograniczeń:  
  
 Atrybut PasswordType R1101 w elemencie UsernameToken\Password MUSI zostać pominięty lub mieć wartość #PasswordText (domyślnie).  
  
 Można zaimplementować #PasswordDigest przy użyciu rozszerzalności. Zaobserwowano, że #PasswordDigest często mylił się jako wystarczająco bezpieczny mechanizm ochrony hasłem. Ale #PasswordDigest nie może służyć jako substytut szyfrowania UsernameToken. Głównym celem #PasswordDigest jest ochrona przed atakami powtarzania. W trybach uwierzytelniania WCF zagrożenia ataku powtarzania są ograniczane przy użyciu podpisów wiadomości.  
  
 B1102 WCF nigdy nie emituje Nonce i utworzone podelementów UsernameToken.  
  
 Te podkawiany mają na celu ułatwienie wykrywania powtarzania. WCF zamiast tego używa podpisów wiadomości.  
  
 Oasis WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) wprowadzono klucz pochodny z funkcji hasła.  
  
 B1103 Nazwa użytkownikaNaken hasło nie może być używany do wyprowadzania klucza, a zatem do operacji kryptograficznych.  
  
 Uzasadnienie: hasła są zazwyczaj uważane za zbyt słabe, aby można je było używać do operacji kryptograficznych.  
  
### <a name="12-x509-token"></a>1.2 Token X509  
 WCF obsługuje certyfikaty X509v3 jako typ poświadczeń i następuje X509TokenProfile1.0 i X509TokenProfile1.1 z następującymi ograniczeniami:  
  
 R1201 Atrybut ValueType w elemencie BinarySecurityToken musi mieć wartość #X509v3, gdy zawiera certyfikat X509v3.  
  
 WSS X509 Token Profile 1.0 i 1.1 definiują również #X509PKIPathv1 i #PKCS7 jako typy wartości. WCF nie obsługuje tych typów.  
  
 R1202 Jeśli rozszerzenie SubjectKeyIdentifier (SKI) jest obecne w certyfikacie X509, wsse:KeyIdentifier powinien być używany do zewnętrznych odwołań do tokenu, z atrybutem ValueType jako #X509SubjectKeyIdentifier i jego zawartości wartości zakodowanej base64 rozszerzenia SKI certyfikatu.  
  
 Referencje SKI są szeroko stosowane i udowodnione jako wysoce interoperacyjny zewnętrzny typ odniesienia.  
  
 R1203 Zewnętrzne odwołanie do tokenu zabezpieczającego X509 NIE POWINNO używać ds:X509IssuerSerial.  
  
 R1204 Jeśli X509TokenProfile1.1 jest w użyciu, zewnętrzne odwołanie do tokenu zabezpieczającego X509 należy użyć odcisk palca wprowadzony przez WS-Security 1.1.  
  
 WCF obsługuje X509IssuerSerial. Istnieją jednak problemy ze współdziałaniem z X509IssuerSerial: WCF używa ciągu do porównania dwóch wartości X509IssuerSerial. W związku z tym jeśli jeden ponownie zamówi składniki nazwy podmiotu i wysyła do usługi WCF odwołanie do certyfikatu, nie może być znaleziony.  
  
### <a name="13-kerberos-token"></a>1.3 Token Protokołu Kerberos  
 WCF obsługuje Protokół KerberosTokenProfile1.1 do celów uwierzytelniania systemu Windows z następującymi ograniczeniami:  
  
 R1301 Token Protokołu Kerberos musi zawierać wartość Opakowanego protokołu Kerberos v4 AP_REQ, zgodnie z definicją w GSS_API i specyfikacji Protokołu Kerberos, oraz musi mieć atrybut ValueType z wartością #GSS_Kerberosv5_AP_REQ.  
  
 WCF używa GSS opakowane Kerberos AP-REQ, a nie nagie AP-REQ. Jest to najlepsze rozwiązanie w zakresie zabezpieczeń.  
  
### <a name="14-saml-v11-token"></a>1.4 SamL v1.1 Token  
 WCF obsługuje WSS SAML Token profile 1.0 i 1.1 dla SAML v1.1 tokenów. Możliwe jest zaimplementowanie innych wersji formatów tokenów SAML.  
  
### <a name="15-security-context-token"></a>1.5 Token kontekstu zabezpieczeń  
 WCF obsługuje token kontekstu zabezpieczeń (SCT) wprowadzony w WS-SecureConversation. SCT jest używany do reprezentowania kontekstu zabezpieczeń ustanowionego w SecureConversation, a także binarnych protokołów negocjacji TLS i SSPI, opisanych poniżej.  
  
## <a name="2-common-message-security-parameters"></a>2. Typowe parametry zabezpieczeń wiadomości  
  
### <a name="21-timestamp"></a>2.1 Sygnatura czasowa  
 Obecność sygnatury <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> czasowej <xref:System.ServiceModel.Channels.SecurityBindingElement> jest kontrolowana przy użyciu właściwości klasy. WCF zawsze serializuje wsse:TimeStamp z wsse:Created i wsse:Expires fields. Sygnatura czasowa wsse:Timestamp jest zawsze podpisywane podczas podpisywania jest używany.  
  
### <a name="22-protection-order"></a>2.2 Nakaz ochrony  
 WCF obsługuje kolejność ochrony wiadomości "Sign Before Encrypt" i "Encrypt Before Sign" (Zasady zabezpieczeń 1.1). "Sign Before Encrypt" jest zalecane z powodów takich jak: wiadomości chronione szyfruj przed podpisaniem są otwarte dla ataków substytucyjnych podpisu, chyba że używany jest mechanizm SignatureConfirmation w ramach WS-Security 1.1, a podpis za pomocą zaszyfrowanej zawartości tworzy audytu.  
  
### <a name="23-signature-protection"></a>2.3 Ochrona podpisu  
 Gdy encrypt before sign jest używany, zaleca się, aby chronić podpis, aby zapobiec atakom siłowych w celu odgadnięcia zaszyfrowanej zawartości lub klucza podpisywania (zwłaszcza gdy niestandardowy token jest używany ze słabym materiałem klucza).  
  
### <a name="24-algorithm-suite"></a>2.4 Pakiet algorytmów  
 WCF obsługuje wszystkie zestawy algorytmów wymienione w zasadach zabezpieczeń 1.1.  
  
### <a name="25-key-derivation"></a>2.5 Wyprowadzanie kluczy  
 WCF używa "Wyprowadzanie kluczy symetrycznych" zgodnie z opisem w WS-SecureConversation.  
  
### <a name="26-signature-confirmation"></a>2.6 Potwierdzenie podpisu  
 Potwierdzenie podpisu może być jako ochrona przed atakami pośrednika, aby chronić zestaw podpisów.  
  
### <a name="27-security-header-layout"></a>2.7 Układ nagłówka zabezpieczeń  
 Każdy tryb uwierzytelniania opisuje określony układ nagłówka zabezpieczeń. Elementy w nagłówku zabezpieczeń są częściowo uporządkowane. Aby zdefiniować kolejność elementów podrzędnych nagłówka zabezpieczeń, usługa WS-Security Policy definiuje następujące tryby układu nagłówka zabezpieczeń:  
  
|||  
|-|-|  
|Dokładny|Elementy są dodawane do nagłówka zabezpieczeń zgodnie z zasadami układu numerowanymi opisanymi w sekcji Zasady zabezpieczeń 7.7.1 zgodnie z ogólną zasadą "deklarowania przed użyciem".|  
|Lax|Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności zgodnej z zasadami WSS: SOAP Message Security.|  
|LaxTimestampPierwsz|Tak samo jak Lax, z tą różnicą, że pierwszy element w nagłówku zabezpieczeń musi być sygnaturą czasową wsse:Timestamp|  
|LaxTimestampLast|Tak samo jak lax, z tą różnicą, że ostatni element w nagłówku zabezpieczeń musi być wsse:Timestamp|  
  
 WCF obsługuje wszystkie cztery tryby dla układu nagłówka zabezpieczeń. Struktura nagłówka zabezpieczeń i przykłady komunikatów dla trybów uwierzytelniania poniżej są zgodne z trybem "Ścisłe".  
  
## <a name="2-common-message-security-parameters"></a>2. Typowe parametry zabezpieczeń wiadomości  
 W tej sekcji przedstawiono przykładowe zasady dla każdego trybu uwierzytelniania wraz z przykładami przedstawiającymi strukturę nagłówka zabezpieczeń w wiadomościach wymienianych przez klienta i usługę.  
  
### <a name="61-transport-protection"></a>6.1 Ochrona przed transportem  
 WCF zapewnia pięć trybów uwierzytelniania, które używają bezpiecznego transportu do ochrony wiadomości; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport i SspiNegotiatedOverTransport.  
  
 Te tryby uwierzytelniania są konstruowane przy użyciu powiązania transportu opisanego w SecurityPolicy. W trybie uwierzytelniania UserNameOverTransport Nazwa_użytkownika Jest podpisanym tokenem pomocniczym. W przypadku innych trybów uwierzytelniania token jest wyświetlany jako podpisany token zatwierdzający. Załącznik C.1.2 i C.1.3 securityPolicy szczegółowo opisują układ nagłówka zabezpieczeń. Poniższe przykładowe nagłówki zabezpieczeń pokazują ścisły układ dla danego trybu uwierzytelniania.  
  
 Wartość właściwości "Klucze pochodne" dla tokenów we wszystkich przypadkach jest "false".  
  
 Wartości różnych właściwości powiązania transportu są następujące:  
  
 Sygnatura czasowa: true  
  
 Układ nagłówka zabezpieczeń: Ścisły  
  
 Pakiet algorytmów: Basic256  
  
#### <a name="611-usernameovertransport"></a>6.1.1 Nazwa użytkownikaTransporttransport  
 W tym trybie uwierzytelniania klient uwierzytelnia się za pomocą tokenu nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy, który jest zawsze wysyłany z inicjatora do adresata. Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu. Używane powiązanie jest powiązanie transportu.  
  
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
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token pomocniczy, który jest zawsze wysyłany z inicjatora do adresata. Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu. Używane powiązanie jest powiązanie transportu.  
  
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
  
#### <a name="613-issuedtokenovertransport"></a>6.1.3 WydanyTokenTransport  
 W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze jako takiej, ale raczej przedstawia token wystawiony przez usługę tokenu zabezpieczającego (STS) i potwierdza znajomość klucza udostępnionego. Wystawiony token pojawia się w warstwie SOAP jako token pomocniczy, który jest zawsze wysyłany z inicjatora do adresata. Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu. Powiązanie jest powiązanie transportu.  
  
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
  
#### <a name="614-kerberosovertransport"></a>6.1.4 Protokół KerberosOverTransport  
 W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu Kerberos. Token Protokołu Kerberos pojawia się w warstwie SOAP jako token pomocniczy. Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu. Powiązanie jest powiązanie transportu.  
  
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
 W tym trybie protokół negocjacji jest używany do wykonywania uwierzytelniania klienta i serwera. Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM. Wynikowy SCT pojawia się w warstwie SOAP jako token pomocniczy, który jest zawsze wysyłany od inicjatora do adresata. Usługa jest dodatkowo uwierzytelniona w warstwie transportu za pomocą certyfikatu X.509. Używane powiązanie jest powiązanie transportu. "SPNEGO" (negocjacja) opisuje, jak WCF używa protokołu negocjacji binarnych SSPI z WS-Trust. Przykłady nagłówka zabezpieczeń w tej sekcji są po SCT został ustanowiony za pośrednictwem uzgadniania SPNEGO.  
  
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
  
### <a name="security-header-examples"></a>Przykłady nagłówków zabezpieczeń  
 Po ustanowieniu tokenu kontekstu zabezpieczeń za pomocą uzgadniania SPNEGO przy użyciu negocjacji binarnych WS-Trust komunikaty aplikacji mają nagłówki zabezpieczeń o następującej strukturze.  
  
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
  
### <a name="62-using-x509-certificates-for-service-authentication"></a>6.2 Korzystanie z certyfikatów X.509 do uwierzytelniania usługi  
 W tej sekcji opisano następujące tryby uwierzytelniania: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate i IssuedTokenForCertificate.  
  
#### <a name="621-mutualcertificate-wss10"></a>6.2.1 Certyfikat wzajemny WSS1.0  
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token inicjatora. Usługa jest również uwierzytelniona przy użyciu certyfikatu X.509.  
  
 Użyte powiązanie jest powiązaniem asymetrycznym z następującymi wartościami właściwości:  
  
 Token inicjatora: certyfikat X.509 klienta, z trybem dołączania ustawionym na .../IncludeToken/AlwaysToRecipient  
  
 Token odbiorcy: Certyfikat X.509 serwera z trybem włączenia jest ustawiony .../IncludeToken/Never  
  
 Ochrona tokenu: Fałsz  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność ochrony: SignBeforeEncrypt  
  
 Szyfruj podpis: True  
  
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
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token inicjatora. Usługa jest również uwierzytelniona przy użyciu certyfikatu X.509.  
  
 Użyte powiązanie jest powiązaniem asymetrycznym z następującymi wartościami właściwości:  
  
 Token inicjatora: Certyfikat X509 klienta, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient  
  
 Token odbiorcy: Certyfikat X509 serwera, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToInitiator  
  
 Ochrona tokenu: Fałsz  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność ochrony: SignBeforeEncrypt  
  
 Szyfruj podpis: True  
  
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
 Prośba i odpowiedź  
  
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
 Prośba i odpowiedź  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a>6.2.3 Korzystanie z symetrycznego powiązania z uwierzytelnianiem usługi X.509  
 "WSS10" zapewnia ograniczoną obsługę scenariuszy z tokenami X509. Na przykład nie było sposobu zapewnienia ochrony podpisu i szyfrowania dla wiadomości przy użyciu tylko usługi token X509. "WSS11" wprowadzono użycie EncryptedKey jako token symetryczny. Teraz klucz tymczasowy zaszyfrowany dla certyfikatu X.509 usługi może służyć zarówno do ochrony wiadomości żądania i odpowiedzi. Tryby uwierzytelniania opisane w sekcji 6.4 poniżej używają tego wzorca.  
  
 WS-SecurityPolicy opisuje ten wzorzec przy użyciu SymmetricBinding z tokenem Usługi X509 jako token ochrony.  
  
 Tryby uwierzytelniania AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 i IssuedTokenForCertificate używają podobnego wystąpienia sp:SymmetricBinding z następującymi wartościami właściwości:  
  
 Token ochrony: Certyfikat X509 serwera, tryb dołączania jest ustawiony na .../IncludeToken/Never  
Ochrona tokenu: Fałsz  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność ochrony: SignBeforeEncrypt  
  
 Szyfruj podpis: True  
  
 Powyższe tryby uwierzytelniania różnią się tylko tokenami pomocniczymi, których używają. AnonymousForCertificate nie ma żadnych tokenów pomocniczych, MutualCertificate WSS 1.1 ma certyfikat X509 klienta jako tokeny wspierające, UserNameForCertificate ma token UserName jako podpisany token pomocniczy i IssuedTokenForCertificate ma wystawiony token jako token pomocniczy.  
  
 Zasady  
  
 Wiązanie symetryczne  
  
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
  
#### <a name="624-anonymousforcertificate"></a>6.2.4 AnonimowośćDocertytutututu  
 W tym trybie uwierzytelniania klient jest anonimowy, a usługa jest uwierzytelniana przy użyciu certyfikatu X.509. Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.4.2.  
  
 Zasady  
  
 Szczegółowe informacje na temat wiążących informacji znajdują się w informacji dodatkowej do "Polityki" w pkt 6.2.3 powyżej  
  
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
  
#### <a name="625-usernameforcertificate"></a>6.2.5 Nazwa użytkownikaDocertyfikat  
 W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu tokenu nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy. Usługa uwierzytelnia się klientowi przy użyciu certyfikatu X.509. Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest klucz generowany przez klienta, zaszyfrowane za pomocą klucza publicznego usługi.  
  
 Zasady  
  
 Szczegółowe informacje na temat wiążących informacji znajdują się w informacji dodatkowej do "Polityki" w pkt 6.2.3 powyżej  
  
 Podpisany token pomocniczy  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a>6.2.6 Certyfikat wzajemny (WSS 1.1)  
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token pomocniczy. Usługa jest również uwierzytelniona przy użyciu certyfikatu X.509. Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest klucz generowany przez klienta, zaszyfrowane za pomocą klucza publicznego usługi.  
  
 Zasady  
  
 Szczegółowe informacje na temat zasad znajdują się w 6.2.3  
  
 Zatwierdzający token pomocniczy  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a>6.2.7 Certyfikat WydanyTokenForCertificate  
 W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze jako takiej, ale zamiast tego przedstawia token wystawiony przez usługę STS i potwierdza znajomość klucza udostępnionego. Wystawiony token pojawia się w warstwie SOAP jako token pomocniczy. Usługa uwierzytelnia się klientowi przy użyciu certyfikatu X.509. Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest klucz generowany przez klienta, zaszyfrowane za pomocą klucza publicznego usługi.  
  
 Zasady  
  
 Szczegółowe informacje na temat zasad znajdują się w 6.2.3 powyżej  
  
 Zatwierdzający token pomocniczy  
  
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
  
## <a name="63-kerberos"></a>6.3 Protokół Kerberos  
 W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu Kerberos. Ten sam bilet zapewnia również uwierzytelnianie serwera. Użyte powiązanie jest powiązaniem symetrycznym z następującymi właściwościami;  
  
 Token ochrony: Bilet Kerberos, tryb włączenia jest ustawiony na .../IncludeToken/Once  
Ochrona tokenu: Fałsz  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność ochrony: SignBeforeEncrypt  
  
 Szyfruj podpis: True  
  
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
  
#### <a name="64-issuedtoken"></a>6.4 WydanyDokład  
 W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze, jako taki, a klient przedstawia token wystawiony przez usługę STS i potwierdza znajomość klucza udostępnionego. Usługa nie jest uwierzytelniana do klienta, jako takie, zamiast STS szyfruje klucz udostępniony jako część wystawionego tokenu, tak aby tylko usługa może odszyfrować klucz. Używane powiązanie jest jako wiązanie symetryczne z następującymi właściwościami;  
  
 Token ochrony: Wystawiony token, tryb włączenia jest ustawiony na .../IncludeToken/AlwaysToRecipient  
Ochrona tokenu: Fałsz  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność ochrony: SignBeforeEncrypt  
  
 Szyfruj podpis: True  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a>6.5 Korzystanie z usługi SslNegotiated do uwierzytelniania usługi  
 W tej sekcji opisano grupę trybów uwierzytelniania, które używają powiązania symetrycznego z tokenem ochrony jako token kontekstu zabezpieczeń na WS-SecureConversation (WS-SecureConversation (WS-SC), którego wartość klucza jest negocjowana przez wykonanie protokołu TLS za pomocą komunikatów RST/RSTR usługi WS-Trust (WS-T). Szczegóły implementacji uzgadniania TLS przy użyciu programu WS-Trust są opisane w TLSNEGO. W tym miejscu w przykładach wiadomości zakładamy, że SCT z skojarzonym kontekstem zabezpieczeń jest już ustanowiony za pomocą uzgadniania.  
  
 Użyte powiązanie jest powiązaniem symetrycznym z następującymi właściwościami;  
  
 Token ochrony: SslContextToken, tryb włączenia jest ustawiony na .../IncludeToken/Never  
Ochrona tokenu: Fałsz  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność ochrony: SignBeforeEncrypt  
  
 Szyfruj podpis: True  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a>6.5.1 Zasady uwierzytelniania usługi SslNegotiated  
 Zasady dla wszystkich trybów uwierzytelniania w tej sekcji są podobne i różnią się tylko określonymi podpisanymi tokenami pomocniczymi lub aprobującymi używanymi.  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a>6.5.2 AnonimowoDo negocjacji  
 W tym trybie uwierzytelniania klient jest anonimowy, a usługa jest uwierzytelniana przy użyciu certyfikatu X.509. Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1 powyżej.  
  
 Zasady  
  
 Szczegółowe informacje dotyczące powiązania można znaleźć w polityce w 6.5.1 powyżej.  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a>6.5.3 Nazwa użytkownikaDo negocjacji  
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu tokenu nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy. Usługa jest uwierzytelniona przy użyciu certyfikatu X.509. Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1.  
  
 Zasady  
  
 Szczegółowe informacje dotyczące wiązania znajdują się w punkcie 6.5.1 powyżej  
  
 Podpisany token pomocniczy  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a>6.5.4 WydanyTokenForSslNegotiated  
 W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze jako takiej, ale zamiast tego przedstawia token wystawiony przez usługę STS i potwierdza znajomość klucza udostępnionego. Wystawiony token pojawia się w warstwie SOAP jako token pomocniczy. Usługa jest uwierzytelniona przy użyciu certyfikatu X.509. Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1 powyżej.  
  
 Zasady  
  
 Szczegółowe informacje dotyczące wiązania znajdują się w punkcie 6.5.1 powyżej  
  
 Zatwierdzający token pomocniczy  
  
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
  
#### <a name="655-mutualsslnegotiated"></a>6.5.5 Objednanie  
 W tym trybie uwierzytelniania klient i usługa uwierzytelniają się przy użyciu certyfikatów X.509. Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1 powyżej.  
  
 Zasady  
  
 Szczegółowe informacje dotyczące wiązania znajdują się w punkcie 6.5.1 powyżej  
  
 Zatwierdzający token pomocniczy  
  
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
  
### <a name="66-sspinegotiated"></a>6.6 SspiNegotyzowany  
 W tym trybie uwierzytelniania protokół negocjacji jest używany do wykonywania uwierzytelniania klienta i serwera. Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM. Użyte powiązanie jest powiązaniem symetrycznym z następującymi właściwościami;  
  
 Token ochrony: SpnegoContextToken, tryb włączenia jest ustawiony na .../IncludeToken/AlwaysToRecipient  
Ochrona tokenu: Fałsz  
  
 Cały nagłówek i podpisy treści: True  
  
 Kolejność ochrony: SignBeforeEncrypt  
  
 Szyfruj podpis: True  
  
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
  
### <a name="67-secureconversation"></a>6.7 Bezpieczna konwersacja  
 Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest SCT na WS-SecureConversation (WS-SC). SCT jest negocjowany przy użyciu WS-Trust (WS-Trust) lub WS-SecureConversation (WS-SC) zgodnie z zagnieżdżonego powiązania, który sam w sobie jest powiązanie symetryczne, który używa protokołu negocjacji. Protokół negocjacji będzie używany do wykonywania uwierzytelniania klienta i serwera, jeśli to możliwe. Jeśli protokołu Kerberos nie można użyć, powróci do NTLM.  
  
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
