---
title: '&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 362e1d7a4ac4c39309aa86561683df1d239f2ab1
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083873"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;
Czyści `Listeners` kolekcję dla źródła śledzenia.  
  
 \<Konfiguracja >  
\<system.diagnostics>  
\<źródła >  
\<source>  
\<listeners>  
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
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.|  
|`source`|Określa źródło śledzenia, który inicjuje komunikatów śledzenia.|  
|`listeners`|Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.|  
  
## <a name="remarks"></a>Uwagi  
 `<clear>` Elementu usuwa wszystkie odbiorniki z `Listeners` kolekcję dla źródła śledzenia, łącznie z <xref:System.Diagnostics.DefaultTraceListener>. Możesz użyć `<clear>` element przed użyciem `<add>` elementu, aby mieć pewność, istnieją nie aktywne odbiorniki w kolekcji.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<clear>` element przed użyciem `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
