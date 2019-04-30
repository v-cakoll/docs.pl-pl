---
title: <EnableAmPmParseAdjustment>, element
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d1a14199debbb90827c1ea95347d485a636329
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704846"
---
# <a name="enableampmparseadjustment-element"></a>\<EnableAmPmParseAdjustment> Element
Określa, czy data i godzina metod analizowania użyć skorygowany zbiór reguł do analizowania ciągów daty, które zawierają dzień, miesiąc, godzinę i oznaczenie AM/PM.  
  
 \<Konfiguracja >  
 \<runtime>  
\<EnableAmPmParseAdjustment>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy data i godzina metod analizowania użyć skorygowany zbiór reguł do analizowania ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.|  
  
### <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Data i godzina metod analizowania reguły nie są używane skorygowany do analizowania ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.|  
|1|Data i godzina metod analizowania na użytek reguły skorygowany analizowanie ciągów daty, które zawierają tylko dnia, miesiąca, godzinę i oznaczenie AM/PM.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 `<EnableAmPmParseAdjustment>` Element kontroluje sposób przeanalizować ciąg daty, która zawiera liczbową wartość dnia i miesiąca, a następnie godzinę i oznaczenie AM/PM (na przykład "6 4/10 AM") w następujących metod:  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Wpływają na nie inne wzorce.  
  
 `<EnableAmPmParseAdjustment>` Element nie ma wpływu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody.  
  
> [!IMPORTANT]
>  .NET Core i .NET Native skorygowany AM/PM reguły analizy składni są domyślnie włączone.  
  
 Jeśli nie włączono analizy reguła korekty, pierwszą cyfrą ciąg jest interpretowany jako godzinę 12-godzinnym, a pozostała część ciągu, oprócz oznaczenia AM/PM jest ignorowany. Data i godzina zwracany przez metodę analizowania składa się z bieżącą datę i godzinę dnia, o której wyodrębnione z ciągu daty.  
  
 Po włączeniu analizy reguła korekty analizy metody interpretacji dzień i miesiąc jako należące do bieżącego roku i interpretować czasie, co godzinę 12-godzinnym.  
  
 W poniższej tabeli przedstawiono różnice w <xref:System.DateTime> wartość przy <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> metoda służy do analizowania ciągu "" 4/10 6 AM"za pomocą `<EnableAmPmParseAdjustment>` elementu `enabled` właściwość ustawioną na"0"lub"1". Przyjęto założenie, że dzisiaj jest 5 stycznia 2017 r. i wyświetla datę tak, jakby jest formatowana przy użyciu ciągu formatu "G" określonej kultury.  
  
|Nazwa kultury|enabled="0"|enabled="1"|  
|------------------|------------------|------------------|  
|en-US|2017-1-5 4:00:00 AM|2017-10/4 6:00:00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Zobacz także

- [\<środowisko uruchomieniowe > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [\<Konfiguracja > Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
