---
title: '&lt;EnableAmPmParseAdjustment&gt; — Element'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17f521be31fa4082d9418c7dad734e37994bbb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt; — Element
Określa, czy data i czas przetwarzania metody użyć skorygowaną zbiór reguł do analizowania ciągi daty, które zawierają dzień, miesiąc, godzinę i oznaczenie AM/PM.  
  
 \<Konfiguracja >  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy data i czas przetwarzania metody użyć skorygowaną zbiór reguł do analizowania ciągi daty, które zawierają tylko dzień, miesiąc, godzinę i oznaczenie AM/PM.|  
  
### <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Data i czas przetwarzania metody nie należy używać reguł skorygowaną dla analizowanie ciągów daty, które zawierają tylko dzień, miesiąc, godzinę i oznaczenie AM/PM.|  
|1|Data i czas przetwarzania metody przy użyciu reguł skorygowaną analizowanie ciągów daty, które zawierają tylko dzień, miesiąc, godzinę i oznaczenie AM/PM.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 `<EnableAmPmParseAdjustment>` Element określa, jak przeanalizować ciąg daty, który zawiera liczbową dnia i miesiąca, a następnie godzinę i oznaczenie AM/PM (na przykład "4/10 6 AM") w następujących metod:  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Nie inne wzorce są zagrożone.  
  
 `<EnableAmPmParseAdjustment>` Element nie ma wpływu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, i <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody.  
  
> [!IMPORTANT]
>  Oprogramowanie .NET Core i platforma .NET Native skorygowanych reguł analizy AM/PM są domyślnie włączone.  
  
 Jeśli nie włączono analizy reguła korekty, cyfra pierwszy ciąg jest interpretowany jako godzina 12-godzinnym, a jest ignorowany w pozostałej części ciągu oprócz wskaźnik AM/PM. Data i godzina zwróconych przez metodę analizowania składa się z bieżącą datę i godzinę dnia, o której wyodrębnione z ciągu daty.  
  
 Włączenie analizy reguła korekty analizy metody interpretacji dnia i miesiąca jako należące do bieżącego roku i interpretować czasie co godzinę 12-godzinnym.  
  
 W poniższej tabeli przedstawiono różnice <xref:System.DateTime> wartość przy <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> metoda jest używana do analizy ciągu "" 4/10 6 AM"z `<EnableAmPmParseAdjustment>` elementu `enabled` właściwości wartość"0"lub"1". Przyjęto założenie, że dzisiaj jest 5 stycznia 2017 r i wyświetla datę tak, jakby jest sformatowany przy użyciu ciągu formatu "G" określonej kultury.  
  
|Nazwa kultury|włączone = "0"|włączone = "1"|  
|------------------|------------------|------------------|  
|EN US|1/5/2017 4:00:00: 00|4/10/2017 6:00:00: 00|  
|pl pl.|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Zobacz też  
 [\<środowisko uruchomieniowe > — Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
