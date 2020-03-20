---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152466"
---
# <a name="wsfederation"></a>\<wsFederation>
Zapewnia konfigurację <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
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
|authenticationType|Identyfikator URI określający typ uwierzytelniania. Ustawia parametr WS-Federation wauth żądania logowania. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wauth nie jest uwzględniony w żądaniu.|  
|Świeżość|Żądany maksymalny wiek żądań uwierzytelniania w minutach. Ustawia parametr WS-Federation wfresh żądania logowania. Element opcjonalny. Wartością domyślną jest zero. Element opcjonalny. **Ostrzeżenie:**  W następnej wersji programu .NET Framework 4.5 `freshness` atrybut `xs:string` będzie typu, `null`a jego wartością domyślną będzie .|  
|Homerealm|Sfera domowa dostawcy tożsamości (IdP) do użycia do uwierzytelniania. Ustawia parametr WS-Federation whr żądania logowania. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr whr nie jest uwzględniony w żądaniu.|  
|issuer|Identyfikator URI zamierzonego wystawcy tokenu. Ustawia podstawowy adres URL żądań logowania federacji WS i wymaganych żądań wylogowywania.|  
|persistentCookiesOnPassiveRedirects|Określa, czy trwałe pliki cookie są wystawiane podczas uwierzytelniania. Element opcjonalny. Wartość domyślna to "false", pliki cookie nie są wystawiane.|  
|Passiveredirectenabled|Określa, czy w uwolionej jest funkcja WSFAM automatycznego przekierowywania nieautoryzowanych żądań do sts. Element opcjonalny. Wartość domyślna to "true", nieautoryzowane żądania są automatycznie przekierowywane.|  
|policy|Adres URL określający lokalizację odpowiednich zasad do użycia w żądaniach logowania. Wartość domyślna to pusty ciąg. Ustawia parametr wp żądania logowania federacji WS. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wp nie jest uwzględniony w żądaniu.|  
|Obszaru|Identyfikator URI obszaru żądającego. (Identyfikator URI identyfikujący jednostkę uzależniającą (RP) w usłudze tokenu zabezpieczającego (STS).) Ustawia parametr żądania wtrealm WS-Federation. Wymagany.|  
|Odpowiedź|Adres URL identyfikujący adres, pod którym aplikacja jednostki uzależniającej (RP) chce otrzymywać odpowiedzi z usługi tokenu zabezpieczającego (STS). Ustawia parametr WS-Federation sign-in request wreply. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wreply nie jest uwzględniony w żądaniu.|  
|Żądanie|Żądanie wystawienia tokenu. Ustawia parametr WS-Federation wreq żądania logowania. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wreq nie jest uwzględniony w żądaniu. Nie wliczając wreq lub wreqptr parametr w żądaniu oznacza, że STS wie, jakiego rodzaju token do wydania.|  
|wniosekPtr|Adres URL określający lokalizację żądania wystawienia tokenu. Ustawia parametr wreqptr żądania. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wreqptr nie jest uwzględniony w żądaniu. Nie wliczając wreq lub wreqptr parametr w żądaniu oznacza, że STS wie, jakiego rodzaju token do wydania.|  
|wymagaj usługiHttps|Określa, czy komunikacja z usługą tokenu zabezpieczającego (STS) musi używać protokołu HTTPS. Element opcjonalny. Wartość domyślna to "true", musi być używany protokół HTTPS.|  
|zasób|Identyfikator URI, który identyfikuje zasób, do który uzyskuje się dostęp, jednostkę uzależniającą (RP), do usługi tokenu zabezpieczającego (STS). Element opcjonalny. Ustawia parametr WS-Federation wres żądania logowania. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że parametr wres nie jest uwzględniony w żądaniu. **Uwaga:** wres jest parametrem legacy. Określ `realm` atrybut, który ma być używany przez parametr wtrealm.|  
|signInQueryStrowanie|Zapewnia punkt rozszerzalności, aby określić parametry kwerendy zdefiniowane przez aplikację w adresie URL żądania logowania Federacji WS. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że w żądaniu nie powinny być uwzględniane żadne dodatkowe parametry. Parametry są określone jako fragment ciągu kwerendy `"param1=value1&param2=value2&param3=value3"` przy użyciu następującego formularza: i tak dalej. **Uwaga:**  W pliku konfiguracyjnym znak "&" w ciągu zapytania musi `&`być określony przy użyciu odwołania do encji, .|  
|znakOutQueryStrowanie|Zapewnia punkt rozszerzalności, aby określić parametry kwerendy zdefiniowane przez aplikację w adresie URL żądania logowania Federacji WS. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że w żądaniu nie powinny być uwzględniane żadne dodatkowe parametry. Parametry są określone jako fragment ciągu kwerendy `"param1=value1&param2=value2&param3=value3"` przy użyciu następującego formularza: i tak dalej. **Uwaga:**  W pliku konfiguracyjnym znak "&" w ciągu zapytania musi `&`być określony przy użyciu odwołania do encji, .|  
|signOutReply (Niezwykłe)|Określa adres URL, do którego klient powinien być przekierowywał przez usługę tokenu zabezpieczającego (STS) podczas wylogowania pasywnego za pośrednictwem protokołu Federacji WS. Ustawia parametr wreply w żądaniu wylogowania federacji WS. Element opcjonalny. Wartość domyślna to pusty ciąg, który określa, że w żądaniu nie powinny być uwzględniane żadne dodatkowe parametry.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Zawiera ustawienia, które <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurują (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą `<wsFederation>` tego elementu można skonfigurować domyślne ustawienia parametrów federacji WS i domyślne zachowanie programu WSFAM. Ustawienia parametrów Federacji WS zdefiniowane w `<wsFederation>` ramach <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> zestawu elementów równoważnych właściwości udostępniane przez klasę. Te właściwości pozostają takie same dla każdego żądania wydanego przez WSFAM. Można dynamicznie zmieniać parametry federacji WS podczas przetwarzania żądań, dodając programy obsługi zdarzeń dla zdarzeń ujawnionych przez program WSFAM; na przykład <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> zdarzenie. Aby uzyskać więcej informacji, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> zobacz dokumentację dla klasy.  
  
 Element `<wsFederation>` jest reprezentowany <xref:System.IdentityModel.Services.Configuration.WSFederationElement> przez klasę. Sam obiekt konfiguracji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> klasę. Pojedyncze <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> wystąpienie jest <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> ustawiane na obiekcie, który jest dostępny za pośrednictwem <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości i zapewnia konfigurację dla WSFAM.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia `<wsFederation>` element określający ustawienia w formacie WSFAM.  
  
> [!WARNING]
> W tym przykładzie WSFAM nie jest wymagane do korzystania z protokołu HTTPS. Dzieje się `requireHttps` tak, ponieważ `<wsFederation>` atrybut `false`elementu jest ustawiony . To ustawienie nie jest zalecane w większości środowisk produkcyjnych, ponieważ może stanowić zagrożenie dla bezpieczeństwa.  
  
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

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
