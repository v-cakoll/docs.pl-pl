---
title: <clear>Element dla <listeners> elementu<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927170"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<Wyczyść element > dla \<odbiorników \<> śledzenia >
`Listeners` Czyści kolekcję do śledzenia.  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<> śledzenia  
\<> odbiorników  
\<clear>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`trace`|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.|  
|`listeners`|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty. Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 Element usuwa wszystkie odbiorniki `Listeners` z kolekcji w celu śledzenia. `<clear>` Możesz użyć `<clear>` elementu przed użyciem elementu, `<add>` aby mieć pewność, że w kolekcji nie ma żadnych innych aktywnych odbiorników.  
  
 Możesz wyczyścić `Listeners` kolekcję programowo, <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> wywołując metodę we <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> właściwości (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
> [!NOTE]
> `<clear>` Element usuwa<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> z kolekcji`Listeners`, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>zmieniając zachowanie metod<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>,,i. <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DefaultTraceListener> Wywołanie metody `Fail` lub zwykle powoduje wyświetlenie okna komunikatu. `Assert` Jednak okno komunikatu nie jest wyświetlane, jeśli <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się `Listeners` w kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje `<clear>` , jak używać elementu przed użyciem elementu, `<add>` aby `Listeners` dodać odbiornik `console` do kolekcji w celu śledzenia.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Schemat ustawień śledzenia i debugowania](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [Obiekty nasłuchujące śledzenie](../../../debug-trace-profile/trace-listeners.md)
