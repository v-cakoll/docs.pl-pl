---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 6c62100b2445ae10a83ebd9e7d154a6e2aa14e0b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942799"
---
# <a name="cookiehandler"></a>\<cookieHandler>
Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , że program (sam) używa do odczytu i zapisu plików cookie.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
  
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
|nazwa|Określa nazwę podstawową dla wszelkich zapisanych plików cookie. Wartość domyślna to "FedAuth".|  
|ścieżka|Określa wartość ścieżki dla dowolnych plików cookie, które są zapisywane. Wartość domyślna to "HttpRuntime. AppDomainAppVirtualPath".|  
|tryb|Jedna z <xref:System.IdentityModel.Services.CookieHandlerMode> wartości, która określa rodzaj obsługi plików cookie używany przez sam. Można użyć następujących wartości:<br /><br /> -"Domyślne" — taka sama jak "fragmentaryczna".<br />-"Fragmentaryczne" — używa wystąpienia <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy. Ten program obsługi plików cookie zapewnia, że poszczególne pliki cookie nie przekraczają maksymalnego rozmiaru. Jest to realizowane przez potencjalnie "dzielenie" jednego logicznego pliku cookie na kilka plików cookie w sieci.<br />-"Custom" — używa wystąpienia klasy niestandardowej pochodzącej od <xref:System.IdentityModel.Services.CookieHandler>. Klasa pochodna odwołuje `<customCookieHandler>` się do elementu podrzędnego.<br /><br /> Wartość domyślna to "domyślne".|  
|persistentSessionLifetime|Określa okres istnienia sesji trwałych. Jeśli wartość jest równa zero, sesje przejściowe są zawsze używane. Wartość domyślna to "0:0:0", która określa przejściową sesję. Wartość maksymalna to "365:0:0", która określa sesję z 365 dni. Wartość należy określić zgodnie z następującymi ograniczeniami: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, gdzie pierwsza wartość określa liczbę dni, wartość środkowa (jeśli jest obecna) określa godziny, a wartość z prawej strony (jeśli jest obecna) określa minuty.|  
|requireSsl|Określa, czy flaga "Secure" jest emitowana dla dowolnych plików cookie pisanych. Jeśli ta wartość jest ustawiona, pliki cookie sesji logowania będą dostępne tylko za pośrednictwem protokołu HTTPS. Wartość domyślna to "true".|  
|hideFromScript|Określa, czy flaga "HttpOnly" jest emitowana dla dowolnych plików cookie pisanych. Niektóre przeglądarki sieci Web uznają tę flagę, chroniąc skrypt po stronie klienta przed dostępem do wartości cookie. Wartość domyślna to "true".|  
|domena|Wartość domeny dla dowolnych plików cookie pisanych. Wartość domyślna to "".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Ten element może być obecny tylko wtedy, `mode` gdy atrybut `<cookieHandler>` elementu ma wartość "default" lub "fragmentaryczne".|  
|[\<customCookieHandler>](customcookiehandler.md)|Ustawia niestandardowy typ procedury obsługi plików cookie. Ten element musi być obecny, `mode` Jeśli atrybut `<cookieHandler>` elementu ma wartość "Custom". Nie może być obecne dla żadnych innych wartości `mode` atrybutu. Typ niestandardowy musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (sam).|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.IdentityModel.Services.CookieHandler> Jest odpowiedzialny za odczytywanie i zapisywanie nieprzetworzonych plików cookie na poziomie protokołu HTTP. Można skonfigurować albo <xref:System.IdentityModel.Services.ChunkedCookieHandler> niestandardową procedurę obsługi plików cookie pochodną <xref:System.IdentityModel.Services.CookieHandler> klasy.  
  
 Aby skonfigurować procedurę obsługi plików cookie podzielony na fragmenty, ustaw atrybut Mode na "fragmentaryczny" lub "domyślny". Domyślny rozmiar fragmentu to 2000 bajtów, ale opcjonalnie można określić inny rozmiar fragmentu, dołączając `<chunkedCookieHandler>` element podrzędny.  
  
 Aby skonfigurować procedurę obsługi niestandardowego pliku cookie, ustaw atrybut Mode na "Custom". Należy również określić `<customCookieHandler>` element podrzędny, który odwołuje się do typu niestandardowego programu obsługi.  
  
 Element jest reprezentowany <xref:System.IdentityModel.Services.CookieHandlerElement> przez klasę. `<cookieHandler>` Procedura obsługi plików cookie określona w konfiguracji jest dostępna <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> we właściwości <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> obiektu ustawionego we <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML pokazuje `<cookieHandler>` element. W tym przykładzie, ponieważ `mode` atrybut nie jest określony, domyślny program obsługi plików cookie będzie używany przez sam. Jest to wystąpienie <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy. Ponieważ element `<chunkedCookieHandler>` podrzędny nie jest określony, zostanie użyty domyślny rozmiar fragmentu. Protokół HTTPS nie będzie wymagany, `requireSsl` ponieważ atrybut jest ustawiony. `false`  
  
> [!WARNING]
>  W tym przykładzie protokół HTTPS nie jest wymagany do zapisywania plików cookie sesji. Jest to spowodowane tym `requireSsl` , że atrybut `<cookieHandler>` w elemencie jest ustawiony `false`na. To ustawienie nie jest zalecane w przypadku większości środowisk produkcyjnych, ponieważ może stanowić zagrożenie bezpieczeństwa.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
