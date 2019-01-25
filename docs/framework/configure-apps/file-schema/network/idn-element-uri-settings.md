---
title: '&lt;IDN&gt; — Element (ustawienia identyfikatora Uri)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 21950beeefb23e81066623534774148e1f5d92ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580746"
---
# <a name="ltidngt-element-uri-settings"></a>&lt;IDN&gt; — Element (ustawienia identyfikatora Uri)
Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazwy domeny.  
  
## <a name="schema-hierarchy"></a>Hierarchia schematu  
 [\<Konfiguracja > Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identyfikator URI >, Element (ustawienia identyfikatora Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
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
|`enabled`|Określa, czy analizy Zinternacjonalizowanych nazw domen (IDN) jest stosowany do nazwy domeny wartość domyślna to Brak.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Identyfikator URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Istniejące <xref:System.Uri> klasy został rozszerzony w .NET Framework 3.5. 3.0 z dodatkiem SP1 i 2.0 z dodatkiem SP1 z obsługą międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN). Bieżący użytkownicy nie będą widzieć wszelkie zmiany w zachowaniu .NET Framework 2.0, chyba że umożliwiają one specjalnie IRI i IDN pomocy technicznej. Dzięki temu zgodność aplikacji z wcześniejszych wersji programu .NET Framework.  
  
 Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:  
  
1.  Dodaj następujący wiersz do pliku machine.config w katalogu .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Określić, czy analizy Zinternacjonalizowanych nazw domen (IDN) stosowane do nazwy domeny i czy powinny być stosowane IRI podczas analizowania reguły. Można to zrobić w pliku machine.config lub w pliku app.config.  
  
 Istnieją trzy możliwe wartości IDN w zależności od serwerów DNS, które są używane:  
  
-   IDN, włączone = All  
  
     Ta wartość spowoduje przekonwertowanie wszystkie nazwy domen, Unicode na ich odpowiedniki Punycode (nazwy IDN).  
  
-   IDN, włączone = AllExceptIntranet  
  
     Ta wartość będzie przekonwertować wszystkie nazwy domeny Unicode nie w lokalnej sieci Intranet w celu użyj odpowiedników Punycode (nazwy IDN). W tym przypadku do obsługi międzynarodowe nazwy w lokalnym intranecie, serwerów DNS, które są używane dla dostępu z intranetu powinien obsługiwać rozpoznawanie nazw Unicode.  
  
-   IDN, włączone = None  
  
     Ta wartość nie zostanie przekonwertować wszystkie nazwy domen Unicode, aby użyć Punycode. Jest to wartość domyślna, która jest zgodna z zachowaniem .NET Framework 2.0.  
  
 Włączanie IDN, spowoduje przekonwertowanie wszystkich etykiet Unicode w nazwie domeny na ich odpowiedniki Punycode. Nazwy Punycode zawierać tylko znaki ASCII i zawsze rozpoczynają się prefiksem xn —. Przyczyną tego jest do obsługi istniejących serwerów DNS w Internecie, ponieważ większość serwery DNS obsługują tylko znaki ASCII (zobacz RFC 3940).  
  
### <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy w celu obsługi analizowania IRI i nazwy IDN.  
  
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
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
