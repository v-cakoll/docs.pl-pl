---
title: <iriParsing>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698094"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing>, element (ustawienia identyfikatora URI)
Określa, czy do <xref:System.Uri> i czy należy zastosować analizę IRI (International Resource Identifier).  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|`enabled`|Określa, czy jest włączone analizowanie IRI. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[adresu](uri-element-uri-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).|  
  
## <a name="remarks"></a>Uwagi  
 Istniejąca <xref:System.Uri> Klasa została rozszerzona w .NET Framework 3,5. 3,0 SP1 i 2,0 SP1, aby zapewnić obsługę międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN). Bieżąca użytkownicy nie będą widzieć żadnych zmian w zachowaniu .NET Framework 2,0, o ile nie włączą one obsługi IRI i IDN. Zapewnia to zgodność aplikacji z wcześniejszymi wersjami .NET Framework.  
  
 Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:  
  
1. Dodaj następujący wiersz do pliku Machine. config w katalogu .NET Framework 2,0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Określ, czy mają być stosowane reguły analizy IRI. Tę czynność można wykonać w pliku Machine. config lub w oknie App. config.  
  
 Włączenie analizy IRI (iriParsing Enabled = `true` ) umożliwi normalizację i sprawdzanie znaków zgodnie z najnowszymi regułami IRI w dokumencie RFC 3987. Wartość domyślna to `false` i umożliwia normalizację i sprawdzanie znaków zgodnie ze standardami rfc 2396 i rfc 3986 (dla literałów IPv6).  
  
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

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
