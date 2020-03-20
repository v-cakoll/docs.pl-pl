---
title: <schemeSettings>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154650"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeSettings> Element (Ustawienia Uri)
Określa sposób <xref:System.Uri> analizacji dla określonych schematów.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<systemyRozstawy>**  
  
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
|[Dodaj](add-element-for-schemesettings-uri-settings.md)|Dodaje ustawienie schematu dla nazwy schematu.|  
|[Wyczyść](clear-element-for-schemesettings-uri-settings.md)|Czyści wszystkie istniejące ustawienia schematu.|  
|[Usunąć](remove-element-for-schemesettings-uri-settings.md)|Usuwa ustawienie schematu dla nazwy schematu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Identyfikator uri](uri-element-uri-settings.md)|Zawiera ustawienia określające sposób obsługi adresów internetowych .NET Framework wyrażonych przy użyciu jednolitych identyfikatorów zasobów (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Uri?displayProperty=nameWithType> klasa un-escapes procent zakodowane ograniczniki ścieżki przed wykonaniem kompresji ścieżki. Zostało to zaimplementowane jako mechanizm zabezpieczeń przed atakami, takimi jak następujące:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Jeśli ten identyfikator URI zostanie przekazany do modułów, które nie obsługują poprawnie procentowych znaków zakodowanych, może to spowodować wykonanie następującego polecenia przez serwer:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tego <xref:System.Uri?displayProperty=nameWithType> powodu klasa najpierw un-escapes ograniczniki ścieżki, a następnie stosuje kompresję ścieżki. Wynik przekazania złośliwego adresu <xref:System.Uri?displayProperty=nameWithType> URL powyżej do konstruktora klasy powoduje następujące identyfikatory URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 To domyślne zachowanie można zmodyfikować tak, aby nie odkodowywało procentów przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia konfigurację <xref:System.Uri> używaną przez klasę do obsługi nie uciekających ograniczników ścieżki zakodowanych w procentach dla schematu http.  
  
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
|Plik sprawdzania poprawności||  
|Może być pusty||  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
