---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152466"
---
# \<wsFederation>
Zapewnia konfigurację programu <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederation>**  
  
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
|authenticationType|Identyfikator URI, który określa typ uwierzytelniania. Ustawia parametr wauth żądania logowania protokołu WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wauth nie jest uwzględniony w żądaniu.|  
|świeżości|Żądany maksymalny wiek żądań uwierzytelniania (w minutach). Ustawia parametr wfresh żądania logowania protokołu WS-Federation. Opcjonalny. Wartością domyślną jest zero. Opcjonalny. **Ostrzeżenie:**  W następnej wersji .NET Framework 4,5 `freshness` atrybut będzie typu, `xs:string` a jego wartość domyślna to `null` .|  
|homeRealm|Obszar macierzysty dostawcy tożsamości (dostawcy tożsamości), który ma być używany do uwierzytelniania. Ustawia parametr "wh" logowania do usługi WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr Wh nie jest uwzględniony w żądaniu.|  
|issuer|Identyfikator URI wystawcy zamierzonego tokenu. Ustawia podstawowy adres URL żądań logowania do usługi WS-Federation i wymagane żądania wylogowania.|  
|persistentCookiesOnPassiveRedirects|Określa, czy trwałe pliki cookie są wydawane przy uwierzytelnianiu. Opcjonalny. Wartość domyślna to "false". pliki cookie nie są wystawiane.|  
|passiveRedirectEnabled|Określa, czy WSFAM jest włączona, aby automatycznie przekierować nieautoryzowane żądania do usługi STS. Opcjonalny. Wartość domyślna to "true", nieautoryzowane żądania są automatycznie przekierowywane.|  
|policy|Adres URL określający lokalizację odpowiednich zasad do użycia w żądaniach logowania. Wartość domyślna to pusty ciąg. Ustawia parametr WP żądania logowania protokołu WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr WP nie jest uwzględniony w żądaniu.|  
|obszarów|Identyfikator URI obszaru żądającego. (Identyfikator URI, który identyfikuje jednostkę uzależnioną (RP) do usługi tokenu zabezpieczającego (STS). Ustawia parametr żądania logowania do usługi WS-Federation wtrealm. Wymagany.|  
|przesyła|Adres URL identyfikujący adres, pod którym aplikacja jednostki uzależnionej (RP) chce otrzymywać odpowiedzi z usługi tokenu zabezpieczającego (STS). Ustawia parametr wreply żądania logowania protokołu WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wreply nie jest uwzględniony w żądaniu.|  
|żądając|Żądanie wystawienia tokenu. Ustawia parametr wreq żądania logowania protokołu WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wreq nie jest uwzględniony w żądaniu. W przypadku nieuwzględnienia parametru wreq lub wreqptr w żądaniu oznacza, że usługa STS wie, jakiego rodzaju tokenu należy wystawić.|  
|requestPtr|Adres URL, który określa lokalizację żądania wystawiania tokenu. Ustawia parametr wreqptr żądania. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wreqptr nie jest uwzględniony w żądaniu. W przypadku nieuwzględnienia parametru wreq lub wreqptr w żądaniu oznacza, że usługa STS wie, jakiego rodzaju tokenu należy wystawić.|  
|Określ|Określa, czy komunikacja z usługą tokenu zabezpieczającego (STS) musi korzystać z protokołu HTTPS. Opcjonalny. Wartość domyślna to "true", należy użyć protokołu HTTPS.|  
|zasób|Identyfikator URI, który identyfikuje dostęp do zasobu, jednostki uzależnionej (RP) do usługi tokenu zabezpieczającego (STS). Opcjonalny. Ustawia parametr wres żądania logowania protokołu WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wres nie jest uwzględniony w żądaniu. **Uwaga:** wres jest starszym parametrem. Określ `realm` atrybut, aby zamiast tego użyć parametru wtrealm.|  
|signInQueryString|Udostępnia punkt rozszerzalności, aby określić parametry zapytania zdefiniowane przez aplikację w adresie URL żądania logowania za pomocą protokołu WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry nie powinny być zawarte w żądaniu. Parametry są określone jako fragment ciągu zapytania przy użyciu następującej formy: `"param1=value1&param2=value2&param3=value3"` i tak dalej. **Uwaga:**  W pliku konfiguracji znak "&" w ciągu zapytania musi być określony za pomocą odwołania do jednostki `&` .|  
|signOutQueryString|Udostępnia punkt rozszerzalności, aby określić parametry zapytania zdefiniowane przez aplikację w adresie URL żądania logowania za pomocą protokołu WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry nie powinny być zawarte w żądaniu. Parametry są określone jako fragment ciągu zapytania przy użyciu następującej formy: `"param1=value1&param2=value2&param3=value3"` i tak dalej. **Uwaga:**  W pliku konfiguracji znak "&" w ciągu zapytania musi być określony za pomocą odwołania do jednostki `&` .|  
|signOutReply|Określa adres URL, do którego klient powinien zostać przekierowany przez usługę tokenu zabezpieczającego (STS) podczas wylogowywania pasywnego za pomocą protokołu WS-Federation. Ustawia parametr wreply w żądaniu wylogowania usługi WS-Federation. Opcjonalny. Wartość domyślna to pusty ciąg, który określa, że żadne dodatkowe parametry nie powinny być zawarte w żądaniu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (sam).|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć elementu, `<wsFederation>` Aby skonfigurować domyślne ustawienia parametrów protokołu WS-Federation i domyślne zachowanie dla WSFAM. Ustawienia parametrów protokołu WS-Federation zdefiniowane w obszarze `<wsFederation>` zestaw elementów równoważne właściwości udostępniane przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasę. Te właściwości pozostają takie same dla każdego żądania wystawionego przez WSFAM. Parametry protokołu WS-Federation można zmienić dynamicznie podczas przetwarzania żądania przez dodanie obsługi zdarzeń dla zdarzeń uwidocznionych przez WSFAM; na przykład <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> zdarzenie. Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy.  
  
 `<wsFederation>`Element jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.WSFederationElement> klasę. Sam obiekt konfiguracji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> klasę. Pojedyncze <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> wystąpienie jest ustawione na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiekcie, do którego dostęp jest uzyskiwany za pomocą <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości i zawiera konfigurację dla WSFAM.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia `<wsFederation>` element określający ustawienia dla WSFAM.  
  
> [!WARNING]
> W tym przykładzie WSFAM nie jest wymagana do korzystania z protokołu HTTPS. Jest to spowodowane tym, że `requireHttps` atrybut w `<wsFederation>` elemencie jest ustawiony `false` . To ustawienie nie jest zalecane w przypadku większości środowisk produkcyjnych, ponieważ może stanowić zagrożenie bezpieczeństwa.  
  
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
