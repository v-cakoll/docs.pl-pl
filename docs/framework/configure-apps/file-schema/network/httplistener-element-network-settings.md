---
title: '&lt;httpListener&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d880583016e6ccc0ae57fea10c35cb32726c93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt; elementu (ustawienia sieciowe)
Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasy.  
  
 \<Konfiguracja >  
\<System.NET >  
\<Ustawienia >  
\<httpListener >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Typ  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|unescapeRequestUrl|Wartość logiczna, która wskazuje, czy <xref:System.Net.HttpListener> wystąpienie korzysta raw URI niezmienionym znaczeniu zamiast przekonwertowanego identyfikatora URI.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 **UnescapeRequestUrl** atrybut wskazuje, czy <xref:System.Net.HttpListener> używa raw URI niezmienionym znaczeniu zamiast przekonwertowanego identyfikatora URI, gdzie wartości procent, kodowane są konwertowane, i są pobierane z procedurą normalizacji.  
  
 Gdy <xref:System.Net.HttpListener> wystąpienia odbiera żądanie za pośrednictwem `http.sys` usługi, tworzy wystąpienie ciągu identyfikatora URI dostarczonych przez `http.sys`i uwidacznia go jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> właściwości.  
  
 `http.sys` Usługi udostępnia dwa ciągi identyfikatora URI żądania:  
  
-   Nieprzetworzona identyfikatora URI.  
  
-   Przekonwertowana identyfikatora URI.  
  
 Nieprzetworzona identyfikator URI jest <xref:System.Uri?displayProperty=nameWithType> dostępne w wierszu żądania HTTP żądania:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Nieprzetworzone udostępniane przez identyfikator URI `http.sys` dla żądania wymienionych powyżej, jest "/ path /". Reprezentuje ciąg następujący zlecenie HTTP, jak została wysłana przez sieć.  
  
 `http.sys` Usługi tworzy przekonwertowanego identyfikatora URI na podstawie informacji dostępnych w żądaniu za pomocą identyfikatora URI, dostępne w wierszu żądania HTTP i powinny zostać przekazane nagłówek hosta, aby określić serwer pochodzenia żądania. Jest to realizowane przez porównanie informacji z żądania z zestawem zarejestrowanych prefiksów identyfikatorów URI. W dokumentacji zestawu SDK serwera HTTP odwołuje się do tego przekonwertowanego identyfikatora URI jako struktura HTTP_COOKED_URL.  
  
 Aby można było porównać żądanie z zarejestrowanych prefiksów identyfikatorów URI, należy jednak wykonać niektóre normalizacji na żądanie. Dla przykładu powyżej przekonwertowanego identyfikator URI będzie w następujący sposób:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` Usługi łączy <xref:System.Uri.Host%2A?displayProperty=nameWithType> wartość właściwości i ciąg w wierszu żądania do utworzenia przekonwertowanego identyfikatora URI. Ponadto `http.sys` i <xref:System.Uri?displayProperty=nameWithType> klasy również wykonuje następujące czynności:  
  
-   Wyrejestruj specjalne procent wszystkich wartości zakodowany.  
  
-   Konwertuje procent, kodowane znaki spoza zestawu ASCII w reprezentacji znaków UTF-16. Należy pamiętać, że oraz znaków Unicode (kodowanie Unicode w formacie % uXXXX) są obsługiwane znaki UTF-8 i ANSI/zestawów znaków Dwubajtowych.  
  
-   Wykonuje inne czynności normalizacji, takie jak ścieżka kompresji.  
  
 Ponieważ żądanie nie zawiera żadnych informacji o kodowanie używane z algorytmem procent wartości, nie może być określić poprawne kodowanie właśnie, analizując kodowany w formacie procent wartości.  
  
 W związku z tym `http.sys` zawiera dwa klucze rejestru do modyfikowania proces:  
  
|Klucz rejestru|Wartość domyślna|Opis|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Jeśli zero, `http.sys` akceptuje tylko adresy URL algorytmem UTF-8.<br /><br /> Jeśli niezerową, `http.sys` również akceptuje kodowaniu ANSI lub kodowany w formacie DBCS adresów URL w żądaniach.|  
|FavorUTF8|1|Jeśli niezerową, `http.sys` zawsze próbuje dekodowanie adresu URL jako UTF-8 najpierw; Jeśli tej konwersji nie powiedzie się i EnableNonUTF8 jest różna od zera, sterownik Http.sys, a następnie próbuje zdekodować kodowaniu ANSI lub zestawów znaków Dwubajtowych.<br /><br /> Jeśli zero (i EnableNonUTF8 jest różna od zera) `http.sys` podejmuje próbę zdekodowania kodowaniu ANSI lub DBCS; Jeśli się nie powiedzie, próby konwersji UTF-8.|  
  
 Gdy <xref:System.Net.HttpListener> odbiera żądanie, używa przekonwertowanego identyfikatora URI z `http.sys` jako wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.  
  
 Istnieje potrzeba do obsługi znaki oprócz znaków i liczb w identyfikatorów URI. Przykładem jest następujący identyfikator URI, który służy do pobierania informacji klienta dla klienta numer "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Należy zwrócić uwagę ukośnika procent, kodowane w identyfikatorze Uri (% 2F). Jest to konieczne, ponieważ w takim przypadku znaku ukośnika reprezentuje danych i nie ogranicznik ścieżki.  
  
 Przekazywanie ciągu identyfikatora Uri konstruktora doprowadzi do następującego identyfikatora URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Dzielenie na jego segmenty ścieżki spowoduje następujące elementy:  
  
 `Customer('1`  
  
 `3812')`  
  
 To nie jest celem nadawca żądania.  
  
 Jeśli **unescapeRequestUrl** atrybut ma ustawioną **false**, a następnie po <xref:System.Net.HttpListener> odbiera żądanie, używa raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako dane wejściowe <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.  
  
 Wartość domyślna dla **unescapeRequestUrl** atrybutu **true**.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Właściwości można pobrać wartości bieżącego **unescapeRequestUrl** atrybutu z plików zastosowania konfiguracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net.HttpListener> klasy, gdy odbiera żądanie użycia raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||
|-|-|  
|Przestrzeń nazw|System.Net|  
|Nazwa schematu||  
|Sprawdzanie poprawności pliku||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
