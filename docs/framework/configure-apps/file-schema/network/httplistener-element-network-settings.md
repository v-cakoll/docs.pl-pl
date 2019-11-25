---
title: <httpListener>, element (ustawienia sieci)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088376"
---
# <a name="httplistener-element-network-settings"></a>\<element > odbiornika HttpListener (Ustawienia sieci)
Dostosowuje parametry używane przez klasę <xref:System.Net.HttpListener>.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](settings-element-network-settings.md) >
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odbiornika httplistener >**

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
|unescapeRequestUrl|Wartość logiczna wskazująca, czy wystąpienie <xref:System.Net.HttpListener> używa nieprzetworzonego niezmienionego identyfikatora URI zamiast przekonwertowanego identyfikatora URI.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.|  
  
## <a name="remarks"></a>Uwagi  
 Atrybut **unescapeRequestUrl** wskazuje, czy <xref:System.Net.HttpListener> używa nieprzetworzonego niezmienionego identyfikatora URI zamiast przekonwertowanego identyfikatora URI, gdzie wszystkie wartości kodowane w procentach są konwertowane i są wykonywane inne czynności normalizacji.  
  
 Gdy wystąpienie <xref:System.Net.HttpListener> odbiera żądanie za pomocą usługi `http.sys`, tworzy wystąpienie ciągu identyfikatora URI dostarczone przez `http.sys`i uwidacznia je jako właściwość <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.  
  
 Usługa `http.sys` udostępnia dwa ciągi identyfikatorów URI żądania:  
  
- Nieprzetworzony identyfikator URI  
  
- Przekonwertowany identyfikator URI  
  
 Nieprzetworzony identyfikator URI jest <xref:System.Uri?displayProperty=nameWithType> podany w wierszu żądania żądania HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Nieprzetworzony identyfikator URI podany w `http.sys` dla żądania wymienionego powyżej ma wartość "/Path/". Reprezentuje ciąg następujący po zleceniu HTTP, który został wysłany przez sieć.  
  
 Usługa `http.sys` tworzy przekonwertowany identyfikator URI z informacji znajdujących się w żądaniu przy użyciu identyfikatora URI podanego w wierszu żądania HTTP i nagłówka hosta w celu określenia serwera pochodzenia, do którego zostanie przesłane żądanie. W tym celu należy porównać informacje z żądania z zestawem zarejestrowanych prefiksów URI. Dokumentacja zestawu SDK serwera HTTP dotyczy tego przekonwertowanego identyfikatora URI jako struktury HTTP_COOKED_URL.  
  
 Aby można było porównać żądanie z zarejestrowanymi prefiksami URI, należy wykonać pewne normalizacji żądania. W przypadku przykładu powyżej przekonwertowanego identyfikatora URI można wykonać następujące czynności:  
  
 `http://www.contoso.com/path/`  
  
 Usługa `http.sys` łączy wartość właściwości <xref:System.Uri.Host%2A?displayProperty=nameWithType> i ciąg w wierszu żądania w celu utworzenia przekonwertowanego identyfikatora URI. Ponadto `http.sys`, a Klasa <xref:System.Uri?displayProperty=nameWithType> wykonuje również następujące czynności:  
  
- Cofa wszystkie wartości zakodowane procentowo.  
  
- Konwertuje znaki nienależące do zestawu znaków ASCII, które nie są zakodowane w formacie UTF-16. Należy zauważyć, że znaki UTF-8 i ANSI/DBCS są obsługiwane, a także znaki Unicode (kodowanie Unicode przy użyciu formatu% uXXXX).  
  
- Wykonuje inne kroki normalizacji, takie jak kompresja ścieżki.  
  
 Ponieważ żądanie nie zawiera żadnych informacji o kodowaniu używanym dla wartości zakodowanych w procentach, może nie być możliwe określenie poprawnego kodowania tylko przez analizowanie wartości zakodowanych w procentach.  
  
 W związku z tym `http.sys` zapewnia dwa klucze rejestru do modyfikacji procesu:  
  
|Klucz rejestru|Wartość domyślna|Opis|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Jeśli wartość jest równa zero, `http.sys` akceptuje tylko adresy URL zakodowane w formacie UTF-8.<br /><br /> Jeśli wartość jest różna od zera, `http.sys` również akceptuje adresy URL kodowane w formacie ANSI lub DBCS w żądaniach.|  
|FavorUTF8|1|Jeśli wartość jest różna od zera, `http.sys` zawsze próbuje zdekodować adres URL jako pierwszy w formacie UTF-8; Jeśli konwersja nie powiedzie się, a EnableNonUTF8 jest różna od zera, http. sys próbuje zdekodować ją jako ANSI lub DBCS.<br /><br /> Jeśli zero (i EnableNonUTF8 jest różna od zera), `http.sys` próbuje zdekodować ją jako ANSI lub DBCS; Jeśli to się nie powiedzie, próbuje konwersję UTF-8.|  
  
 Gdy <xref:System.Net.HttpListener> odbiera żądanie, używa przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych właściwości <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 Istnieje potrzeba obsługi znaków oprócz znaków i cyfr w identyfikatorach URI. Przykładem jest następujący identyfikator URI, który służy do pobierania informacji o kliencie dla numeru klienta "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Zwróć uwagę na ukośnik zakodowany procentowo w identyfikatorze URI (% 2F). Jest to konieczne, ponieważ w tym przypadku znak ukośnika reprezentuje dane, a nie ogranicznik ścieżki.  
  
 Przekazywanie ciągu do konstruktora identyfikatora URI będzie prowadzić do następującego identyfikatora URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Podział ścieżki na segmenty spowoduje następujące elementy:  
  
 `Customer('1`  
  
 `3812')`  
  
 Nie jest to cel nadawcy żądania.  
  
 Jeśli atrybut **unescapeRequestUrl** ma wartość **false**, wtedy, gdy <xref:System.Net.HttpListener> odbiera żądanie, używa nieprzetworzonego identyfikatora URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych właściwości <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 Wartość domyślna atrybutu **unescapeRequestUrl** ma wartość **true**.  
  
 Właściwość <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> może służyć do uzyskiwania bieżącej wartości atrybutu **unescapeRequestUrl** z odpowiednich plików konfiguracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konfigurowania klasy <xref:System.Net.HttpListener> po odebraniu żądania użycia nieprzetworzonego identyfikatora URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych właściwości <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
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
|Może być puste||  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Schemat ustawień sieci](index.md)
