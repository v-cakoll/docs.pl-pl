---
title: '&lt;wsFederation&gt;'
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: de7be463403b675e5f03786e85807e6685348680
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758987"
---
# <a name="ltwsfederationgt"></a>&lt;wsFederation&gt;
Zapewnia konfigurację <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
\<system.identityModel.services >  
\<federationConfiguration >  
\<wsFederation >  
  
## <a name="syntax"></a>Składnia  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Typ authenticationType|Identyfikator URI, który określa typ uwierzytelniania. Ustawia parametr wauth WS-Federation żądania logowania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wauth nie jest uwzględniony w żądaniu.|  
|świeżości|Żądany maksymalny wiek żądania uwierzytelniania w minutach. Ustawia parametr wfresh WS-Federation żądania logowania. Opcjonalna. Wartością domyślną jest zero. Opcjonalna. **Ostrzeżenie:** w kolejnej wersji programu .NET Framework 4.5, `freshness` atrybut będzie typu `xs:string` i jego wartość domyślna będzie `null`.|  
|homeRealm|Obszar macierzysty dostawcy tożsamości (IP) do użycia na potrzeby uwierzytelniania. Ustawia parametr godz. pracy WS-Federation żądania logowania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr godz. pracy nie jest uwzględniony w żądaniu.|  
|issuer|Identyfikator URI zamierzone wystawcy tokenów. Ustawia podstawowy adres URL protokołu WS-Federation logowania żądań i wylogowania żądań wymagane.|  
|persistentCookiesOnPassiveRedirects|Określa, czy trwałe pliki cookie są wydawane w uwierzytelniania. Opcjonalna. Wartość domyślna to "false", pliki cookie nie są wysyłane.|  
|passiveRedirectEnabled|Określa, czy WSFAM jest włączone automatyczne przekierowywanie nieautoryzowanych żądań do usługi tokenu Zabezpieczającego. Opcjonalna. Wartość domyślna to "true", automatycznie są przekierowanie nieautoryzowanych żądań.|  
|Zasady|Adres URL, który określa lokalizację odpowiednich zasad do użycia w odpowiedzi na żądania logowania. Wartość domyślna to ciąg pusty. Ustawia parametr wp WS-Federation żądania logowania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wp nie jest uwzględniony w żądaniu.|  
|obszar|Identyfikator URI żądania obszaru. (Identyfikator URI, który identyfikuje uzależnionej (RP) do usługi tokenu zabezpieczającego (STS).) Ustawia parametr żądania wtrealm logowania WS-Federation żądania. Wymagana.|  
|odpowiedź|Adres URL, który określa adres, w którym chcesz otrzymywać odpowiedzi z zabezpieczeń usługi tokenów (STS) jednostki uzależnionej aplikacji firmy (RP). Ustawia parametr wreply WS-Federation żądania logowania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wreply nie jest uwzględniony w żądaniu.|  
|Żądanie|Żądanie wydawania tokenów. Ustawia parametr wreq WS-Federation żądania logowania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wreq nie jest uwzględniony w żądaniu. Z tym wreq lub parametr wreqptr żądania oznacza, że usługa tokenu Zabezpieczającego wie, jakiego rodzaju token do wystawiania.|  
|requestPtr|Adres URL, który określa lokalizację żądania wystawiania tokenu. Ustawia parametr wreqptr żądania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wreqptr nie jest uwzględniony w żądaniu. Z tym wreq lub parametr wreqptr żądania oznacza, że usługa tokenu Zabezpieczającego wie, jakiego rodzaju token do wystawiania.|  
|requireHttps|Określa, czy komunikację z usługi tokenu zabezpieczającego (STS) musi używać protokołu HTTPS. Opcjonalna. Wartość domyślna to "true", musi być używany protokół HTTPS.|  
|zasób|Identyfikator URI, który identyfikuje zasób, do której uzyskuje dostęp, uzależnionej (RP) do do usługi tokenu zabezpieczającego (STS). Opcjonalna. Ustawia parametr wres WS-Federation żądania logowania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wres nie jest uwzględniony w żądaniu. **Uwaga:** wres jest parametrem starszej wersji. Określ `realm` zamiast tego użyj parametru wtrealm dla atrybutu.|  
|signInQueryString|Udostępnia punkt rozszerzalności do określenia aplikacji zdefiniowane parametry zapytania w adresie URL żądania logowania WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry powinny być uwzględnione w żądaniu. Parametry są określone jako fragment ciągu zapytania przy użyciu następującej postaci: `"param1=value1&param2=value2&param3=value3"` i tak dalej. **Uwaga:** w pliku konfiguracji "&" znak w ciągu zapytania musi być określona za pomocą jego odwołania do jednostki, `&`.|  
|signOutQueryString|Udostępnia punkt rozszerzalności do określenia aplikacji zdefiniowane parametry zapytania w adresie URL żądania logowania WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry powinny być uwzględnione w żądaniu. Parametry są określone jako fragment ciągu zapytania przy użyciu następującej postaci: `"param1=value1&param2=value2&param3=value3"` i tak dalej. **Uwaga:** w pliku konfiguracji "&" znak w ciągu zapytania musi być określona za pomocą jego odwołania do jednostki, `&`.|  
|signOutReply|Określa adres URL, do którego mają być przekierowywane klienta przez usługę tokenu zabezpieczającego (STS) podczas wylogowania za pomocą protokołu WS-Federation pasywne. Ustawia parametr wreply na żądanie usługi WS-Federation wylogowania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry powinny być uwzględnione w żądaniu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `<wsFederation>` element, aby skonfigurować domyślne ustawienia parametru WS-Federation oraz domyślne zachowanie dla WSFAM. Zdefiniowane w obszarze ustawienia parametru WS-Federation `<wsFederation>` element ustawiony równoważne właściwości udostępniane przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy. Te właściwości pozostają takie same dla każdego żądania wydanego przez WSFAM. Parametry WS-Federation można zmienić dynamicznie podczas żądania przetwarzania przez dodanie obsługi zdarzeń dla zdarzenia udostępnianych przez WSFAM; na przykład <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> zdarzeń. Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy.  
  
 `<wsFederation>` Reprezentowany przez element <xref:System.IdentityModel.Services.Configuration.WSFederationElement> klasy. Sam obiekt konfiguracji jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> klasy. Pojedynczy <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> wystąpienia jest ustawiona na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiektu, który jest dostępny za pośrednictwem <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości i zapewnia konfigurację WSFAM.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono XML `<wsFederation>` element, który określa ustawienia dla WSFAM.  
  
> [!WARNING]
>  W tym przykładzie WSFAM nie jest wymagane do używania protokołu HTTPS. Jest to spowodowane `requireHttps` atrybutu `<wsFederation>` ustawiono element `false`. To ustawienie nie jest zalecane dla większości środowisk produkcyjnych, jak może stanowić zagrożenie bezpieczeństwa.  
  
```xml
<wsFederation passiveRedirectEnabled="true"   
              issuer="http://localhost:15839/wsFederationSTS/Issue"   
              realm="http://localhost:50969/"   
              reply="http://localhost:50969/"   
              requireHttps="false"   
              signOutReply="http://localhost:50969/SignedOutPage.html"   
              signOutQueryString="Param1=value2&Param2=value2"   
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
