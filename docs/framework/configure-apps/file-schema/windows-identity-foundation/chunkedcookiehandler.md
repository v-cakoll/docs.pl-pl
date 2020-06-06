---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252106"
---
# \<chunkedCookieHandler>
Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler> . Ten element może być obecny tylko wtedy, gdy `mode` atrybut `<cookieHandler>` elementu ma wartość "default" lub "fragmentaryczne".  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Rozmiaru fragmentu|Maksymalny rozmiar (w znakach) danych plików cookie protokołu HTTP dla dowolnego z plików cookie protokołu HTTP. Należy zachować ostrożność podczas dopasowywania rozmiaru fragmentu. Przeglądarki sieci Web mają różne limity rozmiaru plików cookie i liczby dozwolone dla poszczególnych domen. Na przykład oryginalna Specyfikacja programu Netscape zakłada następujące limity: 300 plików cookie łącznie, 4096 bajtów na nagłówek pliku cookie (w tym metadanych, a nie tylko wartość cookie) oraz 20 plików cookie na domenę. Wartość domyślna to 2000. Wymagany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , że program <xref:System.IdentityModel.Services.SessionAuthenticationModule> (sam) używa do odczytu i zapisu plików cookie.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku określenia <xref:System.IdentityModel.Services.ChunkedCookieHandler> przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "domyślny" lub "podzielony" można określić rozmiar fragmentu, którego program obsługi plików cookie używa do odczytu i zapisu plików cookie, dołączając `<chunkedCookieHandler>` element podrzędny i ustawiając jego `chunkSize` atrybut. Jeśli `<chunkedCookieHandler>` element nie jest obecny, używany jest domyślny rozmiar fragmentu wynoszący 2000 bajtów. Nie można określić tego elementu, gdy `mode` atrybut jest ustawiony na wartość "Custom".  
  
 `<chunkedCookieHandler>`Element jest reprezentowany przez <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> klasę.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład służy do konfigurowania programu obsługi plików cookie fragmentarycznego, który zapisuje pliki cookie w fragmentach 3000 bajtów.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
