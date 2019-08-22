---
title: <clear>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 51c669aff767948523172aa075677ad3fb6478a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664181"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a>\<Wyczyść element > dla schemeSettings (ustawienia identyfikatora URI)
Czyści wszystkie istniejące ustawienia schematu.  
  
 \<> konfiguracji  
\<> identyfikatora URI  
\<schemeSettings>  
\<clear>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<schemeSettings >, element (ustawienia identyfikatora URI)](schemesettings-element-uri-settings.md)|Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki. Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z <xref:System.Uri?displayProperty=nameWithType> tego powodu Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki. Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę, która czyści wszystkie ustawienia schematu, a następnie dodaje obsługę nieprawidłowych ograniczników Path (procentowo) dla schematu http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
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
