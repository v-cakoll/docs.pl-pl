---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c5d526ccd48ea5e822d5d29fb38dacd895c2556c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Ten element może być tylko obecny Jeśli `mode` atrybutu `<cookieHandler>` jest element "Default" lub "Fragmentaryczne".  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
\<chunkedCookieHandler >  
  
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
|niż rozmiar segmentu|Maksymalny rozmiar w znakach dane pliku cookie HTTP dla dowolnego jednego pliku cookie HTTP. Należy zachować ostrożność podczas dostosowywania rozmiar fragmentu. Przeglądarki sieci Web mają różne limity rozmiaru plików cookie i liczbę dozwolonych dla jednej domeny. Na przykład pierwotnej specyfikacji Netscape określone te limity: łączna liczba 300 plików cookie, 4096 bajtów na nagłówek cookie (w tym metadane, nie tylko wartości pliku cookie) i 20 plików cookie dla domeny. Wartość domyślna to 2000. Wymagany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> który <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) używany do odczytywania i zapisywania plików cookie.|  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu <xref:System.IdentityModel.Services.ChunkedCookieHandler> przez ustawienie `mode` atrybutu `<cookieHandler>` element "Default" lub "Fragmentaryczne", można określić rozmiar fragmentu, używaną do odczytu i zapisu plików cookie przez dołączenie obsługi plików cookie `<chunkedCookieHandler>` element podrzędny i ustawienie jej `chunkSize` atrybutu. Jeśli `<chunkedCookieHandler>` element nie jest obecny, jest używany domyślny rozmiar fragmentu 2000 bajtów. Ten element nie może być określona gdy `mode` atrybut jest ustawiony na "Custom".  
  
 `<chunkedCookieHandler>` Reprezentowany przez element <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład służy do konfigurowania obsługi podzielony plik cookie, który zapisuje pliki cookie w fragmentów 3000 bajtów.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
