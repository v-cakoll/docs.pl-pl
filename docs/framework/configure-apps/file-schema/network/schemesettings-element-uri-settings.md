---
title: '&lt;schemeSettings&gt; elementu (ustawienia identyfikatorów Uri)'
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 40ff62a48a3ba1f4a9b5aed28630ab70d37869fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742682"
---
# <a name="ltschemesettingsgt-element-uri-settings"></a>&lt;schemeSettings&gt; elementu (ustawienia identyfikatorów Uri)
Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.  
  
 \<Konfiguracja >  
\<Identyfikator URI >  
\<schemeSettings >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|Dodaje ustawienia schematu dla nazwy schematu.|  
|[Wyczyść](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|Usuwa wszystkie istniejące ustawienia schematu.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|Usuwa ustawienie schematu dla nazwy schematu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Identyfikator URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Zawiera ustawienia, które określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un specjalne klasy zakodowane ogranicznik ścieżki przed wykonaniem kompresji ścieżki. To zostało zaimplementowane jako mechanizm zabezpieczenia przed atakami podobne do poniższych:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Jeśli ten identyfikator URI jest przekazywane do modułów nie obsługuje procent zakodowane znaków prawidłowo, może spowodować następujące polecenie, które było wykonywane przez serwer:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasy pierwszy ogranicznik ścieżki un specjalne, a następnie stosuje kompresji ścieżki. Wynik przekazywanie złośliwego adres URL powyżej, aby <xref:System.Uri?displayProperty=nameWithType> klasy konstruktora powoduje następujący identyfikator URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowanego un ucieczki ograniczniki przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi nie anulowanie procent, kodowane ścieżki ograniczniki schemat http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||
|-|-|  
|Przestrzeń nazw|System|  
|Nazwa schematu||  
|Sprawdzanie poprawności pliku||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
