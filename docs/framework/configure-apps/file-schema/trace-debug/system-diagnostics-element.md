---
title: <system.diagnostyka> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153210"
---
# <a name="systemdiagnostics-element"></a>\<element> system.diagnostics
Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;**\<>system.diagnostics**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dochodzić>](assert-element.md)|Określa, czy okno komunikatu ma <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> być wyświetlane podczas wywoływania metody; określa również nazwę pliku, do który mają być zapisywane wiadomości.|  
|[\<performanceCounters>](performancecounters-element.md)|Określa rozmiar pamięci globalnej współużytkowanej przez liczniki wydajności.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Zawiera detektory, do których może odwoływać się dowolne źródło lub element śledzenia. Detektory zidentyfikowane jako detektory udostępnione można dodać do źródeł lub śladów według nazwy.|  
|[\<źródeł>](sources-element.md)|Określa źródła śledzenia, które inicjują komunikaty śledzenia.|  
|[\<przełączniki>](switches-element.md)|Zawiera przełączniki śledzenia i poziomy, na których są ustawione przełączniki śledzenia.|  
|[\<>śledzenia](trace-element.md)|Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak osadzić przełącznik śledzenia i odbiornik śledzenia wewnątrz ** \<elementu>system.diagnostics.** Przełącznik `General` śledzenia jest ustawiony <xref:System.Diagnostics.TraceLevel> na poziomie. Odbiornik śledzenia `myListener` tworzy plik `MyListener.log` o nazwie i zapisuje dane wyjściowe do pliku.  
  
> [!NOTE]
> W .NET Framework w wersji 2.0 można użyć tekstu, aby określić wartość przełącznika. Na przykład można `true` określić <xref:System.Diagnostics.BooleanSwitch> dla tekstu lub użyć tekstu reprezentującego `Error` wartość <xref:System.Diagnostics.TraceSwitch>wyliczenia, taką jak dla . Linia `<add name="myTraceSwitch" value="Error" />` jest równoważna `<add name="myTraceSwitch" value="1" />`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [Schemat ustawień śledzenia i debugowania](index.md)
