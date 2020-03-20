---
title: <filter>Element <add> dla <listeners> dla<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153519"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<filtr> Element \<dodawania> dla \<> dla> \<źródłowych
Dodaje filtr do odbiornika `Listeners` w kolekcji dla źródła śledzenia.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>źródłowe**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtra**

## <a name="syntax"></a>Składnia  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`type`|Atrybut wymagany.<br /><br /> Określa typ filtru, który powinien dziedziczyć z <xref:System.Diagnostics.TraceFilter> klasy. Można użyć nazwy kwalifikowanej obszaru nazw typu, która odpowiada <xref:System.Type.FullName%2A> właściwości typu, lub można użyć w pełni kwalifikowanej nazwy typu, <xref:System.Type.AssemblyQualifiedName%2A> w tym informacji o zestawie, która odpowiada właściwości. Aby uzyskać informacje o w pełni kwalifikowanych nazwach typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy filtru.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.|  
|`source`|Określa źródło śledzenia, które inicjuje śledzenie komunikatów.|  
|`listeners`|Zawiera odbiorniki, które zbierają, przechowują i rozsyłają wiadomości. Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`add`|Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<filter>` musi być zawarty `<add>` w elemencie dla odbiornika źródła śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowaną [ \<w sharedListeners>](sharedlisteners-element.md). Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners>, ](sharedlisteners-element.md)filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.  
  
 Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<filter>` pokazano, jak użyć elementu, `console` aby `Listeners` dodać filtr `myTraceSource`do odbiornika w kolekcji dla źródła śledzenia, określając poziom zdarzenia filtru jako `Error`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Schemat ustawień śledzenia i debugowania](index.md)
