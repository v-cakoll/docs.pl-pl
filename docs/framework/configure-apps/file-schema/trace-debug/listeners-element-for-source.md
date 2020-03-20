---
title: <listeners>, element dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153415"
---
# <a name="listeners-element-for-source"></a>\<słuchaczy> Element dla \<> źródłowych
Dodaje lub usuwa odbiorników <xref:System.Diagnostics.TraceSource.Listeners%2A> w <xref:System.Diagnostics.TraceSource>kolekcji dla . Odbiornik kieruje dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takiego jak dziennik, okno lub plik tekstowy.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>źródłowe**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<słuchacze>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add-element-for-listeners-for-source.md)|Dodaje odbiornik do `Listeners` kolekcji.|  
|[\<usuń>](remove-element-for-listeners-for-source.md)|Usuwa odbiornik z kolekcji. `Listeners`|  
|[\<wyraźne>](clear-element-for-listeners-for-source.md)|Czyści `Listeners` kolekcję dla źródła śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.|  
|`source`|Określa źródło śledzenia, które inicjuje śledzenie komunikatów.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<listeners>` pokazano, jak użyć elementu, `mySource` aby dodać odbiornik śledzenia konsoli do źródła i usunąć domyślny odbiornik śledzenia.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
