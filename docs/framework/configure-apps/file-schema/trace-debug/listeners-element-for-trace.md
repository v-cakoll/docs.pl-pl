---
title: '&lt;odbiorniki&gt; elementu &lt;śledzenia&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: bfcf96c553f85aeb0a40dfd6ea36667d504e8eee
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028004"
---
# <a name="ltlistenersgt-element-for-lttracegt"></a>&lt;odbiorniki&gt; elementu &lt;śledzenia&gt;
Określa odbiornik, który zbiera, magazynów i przekazuje komunikaty. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.  
  
 \<Konfiguracja > Element  
\<System.Diagnostics > Element  
\<Śledzenie > Element  
\<odbiorniki >, Element dla \<śledzenia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Dodaje odbiornik do `Listeners` kolekcji.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Czyści `Listeners` kolekcji na potrzeby śledzenia.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Usuwa odbiornik z `Listeners` kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.|  
|`trace`|Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klasy współużytkować ten sam **odbiorników** kolekcji. Jeśli dodasz obiektu odbiornika do kolekcji w jednym z tych klas, inne klasy używa tego samego odbiornika. Klasy odbiornika dostarczane z programem .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać  **\<odbiorników >** elementu do dodania odbiorniki `MyListener` i `MyEventListener` do **odbiorników** kolekcji. `MyListener` Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `MyEventListener` tworzy wpis w dzienniku zdarzeń.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.TraceListener>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
