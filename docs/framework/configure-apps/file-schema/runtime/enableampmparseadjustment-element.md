---
title: <EnableAmPmParseAdjustment>, element
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a62bd3507c14e42798c903ae51edb0187e666c8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663765"
---
# <a name="enableampmparseadjustment-element"></a>\<EnableAmPmParseAdjustment, element >
Określa, czy metody analizowania dat i godzin używają dopasowanego zestawu reguł do analizowania ciągów dat zawierających dzień, miesiąc, godzinę i oznaczenie AM/PM.  
  
 \<> konfiguracji  
 \<runtime>  
\<EnableAmPmParseAdjustment >  
  
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
 `<EnableAmPmParseAdjustment>` Element kontroluje, jak następujące metody analizują ciąg daty, który zawiera numeryczny dzień i miesiąc, po którym następuje godzina i oznaczenie AM/PM (na przykład "4/10 6 AM"):  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Nie ma to znaczenia dla innych wzorców.  
  
 <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> Element nie ma wpływu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>na metody,, i. `<EnableAmPmParseAdjustment>`  
  
> [!IMPORTANT]
>  W przypadku platformy .NET Core i .NET Native dostosowane reguły analizowania AM/PM są domyślnie włączone.  
  
 Jeśli reguła dopasowania analizy nie jest włączona, Pierwsza cyfra ciągu jest interpretowana jako godzina zegara 12-godzinnego, a pozostała część ciągu z wyjątkiem oznaczenia AM/PM jest ignorowana. Data i godzina zwrócone przez metodę analizy składa się z bieżącej daty i godziny wyekstrahowanej z ciągu daty.  
  
 Jeśli reguła dopasowywania analizy jest włączona, metoda analizy interpretuje dzień i miesiąc jako należące do bieżącego roku i interpretuje czas jako godzinę zegara 12-godzinnego.  
  
 W poniższej tabeli <xref:System.DateTime> przedstawiono różnice w wartości, <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> gdy metoda jest używana do analizowania ciągu "" `<EnableAmPmParseAdjustment>` 4/10 6 am `enabled` "z właściwością elementu ustawioną na wartość" 0 "lub" 1 ". Przyjęto założenie, że dzisiejszą datą jest 5 stycznia 2017 i wyświetla datę tak, jakby była sformatowana przy użyciu ciągu formatu "G" określonego kultury.  
  
|Nazwa kultury|enabled="0"|enabled="1"|  
|------------------|------------------|------------------|  
|en-US|1/5/2017 4:00:00 AM|4/10/2017 6:00:00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Zobacz także

- [\<Element > środowiska uruchomieniowego](runtime-element.md)
- [\<> elementu konfiguracji](../configuration-element.md)
