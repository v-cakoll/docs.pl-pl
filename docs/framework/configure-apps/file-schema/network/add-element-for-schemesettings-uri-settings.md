---
title: <add>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087718"
---
# <a name="add-element-for-schemesettings-uri-settings"></a>\<add>, element dla schemeSettings (ustawienia identyfikatora URI)
Dodaje ustawienie schematu dla nazwy schematu.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Składnia  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|name|Nazwa schematu, dla którego jest stosowane to ustawienie. Jedyne obsługiwane wartości to Name = "http" i Name = "https".|  
  
## <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Przypisane  
  
|Wartość|Opis|  
|-----------|-----------------|  
|genericUriParserOptions|Opcje parsera dla tego schematu. Jedyna obsługiwana wartość to genericUriParserOptions = "DontUnescapePathDotsAndSlashes".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<schemeSettings>— Element (ustawienia identyfikatora URI)](schemesettings-element-uri-settings.md)|Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki. Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tego powodu <xref:System.Uri?displayProperty=nameWithType> Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki. Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
