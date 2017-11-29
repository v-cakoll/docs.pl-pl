---
title: "&lt;śledzenia&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 157adb6c7317aa047976cdb9e30711d20c9e543b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttracegt-element"></a>&lt;śledzenia&gt; — Element
Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.  
  
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
|`autoflush`|Atrybut opcjonalny.<br /><br /> Określa, czy odbiorniki śledzenia automatycznie opróżniania buforu wyjściowego po każdej operacji zapisu.|  
|`indentsize`|Atrybut opcjonalny.<br /><br /> Określa liczbę spacji wcięcia.|  
|`useGlobalLock`|Atrybut opcjonalny.<br /><br /> Wskazuje, czy globalne blokady powinien być używany.|  
  
## <a name="autoflush-attribute"></a>AutoFlush atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie automatycznie opróżnić buforu wyjściowego. Domyślnie włączone.|  
|`true`|Automatycznie opróżnia bufor wyjściowy.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie używa globalnej blokady, jeśli odbiornik jest wielowątkowość; w przeciwnym razie używa globalnej blokady.|  
|`true`|Wykorzystuje globalne blokady niezależnie od tego, czy odbiornik bezpieczne dla wątków. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<obiekty nasłuchujące >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Określa odbiornika zbiera, magazynów i kieruje komunikaty.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<trace>` elementu do dodania odbiornika `MyListener` do `Listeners` kolekcji. `MyListener`Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `useGlobalLock` Atrybut ma ustawioną `false`, co powoduje, że globalne blokady nie powinna być używana, jeśli odbiornik śledzenia jest bezpieczne dla wątków. `autoflush` Atrybut ma ustawioną `true`, co powoduje, że nasłuchującego śledzenia do zapisania do pliku, niezależnie od tego, czy <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> metoda jest wywoływana. `indentsize` Atrybut jest ustawiony na 0 (zero), co powoduje, że odbiornika do zera wcięć przy <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> metoda jest wywoływana.  
  
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
 [Schemat ustawień debugowania i śledzenia](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
