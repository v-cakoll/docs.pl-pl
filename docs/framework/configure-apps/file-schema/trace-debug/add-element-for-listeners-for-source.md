---
title: <add> Element <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 4d2952e29b09fcf9f81624317e30caf301a61a51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165490"
---
# <a name="add-element-for-listeners-for-source"></a>\<Dodaj >, Element dla \<odbiorników > dla \<źródła >
Dodaje odbiornik do `Listeners` kolekcję dla źródła śledzenia.  
  
 \<Konfiguracja >  
\<system.diagnostics>  
\<źródła >  
\<source>  
\<listeners>  
\<add>  
  
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
|`type`|Wymagany atrybut, chyba że masz odwołanie do odbiornika w `sharedListeners` kolekcji, w którym sprawa jest konieczne tylko odwołanie do niego za pomocą nazwy (zobacz [przykład](#example)).<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy. Element <xref:System.Configuration.ConfigurationException> jest generowany, jeśli klasa nie ma konstruktora, który przyjmuje ciąg.|  
|`name`|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
|`traceOutputOptions`|Atrybut opcjonalny.<br /><br /> Określa <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> wartości właściwości dla odbiornika śledzenia.|  
|[niestandardowe atrybuty]|Opcjonalne atrybuty.<br /><br /> Określa wartość dla atrybutów specyficzne dla odbiornika identyfikowane przez <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metody dla tego odbiornika. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> jest przykładem atrybut dodatkowe unikatowego dla <xref:System.Diagnostics.DelimitedListTraceListener> klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Dodaje filtr do odbiornika w `Listeners` kolekcję dla źródła śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.|  
|`source`|Określa źródło śledzenia, który inicjuje komunikatów śledzenia.|  
|`listeners`|Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczane z programem .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.  
  
 Jeśli nie określisz `name` atrybut odbiornik śledzenia <xref:System.Diagnostics.TraceListener.Name%2A> właściwość odbiornik śledzenia wartość domyślna to ciąg pusty (""). Jeśli aplikacja ma tylko jeden odbiornik, dodać go bez określenia nazwy i można go usunąć, określając pusty ciąg jako nazwę. Jednakże, jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, dzięki czemu można zidentyfikować i zarządzanie nimi poszczególnych śledzenia słuchaczy w <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekcji.  
  
> [!NOTE]
>  Dodawanie więcej niż jeden odbiornik śledzenia tego samego typu i o takiej samej nazwij skutkuje odbiornik śledzenia tylko jeden tego typu i dodawane do `Listeners` kolekcji. Jednak można programowo dodać wiele odbiorników identyczne do `Listeners` kolekcji.  
  
 Wartość `initializeData` atrybutu zależy od typu tworzenia odbiornika. Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia `initializeData`.  
  
> [!NOTE]
>  Kiedy używasz `initializeData` atrybutu, może wystąpić kompilatora ostrzeżenie "atrybut"initializeData"nie został zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjna klasa bazowa <xref:System.Diagnostics.TraceListener>, który nie rozpoznaje `initializeData` atrybutu. Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornik śledzenia, które ma konstruktora, który przyjmuje parametr.  
  
 W poniższej tabeli przedstawiono detektorów śledzenia, które są dołączone do programu .NET Framework i przedstawiono zalety ich `initializeData` atrybutów.  
  
|Klasa odbiornik śledzenia|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.  Ustaw `initializeData` atrybutu "`true`"do zapisu śledzenia i debugowania danych wyjściowych w strumieniu standard error; ustaw ją "`false`" do zapisu do strumienia wyjścia standardowego.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącej źródło dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`. `textListener` Odbiornika zapisuje dane wyjściowe śledzenia myListener.log pliku.  
  
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
- [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
