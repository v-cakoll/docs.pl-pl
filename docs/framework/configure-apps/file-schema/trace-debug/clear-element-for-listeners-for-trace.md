---
title: <clear>Element dla <listeners> elementu<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153545"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<clear>Element dla \<listeners> elementu\<trace>
Czyści `Listeners` kolekcję do śledzenia.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

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
 `<clear>`Element usuwa wszystkie odbiorniki z `Listeners` kolekcji w celu śledzenia. Możesz użyć `<clear>` elementu przed użyciem `<add>` elementu, aby mieć pewność, że w kolekcji nie ma żadnych innych aktywnych odbiorników.  
  
 Możesz wyczyścić `Listeners` kolekcję programowo, wywołując <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metodę we <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> właściwości ( `System.Diagnostics.Trace.Listeners.Clear()` ).  
  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
> [!NOTE]
> `<clear>`Element usuwa <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekcji, zmieniając zachowanie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> metod,, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> . Wywołanie `Assert` metody lub `Fail` zwykle powoduje wyświetlenie okna komunikatu. Jednak okno komunikatu nie jest wyświetlane, jeśli <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się w `Listeners` kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<clear>` elementu przed użyciem `<add>` elementu, aby dodać odbiornik `console` do `Listeners` kolekcji w celu śledzenia.  
  
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
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
