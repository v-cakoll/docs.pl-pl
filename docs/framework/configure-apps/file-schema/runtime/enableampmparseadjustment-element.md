---
title: <EnableAmPmParseAdjustment> Element
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 8920e51fcaaca5cb78b80a99ea321163c9b5240f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117371"
---
# <a name="enableampmparseadjustment-element"></a>\<element > EnableAmPmParseAdjustment
Określa, czy metody analizowania dat i godzin używają dopasowanego zestawu reguł do analizowania ciągów dat zawierających dzień, miesiąc, godzinę i oznaczenie AM/PM.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<EnableAmPmParseAdjustment >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy metody analizowania dat i godzin używają skorygowanego zestawu reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.|  
  
### <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Metody analizowania dat i godzin nie używają skorygowanych reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.|  
|1|Metody analizowania dat i godzin używają skorygowanych reguł do analizowania ciągów dat, które zawierają tylko oznaczenie Day, month, Hour i AM/PM.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<EnableAmPmParseAdjustment>` kontroluje, jak następujące metody analizują ciąg daty, który zawiera numeryczny dzień i miesiąc, po którym następuje godzina i oznaczenie AM/PM (na przykład "4/10 6 AM"):  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Nie ma to znaczenia dla innych wzorców.  
  
 Element `<EnableAmPmParseAdjustment>` nie ma wpływu na metody <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> W przypadku platformy .NET Core i .NET Native dostosowane reguły analizowania AM/PM są domyślnie włączone.  
  
 Jeśli reguła dopasowania analizy nie jest włączona, Pierwsza cyfra ciągu jest interpretowana jako godzina zegara 12-godzinnego, a pozostała część ciągu z wyjątkiem oznaczenia AM/PM jest ignorowana. Data i godzina zwrócone przez metodę analizy składa się z bieżącej daty i godziny wyekstrahowanej z ciągu daty.  
  
 Jeśli reguła dopasowywania analizy jest włączona, metoda analizy interpretuje dzień i miesiąc jako należące do bieżącego roku i interpretuje czas jako godzinę zegara 12-godzinnego.  
  
 W poniższej tabeli przedstawiono różnicę wartości <xref:System.DateTime>, gdy metoda <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> jest używana do analizowania ciągu "" 4/10 6 AM "z właściwością `enabled` elementu `<EnableAmPmParseAdjustment>` ustawioną na wartość" 0 "lub" 1 ". Przyjęto założenie, że dzisiejszą datą jest 5 stycznia 2017 i wyświetla datę tak, jakby była sformatowana przy użyciu ciągu formatu "G" określonego kultury.  
  
|Nazwa kultury|włączone = "0"|włączone = "1"|  
|------------------|------------------|------------------|  
|pl-US|1/5/2017 4:00:00 AM|4/10/2017 6:00:00 AM|  
|pl GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Zobacz także

- [Element > środowiska uruchomieniowego \<](runtime-element.md)
- [\<> elementu konfiguracji](../configuration-element.md)
