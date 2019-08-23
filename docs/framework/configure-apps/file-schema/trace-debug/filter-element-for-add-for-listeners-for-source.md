---
title: <filter><add> Dla elementu<listeners> for<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0d25d0b955a94986147922914068c8a1cf2d96c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920516"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<Filtr elementu > do \<dodawania > dla \<odbiorników > \<dla źródła >
Dodaje filtr do odbiornika w `Listeners` kolekcji dla źródła śledzenia.  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<> źródeł  
\<> źródłowa  
\<> odbiorników  
\<add>  
\<Filtr >  
  
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
|`type`|Atrybut wymagany.<br /><br /> Określa typ filtru, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> po klasie. Można użyć nazwy typu kwalifikowanej przestrzeni nazw, która odpowiada <xref:System.Type.FullName%2A> właściwości typu, lub można użyć w pełni kwalifikowanej nazwy typu, w tym informacji o zestawie, która odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości. Aby uzyskać informacje na temat w pełni kwalifikowanych nazw typów, zobacz [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przesłany do konstruktora dla określonej klasy filtru.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.|  
|`source`|Określa źródło śledzenia, które inicjuje komunikaty śledzenia.|  
|`listeners`|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty. Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`add`|Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Element musi być zawarty `<add>` w elemencie dla odbiornika źródła śledzenia, który określa typ odbiornika, a nie tylko nazwę odbiornika zdefiniowanego w [ \<sharedListeners >.](sharedlisteners-element.md) `<filter>` Jeśli odbiornik jest zdefiniowany w [ \<> sharedListeners](sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowany w tym elemencie.  
  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje `<filter>` , jak za pomocą elementu dodać filtr do odbiornika `console` w `Listeners` kolekcji dla źródła `myTraceSource`śledzenia, określając poziom zdarzenia filtru jako `Error`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Schemat ustawień śledzenia i debugowania](index.md)
