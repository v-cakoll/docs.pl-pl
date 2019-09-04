---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252106"
---
# <a name="chunkedcookiehandler"></a>\<chunkedCookieHandler>
Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Ten element może być obecny tylko wtedy, `mode` gdy atrybut `<cookieHandler>` elementu ma wartość "default" lub "fragmentaryczne".  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chunkedCookieHandler >**  
  
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
|Rozmiaru fragmentu|Maksymalny rozmiar (w znakach) danych plików cookie protokołu HTTP dla dowolnego z plików cookie protokołu HTTP. Należy zachować ostrożność podczas dopasowywania rozmiaru fragmentu. Przeglądarki sieci Web mają różne limity rozmiaru plików cookie i liczby dozwolone dla poszczególnych domen. Na przykład oryginalna Specyfikacja Netscape zaznaczył te limity: 300 plików cookie łącznie, 4096 bajtów na nagłówek pliku cookie (w tym metadane, a nie tylko wartość cookie) oraz 20 plików cookie na domenę. Wartość domyślna to 2000. Wymagana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , że program (sam) używa do odczytu i zapisu plików cookie.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku określenia <xref:System.IdentityModel.Services.ChunkedCookieHandler> przez `mode` ustawienie atrybutu `<cookieHandler>` elementu na "domyślny" lub "podzielony" można określić rozmiar fragmentu, którego program obsługi plików cookie używa `<chunkedCookieHandler>` do odczytu i zapisu plików cookie, włączając element podrzędny i `chunkSize` Ustawianie atrybutu. `<chunkedCookieHandler>` Jeśli element nie jest obecny, używany jest domyślny rozmiar fragmentu wynoszący 2000 bajtów. Nie można określić tego elementu, `mode` gdy atrybut jest ustawiony na wartość "Custom".  
  
 Element jest reprezentowany <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> przez klasę. `<chunkedCookieHandler>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład służy do konfigurowania programu obsługi plików cookie fragmentarycznego, który zapisuje pliki cookie w fragmentach 3000 bajtów.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
