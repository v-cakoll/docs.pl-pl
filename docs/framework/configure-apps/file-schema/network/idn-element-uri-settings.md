---
title: <idn>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 5fe2eafee702be96bfdca80a06af4a040d9ef0f6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664120"
---
# <a name="idn-element-uri-settings"></a>\<> IDN — element (ustawienia identyfikatora URI)
Określa, czy do nazwy domeny jest stosowane analizowanie międzynarodowych nazw domen (IDN).  
  
## <a name="schema-hierarchy"></a>Hierarchia schematu  
 [\<> elementu konfiguracji](../configuration-element.md)  
  
 [\<Identyfikator URI > element (ustawienia identyfikatora URI)](uri-element-uri-settings.md)  
  
 [\<> IDN](idn-element-uri-settings.md)  
  
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
|[uri](uri-element-uri-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Istniejąca <xref:System.Uri> Klasa została rozszerzona w .NET Framework 3,5. 3,0 SP1 i 2,0 SP1 z obsługą międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN). Bieżąca użytkownicy nie będą widzieć żadnych zmian w zachowaniu .NET Framework 2,0, o ile nie włączą one obsługi IRI i IDN. Zapewnia to zgodność aplikacji z wcześniejszymi wersjami .NET Framework.  
  
 Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:  
  
1. Dodaj następujący wiersz do pliku Machine. config w katalogu .NET Framework 2,0  
  
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
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi analizy IRI i nazw IDN.  
  
### <a name="code"></a>Kod  
  
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
