---
title: "&lt;Dodaj&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8ce4cc33d054e74fc9868a16764e744daf260c10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a>&lt;Dodaj&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)
Dodaje ustawienia schematu dla nazwy schematu.  
  
 \<Konfiguracja >  
\<Identyfikator URI >  
\<schemeSettings >  
\<Dodaj >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Nazwa schematu, którego dotyczy to ustawienie. Obsługiwane są tylko wartości name = "http" i nazwie = "https".|  
  
## <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|genericUriParserOptions|Opcji analizatora składni dla tego schematu. Jedyna obsługiwana wartość to genericUriParserOptions = "DontUnescapePathDotsAndSlashes".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<schemeSettings > elementu (ustawienia identyfikatorów Uri)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.|  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
