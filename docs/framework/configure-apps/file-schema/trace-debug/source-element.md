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
manager: markl
ms.openlocfilehash: b7c2a71b129a0ad7d1c2a72b18b8a69a111f9495
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752575"
---
# <a name="ltsourcegt-element"></a>&lt;źródło&gt; — Element
Określa źródło śledzenia, który inicjuje śledzenia wiadomości.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<źródeł >  
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
|`switchName`|Atrybut opcjonalny.<br /><br /> Określa nazwę wystąpienia przełącznika śledzenia w aplikacji. Jeśli przełącznik nie zostanie zidentyfikowana w `<switches>` elementu, wartość określa poziom przełącznika.|  
|`switchType`|Atrybut opcjonalny.<br /><br /> Określa typ przełącznika śledzenia. Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.|  
|`extraAttribute`|Atrybut opcjonalny.<br /><br /> Określa wartość atrybutu określonego źródła śledzenia identyfikowane przez <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodę dla tego źródła śledzenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<obiekty nasłuchujące >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Zawiera nasłuchujących zbierania, przechowywania i kierowania wiadomości.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<source>` elementu do dodania źródła śledzenia `mySource` i ustaw poziom przełącznik źródła o nazwie `sourceSwitch`. Odbiornik śledzenia konsoli są dodawane który zapisuje informacje śledzenia do konsoli.  
  
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
