---
title: '&lt;cookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 99bf6edb4e4f631eba292990c65c1f0c8553d8c0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235299"
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) używa na odczytywanie i zapisywanie plików cookie.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Określa nazwę podstawową dla żadnych plików cookie, zapisane. Wartość domyślna to "FedAuth".|  
|ścieżka|Określa wartość ścieżki na pliki cookie zapisywane. Wartość domyślna to "Elementu HttpRuntime.AppDomainAppVirtualPath".|  
|tryb|Jedną z <xref:System.IdentityModel.Services.CookieHandlerMode> wartości, które określa rodzaj obsługi plików cookie używany przez tego Zabronić. Mogą być używane następujące wartości:<br /><br /> -"Default" — taka sama jak "Fragmentaryczne".<br />-"Fragmentaryczne" — używa wystąpienia <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy. Ten program obsługi plików cookie sprawdza, czy poszczególnych plików cookie nie przekracza maksymalny rozmiar zestawu. Jest to osiągane przez potencjalnie "segmentu" jednego logicznego pliku cookie do liczby plików cookie w locie.<br />-"Niestandardowy" — używa wystąpienia niestandardowej klasy pochodzącej od <xref:System.IdentityModel.Services.CookieHandler>. Odwołuje się do klasy pochodnej `<customCookieHandler>` elementu podrzędnego.<br /><br /> Wartość domyślna to "Default".|  
|persistentSessionLifetime|Określa czas istnienia trwałych sesji. Jeśli zero, przejściowe sesje są zawsze używane. Wartość domyślna to "0:0:0", który określa przejściowy sesji. Wartość maksymalna to "365:0:0", który określa sesję 365 dni. Wartość powinna być określona zgodnie z następujących ograniczeń: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, gdzie wartość lewej określa dni, wartość środkowa (jeśli istnieje) określa godziny, a wartość po prawej stronie (jeśli istnieje) określa minut.|  
|Wartość parametru RequireSsl|Określa, czy flaga "Secure" jest emitowane w żadnych plików cookie, zapisane. Jeśli ta wartość jest ustawiona, pliki cookie sesji logowania tylko będą dostępne za pośrednictwem protokołu HTTPS. Wartość domyślna to "true".|  
|hideFromScript|Określa, czy flaga "HttpOnly" jest emitowane w żadnych plików cookie, zapisane. Niektóre przeglądarki sieci web honorować tej flagi, przechowując skryptu po stronie klienta uzyskanie dostępu do wartości pliku cookie. Wartość domyślna to "true".|  
|domena|Wartość domeny żadnych plików cookie, zapisane. Wartość domyślna to "".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Ten element może być tylko obecne Jeśli `mode` atrybutu `<cookieHandler>` element to "Default" lub "Fragmentaryczne".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Ustawia typ procedury obsługi niestandardowego pliku cookie. Ten element musi być obecny Jeśli `mode` atrybutu `<cookieHandler>` element jest "Niestandardowy". Nie może być stosowany w przypadku wszystkich innych wartości z `mode` atrybutu. Niestandardowy typ musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.IdentityModel.Services.CookieHandler> Odpowiada za odczytywanie i zapisywanie nieprzetworzone pliki cookie HTTP protokołu poziom. Można skonfigurować <xref:System.IdentityModel.Services.ChunkedCookieHandler> lub obsługi niestandardowych plików cookie jest pochodną <xref:System.IdentityModel.Services.CookieHandler> klasy.  
  
 Aby skonfigurować plik cookie z podziałem program obsługi, ustaw atrybut tryb "Fragmentaryczne" lub "Default". Domyślny rozmiar fragmentu to 2000 bajtów, ale Opcjonalnie można określić rozmiaru fragmentu różnych umieszczając `<chunkedCookieHandler>` elementu podrzędnego.  
  
 Aby skonfigurować program obsługi niestandardowych plików cookie, ustaw atrybut tryb na "Niestandardowe". Należy także określić `<customCookieHandler>` elementu podrzędnego, który odwołuje się typ programu obsługi niestandardowych.  
  
 `<cookieHandler>` Element jest reprezentowany przez <xref:System.IdentityModel.Services.CookieHandlerElement> klasy. Program obsługi plików cookie, który został określony w konfiguracji jest dostępny z <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> właściwość <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiektu ustawione na <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Pokazano w poniższym XML `<cookieHandler>` elementu. W tym przykładzie ponieważ `mode` atrybut nie zostanie określony, domyślny program obsługi plików cookie, które będą używane przez Menedżera kont zabezpieczeń. To wystąpienie <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy. Ponieważ `<chunkedCookieHandler>` element podrzędny nie zostanie określony, będzie używany domyślny rozmiar fragmentu. Protokół HTTPS nie będzie wymagane, ponieważ `requireSsl` ma ustawioną wartość atrybutu `false`.  
  
> [!WARNING]
>  W tym przykładzie HTTPS nie jest wymagany do zapisania plików cookie sesji. Jest to spowodowane `requireSsl` atrybutu na `<cookieHandler>` element jest ustawiony na wartość `false`. To ustawienie nie jest zalecane dla większości środowisk produkcyjnych, ponieważ może on stwarzać zagrożenie bezpieczeństwa.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
