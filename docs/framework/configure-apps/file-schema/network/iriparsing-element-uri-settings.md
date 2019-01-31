---
title: <iriParsing> — Element (Ustawienia identyfikatora Uri)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: a4d4df8c214efb955f8f9d6678aaf8d56de71ebc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256660"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing >, Element (ustawienia identyfikatora Uri)
Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.  
  
## <a name="schema-hierarchy"></a>Hierarchia schematu  
 [\<Konfiguracja > Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identyfikator URI >, Element (ustawienia identyfikatora Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing >](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|`enabled`|Określa, czy analiza kodu IRI jest włączone. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Identyfikator URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Istniejące <xref:System.Uri> klasy został rozszerzony w .NET Framework 3.5. 3.0 z dodatkiem SP1 i 2.0 z dodatkiem SP1, aby zapewnić obsługę międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN). Bieżący użytkownicy nie będą widzieć wszelkie zmiany w zachowaniu .NET Framework 2.0, chyba że umożliwiają one specjalnie IRI i IDN pomocy technicznej. Dzięki temu zgodność aplikacji z wcześniejszych wersji programu .NET Framework.  
  
 Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:  
  
1.  Dodaj następujący wiersz do pliku machine.config w katalogu .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Określ, czy powinny być stosowane IRI podczas analizowania reguły. Można to zrobić w pliku machine.config lub w pliku app.config.  
  
 Włączanie analizy IRI (iriParsing włączone = `true`) będziesz robić normalizacji i znak sprawdzanie zgodnie z IRI najnowsze reguły w dokumencie RFC 3987. Wartość domyślna to `false` będzie czy normalizacji i znak sprawdzanie zgodnie z RFC 2396 i ze standardem RFC 3986 (dla literałów IPv6).  
  
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
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
