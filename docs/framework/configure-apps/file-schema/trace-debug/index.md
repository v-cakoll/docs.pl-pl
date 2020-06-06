---
title: Schemat ustawień śledzenia i debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927120"
---
# <a name="trace-and-debug-settings-schema"></a>Schemat ustawień śledzenia i debugowania
Ustawienia śledzenia i debugowania określają detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.  
  
 W poniższej tabeli opisano funkcję każdego elementu ustawień śledzenia i debugowania.  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.|  
|[\<add>](add-element-for-listeners-for-trace.md)|Dodaje odbiornik do `Listeners` kolekcji.|  
|[\<add>](add-element-for-sharedlisteners.md)|Dodaje odbiornik do `sharedListeners` kolekcji.|  
|[\<add>](add-element-for-switches.md)|Określa poziom, w którym jest ustawiony przełącznik śledzenia.|  
|[\<assert>](assert-element.md)|Określa, czy podczas wywoływania metody ma być wyświetlane okno komunikatu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> , a także określa nazwę pliku, w którym mają zostać zapisane komunikaty.|  
|[\<clear>](clear-element-for-listeners-for-source.md)|Czyści `Listeners` kolekcję dla źródła śledzenia.|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|Czyści `Listeners` kolekcję do śledzenia.|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji dla źródła śledzenia.|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji w celu śledzenia.|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|Dodaje filtr do odbiornika w `sharedListeners` kolekcji.|  
|[\<listeners>](listeners-element-for-source.md)|Określa detektory dla `Listeners` kolekcji dla źródła śledzenia.|  
|[\<listeners>](listeners-element-for-trace.md)|Określa detektory dla `Listeners` kolekcji do śledzenia.|  
|[\<performanceCounters>](performancecounters-element.md)|Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności.|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|Usuwa odbiornik z `Listeners` kolekcji na potrzeby śledzenia.|  
|[\<remove>](remove-element-for-listeners-for-source.md)|Usuwa odbiornik z `Listeners` kolekcji dla źródła śledzenia.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace.|  
|[\<sources>](sources-element.md)|Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.|  
|[\<source>](source-element.md)|Określa źródło śledzenia, które inicjuje komunikaty śledzenia.|  
|[\<switches>](switches-element.md)|Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.|  
|[\<system.diagnostics>](system-diagnostics-element.md)|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|[\<trace>](trace-element.md)|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [Schemat pliku konfiguracji](../index.md)
