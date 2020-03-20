---
title: <clear>Element <listeners> dla<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153545"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<clear> Element dla \<słuchaczy>> \<śledzenia
Czyści `Listeners` kolekcję do śledzenia.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wyraźne>**

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
|`system.diagnostics`|Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.|  
|`trace`|Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.|  
|`listeners`|Zawiera odbiorniki, które zbierają, przechowują i rozsyłają wiadomości. Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<clear>` usuwa wszystkie odbiorniki `Listeners` z kolekcji do śledzenia. Można użyć `<clear>` elementu przed `<add>` użyciem elementu, aby mieć pewność, że nie ma żadnych innych aktywnych odbiorników w kolekcji.  
  
 Kolekcję `Listeners` można wyczyścić programowo, <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> wywołując <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> metodę`System.Diagnostics.Trace.Listeners.Clear()`we właściwości ( ).  
  
 Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
> [!NOTE]
> Element `<clear>` <xref:System.Diagnostics.DefaultTraceListener> usuwa `Listeners` z kolekcji, zmieniając zachowanie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody. Wywołanie `Assert` `Fail` lub metoda zwykle powoduje wyświetlenie okna komunikatu. Jednak okno komunikatu nie jest <xref:System.Diagnostics.DefaultTraceListener> wyświetlany, jeśli `Listeners` nie jest w kolekcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<clear>` pokazano, jak `<add>` używać elementu przed `console` użyciem elementu, aby dodać odbiornika do `Listeners` kolekcji do śledzenia.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Schemat ustawień śledzenia i debugowania](index.md)
- [\<usuń>](remove-element-for-listeners-for-trace.md)
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
