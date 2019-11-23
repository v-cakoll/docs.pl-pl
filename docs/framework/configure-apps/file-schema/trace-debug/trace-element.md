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
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699180"
---
# <a name="trace-element"></a>Element > śledzenia \<
Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.  
  
[ **> konfiguracji \<** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<system. Diagnostics >** ](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<trace >**  
  
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
|`autoflush`|Atrybut opcjonalny.<br /><br /> Określa, czy odbiorniki śledzenia automatycznie opróżniają bufor wyjściowy po każdej operacji zapisu.|  
|`indentsize`|Atrybut opcjonalny.<br /><br /> Określa liczbę spacji do wcięcia.|  
|`useGlobalLock`|Atrybut opcjonalny.<br /><br /> Wskazuje, czy globalna blokada powinna być używana.|  
  
## <a name="autoflush-attribute"></a>AutoFlush — atrybut  
  
|Value|Opis|  
|-----------|-----------------|  
|`false`|Nie opróżnia bufora wyjściowego. Domyślnie włączone.|  
|`true`|Automatycznie opróżnia bufor wyjściowy.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock Attribute  
  
|Value|Opis|  
|-----------|-----------------|  
|`false`|Nie używa blokady globalnej, jeśli odbiornik jest bezpieczny wątkowo; w przeciwnym razie używa blokady globalnej.|  
|`true`|Używa blokady globalnej niezależnie od tego, czy odbiornik jest bezpieczny wątkowo. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<detektory >](listeners-element-for-trace.md)|Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć elementu `<trace>`, aby dodać `MyListener` odbiornika do kolekcji `Listeners`. `MyListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. Atrybut `useGlobalLock` jest ustawiony na `false`, co powoduje, że globalna blokada nie zostanie użyta, jeśli odbiornik śledzenia jest bezpieczny wątkowo. Atrybut `autoflush` jest ustawiony na `true`, co powoduje, że odbiornik śledzenia ma zapisywać do pliku bez względu na to, czy metoda <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> jest wywoływana. Atrybut `indentsize` jest ustawiony na 0 (zero), co powoduje, że odbiornik ma wcięcie zerowej spacji w przypadku wywołania metody <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
