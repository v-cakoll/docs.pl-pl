---
title: '&lt;śledzenie&gt; — Element'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 55a7eb431432b67b3252853d14bf93be304ee883
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046522"
---
# <a name="lttracegt-element"></a>&lt;śledzenie&gt; — Element
Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<śledzenia >  
  
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
|`autoflush`|Atrybut opcjonalny.<br /><br /> Określa, czy obiekty nasłuchujące śledzenia automatycznie opróżniania buforu wyjściowego po każdej operacji zapisu.|  
|`indentsize`|Atrybut opcjonalny.<br /><br /> Określa liczbę spacji wcięcia.|  
|`useGlobalLock`|Atrybut opcjonalny.<br /><br /> Wskazuje, czy należy użyć globalnego blokady.|  
  
## <a name="autoflush-attribute"></a>AutoFlush atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie opróżnia automatycznie bufor wyjściowy. Domyślnie włączone.|  
|`true`|Automatycznie opróżnia bufor wyjściowy.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie używa globalnej blokady, jeśli odbiornik jest bezpieczny wątkowo; w przeciwnym razie używa globalnego blokady.|  
|`true`|Używa globalnych blokady niezależnie od tego, czy odbiornik jest bezpieczny dla wątków. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<odbiorniki >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Określa odbiornik, który zbiera, magazynów i przekazuje komunikaty.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<trace>` elementu do dodania odbiornika `MyListener` do `Listeners` kolekcji. `MyListener` Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `useGlobalLock` Ma ustawioną wartość atrybutu `false`, co powoduje, że globalne blokady nie powinna być używana, jeśli odbiornik śledzenia jest bezpieczny dla wątków. `autoflush` Ma ustawioną wartość atrybutu `true`, co powoduje, że odbiornik śledzenia można zapisać do pliku, niezależnie od tego, czy <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> metoda jest wywoływana. `indentsize` Atrybut jest ustawiony na wartość 0 (zero), co powoduje, że odbiornika wcięcia zero miejsca do magazynowania podczas <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> metoda jest wywoływana.  
  
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
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
