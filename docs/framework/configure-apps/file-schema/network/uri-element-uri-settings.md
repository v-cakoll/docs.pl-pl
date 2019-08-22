---
title: <Uri>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663965"
---
# <a name="uri-element-uri-settings"></a>\<Identyfikator URI > element (ustawienia identyfikatora URI)
Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).  
  
## <a name="schema-hierarchy"></a>Hierarchia schematu  
 [\<> elementu konfiguracji](../configuration-element.md)  
  
 [\<> identyfikatora URI](uri-element-uri-settings.md)  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[IDN](idn-element-uri-settings.md)|Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).|  
|[iriParsing](iriparsing-element-uri-settings.md)|Określa <xref:System.Uri> , czy ma zostać zastosowana Analiza IRI (International Resource Identifier) i czy mają być stosowane IRI reguły analizy.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[skonfigurować](../configuration-element.md)|Zawiera ustawienia dla wszystkich przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Element zawiera ustawienia dla elementów członkowskich <xref:System.Uri> klasy <xref:System.Net> używanej przez klasy w przestrzeni nazw. `uri` Ustawienia umożliwiają skonfigurowanie obsługi IRI i IDN.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi analizy IRI i nazw IDN. W przykładzie zostanie również wyczyszczone wszystkie ustawienia schematu, a następnie dodano obsługę ograniczników ścieżek o wartości procentowo zakodowanych w schemacie protokołu HTTP.  
  
### <a name="code"></a>Kod  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień sieci](index.md)
