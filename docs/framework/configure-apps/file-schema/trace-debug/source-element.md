---
title: '&lt;źródło&gt; — Element'
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 818324077322fffb40a192c9197efde6e8ff7591
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088948"
---
# <a name="ltsourcegt-element"></a>&lt;źródło&gt; — Element
Określa źródło śledzenia, który inicjuje komunikatów śledzenia.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<źródła >  
\<źródło >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Atrybut opcjonalny.<br /><br /> Określa nazwę źródła śledzenia.|  
|`switchName`|Atrybut opcjonalny.<br /><br /> Określa nazwę wystąpienia przełącznika śledzenia w aplikacji. Jeśli przełącznik nie zostanie zidentyfikowany w `<switches>` elementu, a wartość określa poziom przełącznika.|  
|`switchType`|Atrybut opcjonalny.<br /><br /> Określa typ o przełącznikiem śledzenia. Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.|  
|`extraAttribute`|Atrybut opcjonalny.<br /><br /> Określa wartość atrybutu specyficznymi dla źródła śledzenia identyfikowane przez <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodę dla tego źródła śledzenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<odbiorniki >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<source>` elementu do dodania źródła śledzenia `mySource` i ustaw poziom przełącznik źródła o nazwie `sourceSwitch`. Detektor śledzenia konsoli jest dodawany, który zapisuje informacje śledzenia do konsoli.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Przełączniki śledzenia](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
