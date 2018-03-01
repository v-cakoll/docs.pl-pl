---
title: "&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b2739cc5eaa6a1e43c06849e1b00f7ac8bd531e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;
Czyści `Listeners` kolekcji do śledzenia.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<śledzenia >  
\<obiekty nasłuchujące >  
\<Wyczyść >  
  
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
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
|`trace`|Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.|  
|`listeners`|Zawiera nasłuchujących zbierania, przechowywania i kierowania wiadomości. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 `<clear>` Elementu spowoduje usunięcie wszystkich odbiorników z `Listeners` kolekcji do śledzenia. Można użyć `<clear>` element, aby można było używać `<add>` elementu, aby mieć pewność, istnieją inne odbiorników active w kolekcji.  
  
 Możesz wyczyścić `Listeners` kolekcji programowo przez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metoda <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> właściwości (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
> [!NOTE]
>  `<clear>` Usuwa element <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekcji zmianę zachowania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody. Wywoływanie `Assert` lub `Fail` metody zwykle powoduje wyświetlanie okna komunikatu. Jednak w oknie komunikatu nie jest wyświetlane, gdy <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się w `Listeners` kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<clear>` element, aby można było używać `<add>` elementu do dodania odbiornika `console` do `Listeners` kolekcji do śledzenia.  
  
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
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [\<Usuń >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
