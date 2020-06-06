---
title: <uri>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697441"
---
# <a name="uri-element-uri-settings"></a>\<uri>, element (ustawienia identyfikatora URI)
Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
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
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[IDN](idn-element-uri-settings.md)|Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).|  
|[iriParsing](iriparsing-element-uri-settings.md)|Określa, czy ma zostać zastosowana Analiza IRI (International Resource Identifier) <xref:System.Uri> i czy mają być stosowane IRI reguły analizy.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[skonfigurować](../configuration-element.md)|Zawiera ustawienia dla wszystkich przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `uri`Element zawiera ustawienia dla elementów członkowskich <xref:System.Uri> klasy używanej przez klasy w <xref:System.Net> przestrzeni nazw. Ustawienia umożliwiają skonfigurowanie obsługi IRI i IDN.  
  
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
