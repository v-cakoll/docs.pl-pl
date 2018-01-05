---
title: "&lt;Dodaj&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 86177010d8ed70302b51ec9c416a3295009e7394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Dodaj&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;
Dodaje odbiornika do `Listeners` kolekcji źródła śledzenia.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<źródeł >  
\<źródło >  
\<obiekty nasłuchujące >  
\<Dodaj >  
  
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
|`type`|Wymagany atrybut, chyba że odwołujesz odbiornika w `sharedListeners` kolekcji, w których wielkość liter jest konieczne tylko odwołuje się do niego według nazwy (zobacz [przykład](#example)).<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy. A <xref:System.Configuration.ConfigurationException> jest generowany, jeśli klasa nie ma konstruktora przyjmującego ciąg.|  
|`name`|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
|`traceOutputOptions`|Atrybut opcjonalny.<br /><br /> Określa <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> wartości właściwości dla obiektu nasłuchującego śledzenia.|  
|[atrybuty niestandardowe]|Opcjonalne atrybuty.<br /><br /> Określa wartość atrybuty specyficzne dla odbiornika identyfikowane przez <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metody dla tego odbiornika. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>Przykładem dodatkowe atrybutu jest unikatowa dla <xref:System.Diagnostics.DelimitedListTraceListener> klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji źródła śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.|  
|`source`|Określa źródło śledzenia, który inicjuje śledzenia wiadomości.|  
|`listeners`|Określa nasłuchujących zbierania, przechowywania i kierowania wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczone z programu .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.  
  
 Jeśli nie określisz `name` atrybutu obiektu nasłuchującego śledzenia <xref:System.Diagnostics.TraceListener.Name%2A> właściwości obiektu nasłuchującego śledzenia domyślnie ciąg pusty (""). Jeśli aplikacja ma tylko jeden odbiornik, dodaj go bez określania nazwy i usuń go przez określenie pustego ciągu w nazwie. Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, który służy do identyfikowania i zarządzania nim obiekty nasłuchujące śledzenia poszczególnych w <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekcji.  
  
> [!NOTE]
>  Dodanie więcej niż jeden odbiornik śledzenia tego samego typu i o tej samej nazwie wyniki śledzenia tylko jednego odbiornika tego typu i nazwy dodawane do `Listeners` kolekcji. Jednak programowo można dodać wiele odbiorników identyczne do `Listeners` kolekcji.  
  
 Wartość `initializeData` atrybutu zależy od typu tworzenia odbiornika. Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia `initializeData`.  
  
> [!NOTE]
>  Jeśli używasz `initializeData` atrybutu, mogą wystąpić kompilatora ostrzeżenie "atrybutu"initializeData —"nie został zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są sprawdzane w abstrakcyjnej klasy podstawowej <xref:System.Diagnostics.TraceListener>, którego nie rozpoznaje `initializeData` atrybutu. Zazwyczaj można zignorować to ostrzeżenie implementacji odbiornika śledzenia, które mają Konstruktor, który przyjmuje parametr.  
  
 Poniższa tabela przedstawia obiekty nasłuchujące śledzenia, które są dołączone do programu .NET Framework oraz opis wartość ich `initializeData` atrybutów.  
  
|Klasa odbiornika śledzenia|initializeData — wartość atrybutu|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.  Ustaw `initializeData` atrybutu "`true`"zapisu śledzenia i debugowania dane wyjściowe do Standardowy strumień błędów; ustaw go "`false`" można zapisać do standardowego strumienia wyjściowego.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącej źródło dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji źródła śledzenia `TraceSourceApp`. `textListener` Odbiornika zapisuje dane wyjściowe śledzenia myListener.log pliku.  
  
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
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
