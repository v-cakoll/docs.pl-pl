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
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699193"
---
# <a name="systemdiagnostics-element"></a>\<element > System. Diagnostics
Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.  
  
[ **> konfiguracji \<** ](../configuration-element.md)  
&nbsp;&nbsp; **\<system. diagnostics >**  
  
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
|[\<Assert >](assert-element.md)|Określa, czy podczas wywoływania metody <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ma być wyświetlane okno komunikatu. określa również nazwę pliku, do którego mają być zapisane wiadomości.|  
|[\<liczniki wydajności >](performancecounters-element.md)|Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności.|  
|[\<sharedListeners >](sharedlisteners-element.md)|Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace. Odbiorniki identyfikowane jako odbiorniki udostępnione mogą być dodawane do źródeł lub śladów według nazwy.|  
|[\<źródła >](sources-element.md)|Określa źródła śledzenia, które inicjują komunikaty śledzenia.|  
|[\<przełączniki >](switches-element.md)|Zawiera przełączniki śledzenia i poziomy, w których są ustawiane przełączniki śledzenia.|  
|[\<trace>](trace-element.md)|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak osadzić przełącznik śledzenia i odbiornik śledzenia wewnątrz elementu **\<system. diagnostics >** . Przełącznik śledzenia `General` jest ustawiony na poziom <xref:System.Diagnostics.TraceLevel>. Odbiornik śledzenia `myListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 można użyć tekstu, aby określić wartość dla przełącznika. Na przykład można określić `true` dla <xref:System.Diagnostics.BooleanSwitch> lub użyć tekstu reprezentującego wartość wyliczenia, taką jak `Error` dla <xref:System.Diagnostics.TraceSwitch>. Wiersz `<add name="myTraceSwitch" value="Error" />` jest równoznaczny z `<add name="myTraceSwitch" value="1" />`.  
  
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
