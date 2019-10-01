---
title: <idn>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698173"
---
# <a name="idn-element-uri-settings"></a>\<idn >, element (ustawienia identyfikatora URI)

Określa, czy do nazwy domeny jest stosowane analizowanie międzynarodowych nazw domen (IDN).
  
[ **@no__t — 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<idn >**  
  
## <a name="syntax"></a>Składnia  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  

|**Element**|**Opis**|  
|-----------------|---------------------|  
|`enabled`|Określa, czy do nazwy domeny jest stosowane analizowanie międzynarodowych nazw domen (IDN), wartość domyślna to None.|  

### <a name="child-elements"></a>Elementy podrzędne

Brak
  
### <a name="parent-elements"></a>Elementy nadrzędne

|**Element**|**Opis**|  
|-----------------|---------------------|  
|[adresu](uri-element-uri-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).|  

## <a name="remarks"></a>Uwagi

Istniejąca Klasa <xref:System.Uri> została rozszerzona w .NET Framework 3,5. 3,0 SP1 i 2,0 SP1 z obsługą międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN). Bieżąca użytkownicy nie będą widzieć żadnych zmian w zachowaniu .NET Framework 2,0, o ile nie włączą one obsługi IRI i IDN. Zapewnia to zgodność aplikacji z wcześniejszymi wersjami .NET Framework.

Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:

1. Dodaj następujący wiersz do pliku Machine. config w katalogu .NET Framework 2,0:
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Określ, czy do nazwy domeny mają być stosowane analizy międzynarodowej nazwy domeny (IDN) i czy mają być stosowane reguły analizy IRI. Tę czynność można wykonać w pliku Machine. config lub w oknie App. config.

 Istnieją trzy możliwe wartości IDN w zależności od używanych serwerów DNS:

- włączono IDN = wszystkie  

     Ta wartość spowoduje przekonwertowanie dowolnych nazw domen Unicode na ich odpowiedniki formacie Punycode (nazwy IDN).

- włączono IDN = AllExceptIntranet

     Ta wartość spowoduje przekonwertowanie wszystkich nazw domen Unicode, które nie są w lokalnym intranecie, aby użyć odpowiedników formacie Punycode (nazw IDN). W takim przypadku, aby obsługiwać nazwy międzynarodowe w lokalnym intranecie, serwery DNS, które są używane do sieci intranet, powinny obsługiwać rozpoznawanie nazw Unicode.

- włączono obsługę IDN = brak

     Ta wartość nie spowoduje konwersji nazw domen Unicode w celu użycia formacie Punycode. Jest to wartość domyślna, która jest zgodna z zachowaniem .NET Framework 2,0.

 Włączenie IDN spowoduje przekonwertowanie wszystkich etykiet Unicode w nazwie domeny na ich odpowiedniki formacie Punycode. Nazwy formacie Punycode zawierają tylko znaki ASCII i zawsze zaczynają się od Xn--prefix. Przyczyną tego problemu jest obsługa istniejących serwerów DNS w Internecie, ponieważ większość serwerów DNS obsługuje tylko znaki ASCII (patrz dokument RFC 3940).

### <a name="configuration-files"></a>Pliki konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi IRI analizy i nazw IDN:

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
