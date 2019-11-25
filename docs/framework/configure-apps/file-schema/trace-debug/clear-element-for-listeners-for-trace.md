---
title: Element <clear> dla <listeners> <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088913"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<Wyczyść element > dla odbiorników \<> \<śledzenia >
Czyści kolekcję `Listeners` na potrzeby śledzenia.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**odbiorników**](listeners-element-for-trace.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**

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
 Element `<clear>` usuwa wszystkie odbiorniki z kolekcji `Listeners` do śledzenia. Można użyć elementu `<clear>` przed użyciem elementu `<add>`, aby się upewnić, że nie ma żadnych innych aktywnych odbiorników w kolekcji.  
  
 Możesz wyczyścić kolekcję `Listeners` programowo, wywołując metodę <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> na właściwości <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
> [!NOTE]
> Element `<clear>` usuwa <xref:System.Diagnostics.DefaultTraceListener> z kolekcji `Listeners`, zmieniając zachowanie metod <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>. Wywołanie metody `Assert` lub `Fail` zwykle powoduje wyświetlenie okna komunikatu. Jednak okno komunikatu nie jest wyświetlane, jeśli <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się w kolekcji `Listeners`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać elementu `<clear>` przed użyciem elementu `<add>` do dodawania `console` odbiornika do kolekcji `Listeners` na potrzeby śledzenia.  
  
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
- [\<Usuń >](remove-element-for-listeners-for-trace.md)
- [Obiekty nasłuchujące śledzenie](../../../debug-trace-profile/trace-listeners.md)
