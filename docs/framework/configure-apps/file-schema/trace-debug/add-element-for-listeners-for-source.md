---
title: <add>Element dla <listeners> elementu<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153688"
---
# <a name="add-element-for-listeners-for-source"></a>\<add>Element dla \<listeners> elementu\<source>
Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Składnia  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`type`|Wymagany atrybut, chyba że odwołujesz się do odbiornika w `sharedListeners` kolekcji, w takim przypadku należy tylko odwołać się do niego według nazwy (zobacz [przykład](#example)).<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przesłany do konstruktora dla określonej klasy. <xref:System.Configuration.ConfigurationException>Jest zgłaszany, jeśli Klasa nie ma konstruktora, który przyjmuje ciąg.|  
|`name`|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
|`traceOutputOptions`|Atrybut opcjonalny.<br /><br /> Określa <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> wartość właściwości dla odbiornika śledzenia.|  
|[atrybuty niestandardowe]|Atrybuty opcjonalne.<br /><br /> Określa wartość dla atrybutów specyficznych dla odbiornika identyfikowanych przez <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metodę dla tego odbiornika. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>jest przykładem dodatkowego atrybutu unikatowego dla <xref:System.Diagnostics.DelimitedListTraceListener> klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji dla źródła śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.|  
|`source`|Określa źródło śledzenia, które inicjuje komunikaty śledzenia.|  
|`listeners`|Określa detektory, które zbierają, przechowują i rozsyłają komunikaty.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczane z .NET Framework pochodzą od <xref:System.Diagnostics.TraceListener> klasy.  
  
 Jeśli nie określisz `name` atrybutu odbiornika śledzenia, <xref:System.Diagnostics.TraceListener.Name%2A> Właściwość odbiornika śledzenia domyślnie będzie pustym ciągiem (""). Jeśli aplikacja ma tylko jeden odbiornik, możesz ją dodać bez określenia nazwy i można ją usunąć, określając pusty ciąg w polu Nazwa. Jeśli jednak aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, co pozwala identyfikować poszczególne detektory śledzenia i zarządzać nimi w <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekcji.  
  
> [!NOTE]
> Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i z tą samą nazwą powoduje tylko jeden odbiornik śledzenia tego typu i nazwę dodawane do `Listeners` kolekcji. Można jednak programowo dodać wiele identycznych odbiorników do `Listeners` kolekcji.  
  
 Wartość `initializeData` atrybutu zależy od typu tworzonego odbiornika. Nie wszystkie detektory śledzenia wymagają określenia `initializeData` .  
  
> [!NOTE]
> W przypadku korzystania z `initializeData` atrybutu może zostać wyświetlone ostrzeżenie kompilatora "initializeData" nie jest zadeklarowany. " To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy bazowej <xref:System.Diagnostics.TraceListener> , która nie rozpoznaje `initializeData` atrybutu. Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartości ich `initializeData` atrybutów.  
  
|Trace — Klasa odbiornika|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`Wartość dla <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.  Ustaw `initializeData` atrybut na " `true` ", aby zapisać dane wyjściowe śledzenia i debugowania do strumienia błędu standardowego; Ustaw dla niego wartość " `false` ", aby zapisać w standardowym strumieniu wyjściowym.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym są <xref:System.Diagnostics.DelimitedListTraceListener> zapisywane dane.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.EventSchemaTraceListener> .|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.TextWriterTraceListener> .|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.XmlWriterTraceListener> .|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak za pomocą `<add>` elementów dodać odbiorniki `console` i `textListener` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp` . `textListener`Odbiornik zapisuje dane wyjściowe śledzenia do pliku listen. log.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
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
- [Schemat ustawień śledzenia i debugowania](index.md)
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
