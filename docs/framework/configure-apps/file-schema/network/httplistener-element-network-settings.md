---
title: <httpListener>, element (ustawienia sieci)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: b3a6d527bc1bf8210bb85424fa218fda495a2a2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705080"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener >, Element (ustawienia sieci)
Dostosowuje parametrów używanych przez <xref:System.Net.HttpListener> klasy.  
  
 \<Konfiguracja >  
\<system.net>  
\<settings>  
\<httpListener>  
  
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
|unescapeRequestUrl|Wartość logiczna, która wskazuje, czy <xref:System.Net.HttpListener> wystąpienie używa pierwotne URI o niezmienionym znaczeniu zamiast przekonwertowanego identyfikatora URI.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 **UnescapeRequestUrl** atrybut wskazuje, jeśli <xref:System.Net.HttpListener> używa pierwotne URI o niezmienionym znaczeniu zamiast przekonwertowanego identyfikator URI, gdzie wszystkie zakodowane w formacie procent wartości są konwertowane i są podjąć inne kroki normalizacji.  
  
 Gdy <xref:System.Net.HttpListener> wystąpienia odbiera żądanie za pośrednictwem `http.sys` usługi, tworzy wystąpienie ciągu identyfikatora URI, dostarczone przez `http.sys`i uwidacznia go jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> właściwości.  
  
 `http.sys` Service udostępnia dwa ciągi identyfikatora URI żądania:  
  
- Identyfikator URI nieprzetworzone  
  
- Przekonwertowana identyfikatora URI  
  
 Nieprzetworzone identyfikator URI jest <xref:System.Uri?displayProperty=nameWithType> podane w wierszu żądania żądania HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Nieprzetworzone dostarczone przez identyfikator URI `http.sys` dla żądania, o których wspomniano powyżej, jest "/ path /". Reprezentuje ciąg po zlecenie HTTP, ponieważ została wysłana przez sieć.  
  
 `http.sys` Usługa tworzy przekonwertowanego identyfikatora URI z informacjami w żądaniu przy użyciu podanego w wierszu żądania HTTP identyfikatora URI i nagłówek hosta, aby określić serwer pochodzenia żądania powinien być przekazywany do. Odbywa się przez porównywanie informacji dotyczących z żądania z zestawem zarejestrowanych prefiksów identyfikatorów URI. W dokumentacji zestawu SDK serwera HTTP odwołuje się do tego przekonwertowanego identyfikatora URI jako struktury HTTP_COOKED_URL.  
  
 Aby można było porównać żądania przy użyciu zarejestrowanego prefiksów identyfikatorów URI, musi wykonać niektóre normalizacji na żądanie. W przykładzie powyżej przekonwertowanego identyfikator URI będzie następujący:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` Usługi łączy w sobie <xref:System.Uri.Host%2A?displayProperty=nameWithType> wartości właściwości, a ciąg w wierszu żądania do utworzenia przekonwertowanego identyfikatora URI. Ponadto `http.sys` i <xref:System.Uri?displayProperty=nameWithType> klasy również wykonuje następujące czynności:  
  
- ONZ anuluje wszystkie zakodowany wartość procentowa.  
  
- Konwertuje kodowany w formacie procent znaki spoza zestawu ASCII w reprezentacji znaków UTF-16. Należy pamiętać, że UTF-8 i ANSI/DBCS są obsługiwane znaki oraz znaki Unicode (kodowanie Unicode przy użyciu formatu uXXXX %).  
  
- Wykonuje inne czynności normalizacji, takie jak kompresja ścieżki.  
  
 Ponieważ żądanie nie zawiera żadnych informacji o kodowanie używane do zakodowane w formacie procent wartości, nie może być określić poprawne kodowanie przez analizowanie zakodowane w formacie procent wartości.  
  
 W związku z tym `http.sys` zawiera dwa klucze rejestru do modyfikowania procesu:  
  
|Klucz rejestru|Wartość domyślna|Opis|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Jeśli zero, `http.sys` akceptuje tylko adresy URL algorytmem UTF-8.<br /><br /> Jeśli różna od zera, `http.sys` akceptuje także kodowaniu ANSI lub zakodowane w formacie DBCS adresy URL w żądaniach.|  
|FavorUTF8|1|Jeśli różna od zera, `http.sys` zawsze próbuje dekodowanie adresu URL jako UTF-8 najpierw; Jeśli tej konwersji nie powiedzie się i EnableNonUTF8 jest różna od zera, sterownik Http.sys, a następnie próbuje go dekodować w kodowaniu ANSI lub znaków Dwubajtowych.<br /><br /> Jeśli zero i EnableNonUTF8 jest różna od zera, `http.sys` podejmuje próbę zdekodowania kodowaniu ANSI lub znaków Dwubajtowych; Jeśli to się nie powiedzie, podejmuje próby konwersji UTF-8.|  
  
 Gdy <xref:System.Net.HttpListener> odbiera żądanie, używa ona przekonwertowana identyfikatora URI z `http.sys` jako danych wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.  
  
 Istnieje potrzeba do obsługi znaki oprócz znaków i numery identyfikatorów URI. Przykładem jest następujący identyfikator URI, który służy do pobierania informacji klienta dla klientów number "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Należy pamiętać, ukośnika procent, kodowane w identyfikatorze Uri (% 2F). Jest to konieczne, ponieważ w tym przypadku reprezentuje znak ukośnika, danych i nie ogranicznika ścieżka.  
  
 Przekazywanie ciągu identyfikatora Uri konstruktora doprowadzi do następujący identyfikator URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Dzielenie ścieżkę na jej segmenty mogłoby spowodować następujące elementy:  
  
 `Customer('1`  
  
 `3812')`  
  
 Nie jest celem nadawca żądania.  
  
 Jeśli **unescapeRequestUrl** ma ustawioną wartość atrybutu **false**, a następnie po <xref:System.Net.HttpListener> odbiera żądanie, używa raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako dane wejściowe <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.  
  
 Wartością domyślną dla **unescapeRequestUrl** atrybut jest **true**.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Właściwość może służyć do uzyskania bieżącej wartości **unescapeRequestUrl** atrybut z właściwych plików konfiguracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net.HttpListener> klasy po odebraniu żądania do używania raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.  
  
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
|Plik walidacji||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
