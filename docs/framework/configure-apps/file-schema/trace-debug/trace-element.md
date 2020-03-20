---
title: <trace>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153169"
---
# <a name="trace-element"></a>\<element> śledzenia
Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<>śledzenia**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`autoflush`|Atrybut opcjonalny.<br /><br /> Określa, czy detektory śledzenia automatycznie opróżniają bufor wyjściowy po każdej operacji zapisu.|  
|`indentsize`|Atrybut opcjonalny.<br /><br /> Określa liczbę spacji do wcięcie.|  
|`useGlobalLock`|Atrybut opcjonalny.<br /><br /> Wskazuje, czy blokada globalna powinna być używana.|  
  
## <a name="autoflush-attribute"></a>Atrybut autoflush  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie opróżnia automatycznie buforu wyjściowego. Domyślnie włączone.|  
|`true`|Automatycznie opróżnia bufor wyjściowy.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock Atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie używa blokady globalnej, jeśli odbiornik jest bezpieczny dla wątków; w przeciwnym razie używa blokady globalnej.|  
|`true`|Używa blokady globalnej, niezależnie od tego, czy odbiornik jest bezpieczny dla wątków. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<słuchacze>](listeners-element-for-trace.md)|Określa odbiornik, który zbiera, przechowuje i kieruje wiadomości.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<trace>` pokazano, jak użyć `MyListener` elementu, aby dodać odbiornik do `Listeners` kolekcji. `MyListener`tworzy plik, który `MyListener.log` jest nazwany i zapisuje dane wyjściowe do pliku. Atrybut `useGlobalLock` jest ustawiony `false`na , co powoduje, że blokada globalna nie ma być używany, jeśli odbiornik śledzenia jest bezpieczny dla wątków. Atrybut `autoflush` jest ustawiony `true`na , co powoduje, że odbiornik śledzenia do <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> zapisu do pliku, niezależnie od tego, czy metoda jest wywoływana. Atrybut `indentsize` jest ustawiony na 0 (zero), co powoduje, że odbiornik <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> wcięcie zero spacji, gdy metoda jest wywoływana.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
