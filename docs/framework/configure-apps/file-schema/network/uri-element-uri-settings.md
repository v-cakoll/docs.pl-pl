---
title: <uri>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697441"
---
# <a name="uri-element-uri-settings"></a>\<uri >, element (ustawienia identyfikatora URI)
Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).  
  
[ **@no__t — 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1 **\<uri >**  
  
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
|[iriParsing](iriparsing-element-uri-settings.md)|Określa, czy do <xref:System.Uri> ma być stosowana analiza międzynarodowego identyfikatora zasobów (IRI) i czy mają być stosowane reguły analizy IRI.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|Określa sposób, w jaki <xref:System.Uri> będzie analizowana dla określonych schematów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[skonfigurować](../configuration-element.md)|Zawiera ustawienia dla wszystkich przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Element `uri` zawiera ustawienia dla elementów członkowskich klasy <xref:System.Uri> używane przez klasy w przestrzeni nazw <xref:System.Net>. Ustawienia umożliwiają skonfigurowanie obsługi IRI i IDN.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi IRI analizy nazw i IDN. W przykładzie zostanie również wyczyszczone wszystkie ustawienia schematu, a następnie dodano obsługę ograniczników ścieżek o wartości procentowo zakodowanych w schemacie protokołu HTTP.  
  
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
