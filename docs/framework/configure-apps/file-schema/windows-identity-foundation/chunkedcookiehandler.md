---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 1726d4ade9405543bdfdb4e4803f87f258de791e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691284"
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Ten element może być tylko obecne Jeśli `mode` atrybutu `<cookieHandler>` element to "Default" lub "Fragmentaryczne".  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
\<chunkedCookieHandler>  
  
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
|chunkSize|Maksymalny rozmiar w znakach dane pliku cookie HTTP dla dowolnego jednego pliku cookie HTTP. Należy zachować ostrożność podczas dostosowywania rozmiaru fragmentu. Przeglądarki sieci Web mają różne limity dotyczące rozmiaru plików cookie i liczbę dozwolonych w każdej domenie. Na przykład pierwotną specyfikację Netscape określone limity: Łączna liczba plików cookie 300, 4096 bajtów na nagłówek cookie (w tym metadane i nie tylko wartości pliku cookie) i 20 plików cookie dla domeny. Wartość domyślna to 2000. Wymagana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) używa na odczytywanie i zapisywanie plików cookie.|  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu <xref:System.IdentityModel.Services.ChunkedCookieHandler> , ustawiając `mode` atrybutu `<cookieHandler>` element "Default" lub "Fragmentaryczne", można określić rozmiar fragmentu, używającej obsługi plików cookie na odczytywanie i zapisywanie plików cookie, umieszczając `<chunkedCookieHandler>` element podrzędny i ustawienie jego `chunkSize` atrybutu. Jeśli `<chunkedCookieHandler>` element nie jest obecny, jest używany domyślny rozmiar fragmentu 2000 bajtów. Ten element nie może być określony, gdy `mode` atrybut jest ustawiony na "Niestandardowe".  
  
 `<chunkedCookieHandler>` Element jest reprezentowany przez <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia skonfigurowanie plik cookie z podziałem program obsługi, który zapisuje pliki cookie we fragmentach 3000 bajtów.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
