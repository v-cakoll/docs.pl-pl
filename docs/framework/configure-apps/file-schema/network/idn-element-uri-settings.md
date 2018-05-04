---
title: '&lt;IDN&gt; elementu (ustawienia identyfikatorów Uri)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17f68fbb92797928be911e530232e8638793687f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltidngt-element-uri-settings"></a>&lt;IDN&gt; elementu (ustawienia identyfikatorów Uri)
Określa, czy podczas analizowania międzynarodowych nazw domen (IDN) została zastosowana do nazwy domeny.  
  
## <a name="schema-hierarchy"></a>Schemat hierarchii  
 [\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identyfikator URI > elementu (ustawienia identyfikatorów Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<IDN >](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
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
|`enabled`|Określa, czy podczas analizowania międzynarodowych nazw domen (IDN) jest stosowana do nazwy domeny wartością domyślną jest Brak.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Identyfikator URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Zawiera ustawienia, które określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Istniejące <xref:System.Uri> klasy został rozszerzony w programie .NET Framework 3.5. 3.0 z dodatkiem SP1, a 2.0 z dodatkiem SP1 z obsługą międzynarodowej identyfikatory zasobów (IRI) oraz międzynarodowych nazw domen (IDN). Bieżący użytkownicy nie będą widzieli zmiany z zachowaniem .NET Framework 2.0, o ile nie są jawnie włączyć IRI i IDN obsługuje. Dzięki temu zgodność aplikacji we wcześniejszych wersjach programu .NET Framework.  
  
 Aby włączyć obsługę IRI, wymagane są następujące zmiany dwóch:  
  
1.  Dodaj następujący wiersz w pliku machine.config w katalogu .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Określ, czy mają być stosowane podczas analizowania międzynarodowych nazw domen (IDN) na nazwę domeny i czy powinny być stosowane IRI podczas analizowania reguły. Można to zrobić w pliku machine.config lub w pliku app.config.  
  
 Istnieją trzy możliwe wartości IDN w zależności od serwerów DNS, które są używane:  
  
-   IDN włączone = All  
  
     Ta wartość przekonwertuje wszystkie nazwy domen Unicode odpowiedniki Punycode (nazwy IDN).  
  
-   IDN włączone = AllExceptIntranet  
  
     Ta wartość przekonwertuje wszystkie nazwy domen Unicode nie w lokalnym intranecie używania odpowiedniki Punycode (nazwy IDN). W takim przypadku do obsługi międzynarodowe nazwy w lokalnym intranecie, serwery DNS, które będą używane dla dostępu z intranetu powinien obsługiwać rozpoznawania nazw Unicode.  
  
-   IDN włączone = Brak  
  
     Ta wartość nie przekonwertuje wszystkie nazwy domen Unicode do użycia Punycode. Jest to wartość domyślna, zgodnie z zachowania programu .NET Framework 2.0.  
  
 Włączanie IDN przekonwertuje wszystkich etykiet Unicode w domenie o nazwie odpowiedniki ciąg Punycode. Ciąg Punycode nazwy zawierają tylko znaki ASCII i zawsze rozpoczyna się od prefiksu xn--. Przyczyną tego jest do obsługi istniejących serwerów DNS w Internecie, ponieważ większość serwery DNS obsługują tylko znaki ASCII (zobacz dokument RFC 3940).  
  
### <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi analizowania IRI i nazwy IDN.  
  
### <a name="code"></a>Kod  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
