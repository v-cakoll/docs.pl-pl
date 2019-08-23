---
title: < element > System. Diagnostics
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: f3b4238a8d7028d47122a420526b38ee4f327332
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926942"
---
# <a name="systemdiagnostics-element"></a>\<Element System. Diagnostics >
Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.  
  
 \<> konfiguracji  
\<system.diagnostics>  
  
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
|[\<> potwierdzenia](assert-element.md)|Określa, czy podczas wywoływania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody ma być wyświetlane okno komunikatu, a także określa nazwę pliku, w którym mają zostać zapisane komunikaty.|  
|[\<Liczniki wydajności >](performancecounters-element.md)|Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności.|  
|[\<sharedListeners >](sharedlisteners-element.md)|Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace. Odbiorniki identyfikowane jako odbiorniki udostępnione mogą być dodawane do źródeł lub śladów według nazwy.|  
|[\<> źródeł](sources-element.md)|Określa źródła śledzenia, które inicjują komunikaty śledzenia.|  
|[\<Przełączniki >](switches-element.md)|Zawiera przełączniki śledzenia i poziomy, w których są ustawiane przełączniki śledzenia.|  
|[\<trace>](trace-element.md)|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak osadzić przełącznik śledzenia i odbiornik śledzenia wewnątrz  **\<elementu System. Diagnostics >** . Przełącznik śledzenia jest ustawiony <xref:System.Diagnostics.TraceLevel> na poziom. `General` Odbiornik `myListener` śledzenia tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 można użyć tekstu, aby określić wartość dla przełącznika. `true` Na przykład można określić <xref:System.Diagnostics.BooleanSwitch> dla lub użyć tekstu reprezentującego wartość wyliczenia, taką jak `Error` dla elementu <xref:System.Diagnostics.TraceSwitch>. Wiersz `<add name="myTraceSwitch" value="Error" />` jest`<add name="myTraceSwitch" value="1" />`odpowiednikiem.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [Schemat ustawień śledzenia i debugowania](index.md)
