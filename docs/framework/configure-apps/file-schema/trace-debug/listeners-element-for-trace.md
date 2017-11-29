---
title: "&lt;obiekty nasłuchujące&gt; elementu &lt;śledzenia&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 97d6673fddb20e99454bf97c87254049b82f0000
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistenersgt-element-for-lttracegt"></a>&lt;obiekty nasłuchujące&gt; elementu &lt;śledzenia&gt;
Określa odbiornika zbiera, magazynów i kieruje komunikaty. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.  
  
 \<Konfiguracja > — Element  
\<System.Diagnostics > — Element  
\<śledzenia > — Element  
\<obiekty nasłuchujące > elementu \<śledzenia >  
  
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
|[\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Dodaje odbiornika do `Listeners` kolekcji.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Czyści `Listeners` kolekcji do śledzenia.|  
|[\<Usuń >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Usuwa odbiornik z `Listeners` kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa element root dla sekcji konfiguracji ASP.NET.|  
|`trace`|Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klasy udostępnianie takie same **odbiorników** kolekcji. Jeśli obiekt odbiornika zostanie dodany do kolekcji w jednym z tych klas, inne klasy używa tego samego odbiornika. Klasy odbiornika dostarczone z programu .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie  **\<odbiorników >** elementu do dodania odbiorniki `MyListener` i `MyEventListener` do **odbiorników** kolekcji. `MyListener`Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `MyEventListener`tworzy wpis w dzienniku zdarzeń.  
  
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
 [Schemat ustawień debugowania i śledzenia](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
