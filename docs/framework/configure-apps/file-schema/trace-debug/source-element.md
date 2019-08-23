---
title: <source>, element
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 55120e292ac2a2c822c5510563d1aa167ca921e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920455"
---
# <a name="source-element"></a>\<źródłowy element >
Określa źródło śledzenia, które inicjuje komunikaty śledzenia.  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<> źródeł  
\<> źródłowa  
  
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
|`switchName`|Atrybut opcjonalny.<br /><br /> Określa nazwę wystąpienia przełącznika śledzenia w aplikacji. Jeśli przełącznik nie zostanie zidentyfikowany w `<switches>` elemencie, wartość określa poziom przełącznika.|  
|`switchType`|Atrybut opcjonalny.<br /><br /> Określa typ przełącznika śledzenia. Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.|  
|`extraAttribute`|Atrybut opcjonalny.<br /><br /> Określa wartość dla atrybutu specyficznego dla źródła śledzenia identyfikowanego przez <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodę dla tego źródła śledzenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> odbiorników](listeners-element-for-source.md)|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć elementu, `<source>` aby dodać źródło `mySource` śledzenia i ustawić poziom dla przełącznika źródła o nazwie `sourceSwitch`. Dodano odbiornik śledzenia konsoli, który zapisuje informacje o śledzeniu do konsoli.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień śledzenia i debugowania](index.md)
- [Przełączniki śledzenia](../../../debug-trace-profile/trace-switches.md)
