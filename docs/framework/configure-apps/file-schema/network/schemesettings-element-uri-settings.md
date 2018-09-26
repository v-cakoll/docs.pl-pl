---
title: '&lt;schemeSettings&gt; — Element (ustawienia identyfikatora Uri)'
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 76ca5acc22eca07d372a2964cf3a6df4ea3b58d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077489"
---
# <a name="ltschemesettingsgt-element-uri-settings"></a>&lt;schemeSettings&gt; — Element (ustawienia identyfikatora Uri)
Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.  
  
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
|[Usuń zaznaczenie](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|Usuwa wszystkie istniejące ustawienia schematu.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|Usuwa ustawienie schematu dla nazwy schematu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Identyfikator URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un wyprowadza klasy zakodowane ograniczniki ścieżka przed wykonaniem kompresji ścieżki. Było to wdrożone jako mechanizm zabezpieczeń przed atakami, jak pokazano poniżej:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Jeśli ten identyfikator URI zostanie przekazany do modułów braku obsługi procent zakodowane znaków prawidłowo, może to spowodować następujące polecenie, które są wykonywane przez serwer:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tego powodu <xref:System.Uri?displayProperty=nameWithType> pierwszy ograniczniki ścieżki un wyprowadza klasy, a następnie stosuje kompresji ścieżki. Wynik przekazania złośliwy adres URL powyżej <xref:System.Uri?displayProperty=nameWithType> klasy Konstruktor skutkuje następujący identyfikator URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowany un ucieczki ograniczniki za pomocą opcji konfiguracji schemeSettings dla określonego schematu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy do obsługi nie anulowania zapewnianego element ścieżki zakodowane w formacie procent ograniczniki schemat http.  
  
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
|Plik walidacji||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
