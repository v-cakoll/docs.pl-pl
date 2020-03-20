---
title: <add>Element <listeners> dla<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153688"
---
# <a name="add-element-for-listeners-for-source"></a>\<dodaj element> dla \<> dla> \<źródłowych
Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>źródłowe**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**

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
|`type`|Wymagany atrybut, chyba że odwołujesz się do `sharedListeners` odbiornika w kolekcji, w którym to przypadku wystarczy odwołać się do niego tylko według nazwy (zobacz [przykład](#example)).<br /><br /> Określa typ odbiornika. Należy użyć ciągu spełniającego wymagania określone w określaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy. A <xref:System.Configuration.ConfigurationException> jest generowany, jeśli klasa nie ma konstruktora, który przyjmuje ciąg.|  
|`name`|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
|`traceOutputOptions`|Atrybut opcjonalny.<br /><br /> Określa wartość <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> właściwości dla odbiornika śledzenia.|  
|[atrybuty niestandardowe]|Atrybuty opcjonalne.<br /><br /> Określa wartość atrybutów specyficznych dla odbiornika <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> identyfikowane przez metodę dla tego odbiornika. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>jest przykładem dodatkowego atrybutu <xref:System.Diagnostics.DelimitedListTraceListener> unikatowego dla klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>filtra](filter-element-for-add-for-listeners-for-source.md)|Dodaje filtr do odbiornika `Listeners` w kolekcji dla źródła śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.|  
|`source`|Określa źródło śledzenia, które inicjuje śledzenie komunikatów.|  
|`listeners`|Określa odbiorniki, które zbierają, przechowują i rozsyłają wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczane z .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy.  
  
 Jeśli nie określisz `name` atrybutu odbiornika śledzenia, <xref:System.Diagnostics.TraceListener.Name%2A> właściwość odbiornika śledzenia domyślnie pusty ciąg (""). Jeśli aplikacja ma tylko jeden odbiornik, można dodać go bez określania nazwy i można ją usunąć, określając pusty ciąg dla nazwy. Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> który pozwala zidentyfikować i zarządzać poszczególnych odbiorników śledzenia w kolekcji.  
  
> [!NOTE]
> Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i o tej samej nazwie powoduje `Listeners` tylko jeden odbiornik śledzenia tego typu i nazwy dodawane do kolekcji. Jednak programowo można dodać wiele identycznych `Listeners` odbiorników do kolekcji.  
  
 Wartość atrybutu `initializeData` zależy od typu odbiornika, który tworzysz. Nie wszystkie detektory śledzenia `initializeData`wymagają określenia .  
  
> [!NOTE]
> Korzystając z `initializeData` atrybutu, może pojawić się ostrzeżenie kompilatora "Atrybut 'initializeData' nie jest zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są <xref:System.Diagnostics.TraceListener>sprawdzane względem abstrakcyjnej klasy podstawowej, która nie rozpoznaje atrybutu. `initializeData` Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornika śledzenia, które mają konstruktora, który przyjmuje parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone `initializeData` do programu .NET Framework i opisano wartość ich atrybutów.  
  
|Śledzenie klasy detektora|initializeDane wartość atrybutu|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Wartość `useErrorStream` konstruktora. <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>  Ustaw `initializeData` atrybut na`true`" ", aby zapisać śledzenie i debugowanie danych wyjściowych do standardowego strumienia błędów; ustawić go`false`na " ", aby zapisać do standardowego strumienia wyjściowego.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku, do <xref:System.Diagnostics.DelimitedListTraceListener> który zapisuje się.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<add>` pokazano, jak `console` używać `textListener` elementów do dodawania odbiorników i `Listeners` do kolekcji dla źródła `TraceSourceApp`śledzenia . Odbiornik `textListener` zapisuje dane wyjściowe śledzenia do pliku myListener.log.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
