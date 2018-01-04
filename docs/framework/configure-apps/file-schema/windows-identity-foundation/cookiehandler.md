---
title: '&lt;cookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 302ccb3d95fc982ec7950dc7808dce61b263c481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> który <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) używany do odczytywania i zapisywania plików cookie.  
  
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
|nazwa|Określa podstawową nazwę żadnych plików cookie zapisywane. Wartość domyślna to "FedAuth".|  
|ścieżka|Określa wartość ścieżki na pliki cookie zapisywane. Wartość domyślna to "Elementu HttpRuntime.AppDomainAppVirtualPath".|  
|tryb|Jeden z <xref:System.IdentityModel.Services.CookieHandlerMode> wartości, które określa rodzaj obsługi plików cookie używany przez Menedżera kont zabezpieczeń. Mogą być używane następujące wartości:<br /><br /> -"Default" — taka sama jak "Fragmentaryczne".<br />-"Fragmentaryczne" — używa wystąpienia <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy. Ta obsługa plików cookie sprawdza, czy poszczególne pliki cookie przekracza maksymalny rozmiar zestawu. Jest to osiągane przez potencjalnie "podziału" jednego logicznego pliku cookie na liczbę plików cookie w locie.<br />-"Niestandardowe" — używa wystąpienia klasy niestandardowej pochodzącej od <xref:System.IdentityModel.Services.CookieHandler>. Klasa pochodna odwołuje się do niego `<customCookieHandler>` element podrzędny.<br /><br /> Wartość domyślna to "Domyślny".|  
|persistentSessionLifetime|Określa okres istnienia trwały sesji. Jeśli zero, są zawsze używane sesje przejściowej. Wartość domyślna to "0:0:0", określający przejściowej sesji. Maksymalna wartość to "365:0:0", która określa sesję do 365 dni. Wartość powinna być określona zgodnie z następujących ograniczeń: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, gdzie wartość lewej określa dni, godziny określa wartość środkowa (jeśli istnieje), a wartość prawej (jeśli istnieje) określa minut.|  
|parametru requireSsl|Określa, czy flaga "Secure" jest emitowany żadnych plików cookie zapisywane. Jeśli ta wartość jest ustawiona, plików cookie sesji logowania tylko będą dostępne za pośrednictwem protokołu HTTPS. Wartość domyślna to "true".|  
|hideFromScript|Określa, czy flagi "HttpOnly" jest emitowany żadnych plików cookie zapisywane. Niektóre przeglądarki sieci web honorować tej flagi przechowując skryptu po stronie klienta, dostęp do wartości pliku cookie. Wartość domyślna to "true".|  
|domena|Wartość domeny żadnych plików cookie zapisywane. Wartość domyślna to "".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Ten element może być tylko obecny Jeśli `mode` atrybutu `<cookieHandler>` jest element "Default" lub "Fragmentaryczne".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Ustawia typ obsługi niestandardowego pliku cookie. Ten element musi być obecny Jeśli `mode` atrybutu `<cookieHandler>` element jest "Custom". Nie może być stosowany w przypadku wszystkich innych wartości z `mode` atrybutu. Niestandardowy typ musi pochodzić z <xref:System.IdentityModel.Services.CookieHandler> klasy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.IdentityModel.Services.CookieHandler> Jest odpowiedzialny za odczytywanie i zapisywanie nieprzetworzone pliki cookie HTTP poziomu protokołu. Można skonfigurować <xref:System.IdentityModel.Services.ChunkedCookieHandler> lub obsługi niestandardowej pliku cookie z <xref:System.IdentityModel.Services.CookieHandler> klasy.  
  
 W celu skonfigurowania obsługi podzielony plik cookie, należy ustawić atrybut mode "Fragmentaryczne" lub "Default". Domyślny rozmiar fragmentu to 2000 bajtów, ale Opcjonalnie można określić rozmiaru fragmentu innego umieszczając `<chunkedCookieHandler>` element podrzędny.  
  
 Aby skonfigurować program obsługi niestandardowego pliku cookie, ustaw tryb atrybutu "Niestandardowe". Należy także określić `<customCookieHandler>` elementu podrzędnego, który odwołuje się do typu z niestandardowego programu obsługi.  
  
 `<cookieHandler>` Reprezentowany przez element <xref:System.IdentityModel.Services.CookieHandlerElement> klasy. Program obsługi plików cookie, który został określony w konfiguracji jest dostępny z <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> właściwość <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiektu ustawione na <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono XML `<cookieHandler>` elementu. W tym przykładzie ponieważ `mode` atrybut nie jest określony, będzie używany domyślny program obsługi plików cookie przez Menedżera kont zabezpieczeń. Jest to wystąpienie <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy. Ponieważ `<chunkedCookieHandler>` element podrzędny nie jest określony, zostanie użyty domyślny rozmiar fragmentu. Protokół HTTPS nie będzie wymagane, ponieważ `requireSsl` ustawiono atrybut `false`.  
  
> [!WARNING]
>  W tym przykładzie protokół HTTPS nie jest wymagany do zapisania plików cookie sesji. Jest to spowodowane `requireSsl` atrybutu `<cookieHandler>` element jest ustawiony na wartość `false`. To ustawienie nie jest zalecane dla większości środowisk produkcyjnych, jak może stanowić zagrożenie bezpieczeństwa.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
