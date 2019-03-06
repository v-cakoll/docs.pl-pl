---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 801970ec05fc88587a5b45b5bb3a855d1a81afb3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356094"
---
# <a name="wsfederation"></a>\<wsFederation>
Udostępnia konfigurację dla <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
\<system.identityModel.services>  
\<federationConfiguration>  
\<wsFederation>  
  
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
|Element authenticationType|Identyfikator URI, który określa typ uwierzytelniania. Ustawia parametr wauth żądanie logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wauth nie jest uwzględniony w żądaniu.|  
|aktualność|Żądany maksymalny wiek żądań uwierzytelniania, w ciągu kilku minut. Ustawia parametr wfresh żądanie logowania usługi WS-Federation. Opcjonalna. Wartością domyślną jest zero. Opcjonalna. **Ostrzeżenie:**  W kolejnej wersji programu .NET Framework 4.5 `freshness` atrybut będzie mieć typ `xs:string` i jego wartość domyślna będzie `null`.|  
|homeRealm|Obszar macierzysty dostawcy tożsamości (IP) w celu użycia na potrzeby uwierzytelniania. Ustawia parametr Wh żądanie logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr Wh nie jest uwzględniony w żądaniu.|  
|issuer|Identyfikator URI zamierzony wystawcy tokenów. Ustawia podstawowy adres URL protokołu WS-Federation logowania żądania i żądania wylogowania wymagane.|  
|persistentCookiesOnPassiveRedirects|Określa, czy trwałe pliki cookie są wydawane na uwierzytelnianie. Opcjonalna. Wartość domyślna to "false", pliki cookie nie są wydawane.|  
|passiveRedirectEnabled|Określa, czy WSFAM jest włączone automatyczne przekierowywanie nieautoryzowanych żądań do usługi STS. Opcjonalna. Wartość domyślna to "true", automatycznie przekierowany nieautoryzowanych żądań.|  
|Zasady|Adres URL, który określa lokalizację odpowiednich zasad do użycia w odpowiedzi na żądania logowania. Wartość domyślna to ciąg pusty. Ustawia parametr wp żądanie logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wp nie jest uwzględniony w żądaniu.|  
|obszar|Identyfikator URI żądania obszaru. (Identyfikator URI, który identyfikuje uzależnionej (RP) do usługi tokenu zabezpieczającego (STS).) Ustawia parametr żądania wtrealm logowania usługi WS-Federation żądania. Wymagana.|  
|Odpowiedz|Adres URL, który określa adres, w którym chcesz otrzymywać odpowiedzi z Usługa tokenu zabezpieczającego (STS) aplikacji jednostki uzależnionej (RP). Ustawia parametr wreply żądanie logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wreply nie jest uwzględniony w żądaniu.|  
|Żądanie|Żądanie wystawiania tokenu. Ustawia parametr wreq żądanie logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wreq nie jest uwzględniony w żądaniu. Z tym wreq lub parametr wreqptr żądania oznacza, że Usługa STS wie, jakiego rodzaju token do wystawiania.|  
|requestPtr|Adres URL, który określa lokalizację żądania wystawiania tokenu. Ustawia parametr wreqptr żądania. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wreqptr nie jest uwzględniony w żądaniu. Z tym wreq lub parametr wreqptr żądania oznacza, że Usługa STS wie, jakiego rodzaju token do wystawiania.|  
|requireHttps|Określa, czy komunikacja z usługi tokenu zabezpieczającego (STS) musi używać protokołu HTTPS. Opcjonalna. Wartość domyślna to "true", należy użyć protokołu HTTPS.|  
|zasób|Identyfikator URI, który identyfikuje zasób, którego uzyskiwany jest dostęp, podmiotu zależnego (RP) do do usługi tokenu zabezpieczającego (STS). Opcjonalna. Ustawia parametr wres żądanie logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że parametr wres nie jest uwzględniony w żądaniu. **Uwaga:** wres jest parametrem starszej wersji. Określ `realm` atrybutu, aby zamiast tego użyj parametru wtrealm.|  
|signInQueryString|Udostępnia punkt rozszerzeń, aby określić parametry zapytań aplikacji zdefiniowanej w adresie URL żądania logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry powinny być uwzględnione w żądaniu. Parametry są określane jako fragment ciągu zapytania za pomocą następującej postaci: `"param1=value1&param2=value2&param3=value3"` i tak dalej. **Uwaga:**  W pliku konfiguracji "&" znak w ciągu zapytania musi być określona za pomocą jego odwołania do jednostki `&`.|  
|signOutQueryString|Udostępnia punkt rozszerzeń, aby określić parametry zapytań aplikacji zdefiniowanej w adresie URL żądania logowania usługi WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry powinny być uwzględnione w żądaniu. Parametry są określane jako fragment ciągu zapytania za pomocą następującej postaci: `"param1=value1&param2=value2&param3=value3"` i tak dalej. **Uwaga:**  W pliku konfiguracji "&" znak w ciągu zapytania musi być określona za pomocą jego odwołania do jednostki `&`.|  
|signOutReply|Określa adres URL, do którego klient powinien być przekierowany przez usługę tokenu zabezpieczającego (STS) podczas wyrejestrowywania za pośrednictwem protokołu WS-Federation passive. Ustawia parametr wreply żądania wylogowania protokołu WS-Federation. Opcjonalna. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry powinny być uwzględnione w żądaniu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `<wsFederation>` elementu, aby skonfigurować domyślne ustawienia parametru WS-Federation i domyślne zachowanie dla WSFAM. Zdefiniowane w obszarze ustawienia parametru WS-Federation `<wsFederation>` element ustawiony równoważne właściwości udostępnianych przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy. Te właściwości pozostają takie same dla każdego żądania, wystawiony przez WSFAM. Parametry protokołu WS-Federation można zmieniać dynamicznie podczas przetwarzania przez dodanie obsługi zdarzeń dla zdarzenia udostępnianych przez WSFAM; żądania na przykład <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> zdarzeń. Aby uzyskać więcej informacji, zobacz dokumentację dla <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy.  
  
 `<wsFederation>` Element jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.WSFederationElement> klasy. Sam obiekt konfiguracji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> klasy. Pojedynczy <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> wystąpienia jest ustawiona na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiekt, który jest dostępny za pośrednictwem <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości i udostępnia konfigurację dla WSFAM.  
  
## <a name="example"></a>Przykład  
 Pokazano w poniższym XML `<wsFederation>` element, który określa ustawienia dla WSFAM.  
  
> [!WARNING]
>  W tym przykładzie WSFAM nie jest wymagany do używania protokołu HTTPS. Jest to spowodowane `requireHttps` atrybutu na `<wsFederation>` ustawiono element `false`. To ustawienie nie jest zalecane dla większości środowisk produkcyjnych, ponieważ może on stwarzać zagrożenie bezpieczeństwa.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
