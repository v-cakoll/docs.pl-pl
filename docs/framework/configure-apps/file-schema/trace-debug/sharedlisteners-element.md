---
title: '&lt;sharedListeners&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3069022287d469704cc7adac40d02ef3c6997b56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563056"
---
# <a name="ltsharedlistenersgt-element"></a>&lt;sharedListeners&gt; — Element
Zawiera dowolnego źródła i elementu śledzenia można odwoływać się do obiektów nasłuchujących.  Te odbiorniki nie otrzymasz żadnych śladów domyślnie i nie jest możliwe pobrać te odbiorniki w czasie wykonywania. Odbiorniki zidentyfikowane jako współdzielonych detektorów można dodać do źródła lub śledzenie według nazwy.  
  
 \<Konfiguracja >  
\<system.diagnostics>  
\<sharedListeners>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Dodaje odbiornik do `sharedListeners` kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`Configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
 Dodanie detektora do kolekcji współdzielonych detektorów nie powoduje on aktywny odbiornik. Jego musi nadal będzie dodawany do źródła śledzenia lub śledzenia przez dodanie jej do `Listeners` kolekcji dla tego elementu śledzenia. Klasy odbiornika w programie .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.  
  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<sharedListeners>` elementu do dodania odbiornika `console` do `Listeners` kolekcji dla obu <xref:System.Diagnostics.TraceSource> i <xref:System.Diagnostics.Trace> klasy. Odbiornik śledzenia konsoli zapisuje informacje śledzenia do konsoli, za pośrednictwem wywołania do jednej <xref:System.Diagnostics.TraceSource> lub <xref:System.Diagnostics.Trace>.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Diagnostics.TraceListener>
- [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
