---
title: '&lt;Dodaj&gt; elementu &lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 93fdb548882422634e1d2456b4d37f434b278f8d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216537"
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a>&lt;Dodaj&gt; elementu &lt;sharedListeners&gt;
Dodaje odbiornik do `sharedListeners` kolekcji. `sharedListeners` wszystkie to kolekcja obiektów nasłuchujących [ \<źródło >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) lub [ \<śledzenia >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) może odwoływać się.  Domyślnie słuchaczy w `sharedListeners` kolekcji nie są umieszczane w `Listeners` kolekcji. Musi zostać dodany przez nazwę, aby [ \<źródło >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) lub [ \<śledzenia >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md). Nie jest możliwe do pobrania odbiorniki w `sharedListeners` kolekcji w kodzie w czasie wykonywania.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<sharedListeners > Element  
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
|`name`|Atrybut wymagany.<br /><br /> Określa nazwę odbiornik, który służy do dodawania udostępnionych odbiornika do `Listeners` kolekcji.|  
|`type`|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Dodaje filtr do odbiornika w `sharedListeners` kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.|  
|`sharedListeners`|Kolekcja obiektów nasłuchujących dowolnego źródła i elementu śledzenia można odwoływać się do.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczane z programem .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy. Wartość `name` atrybut służy do dodawania udostępnionych odbiornika do `Listeners` zbierania śladu lub źródła śledzenia. Wartość `initializeData` atrybutu zależy od typu tworzenia odbiornika. Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia `initializeData`.  
  
> [!NOTE]
>  Kiedy używasz `initializeData` atrybutu, może wystąpić kompilatora ostrzeżenie "atrybut"initializeData"nie został zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjna klasa bazowa <xref:System.Diagnostics.TraceListener>, który nie rozpoznaje `initializeData` atrybutu. Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornik śledzenia, które ma konstruktora, który przyjmuje parametr.  
  
 W poniższej tabeli przedstawiono detektorów śledzenia, które są dołączone do programu .NET Framework i przedstawiono zalety ich `initializeData` atrybutów.  
  
|Klasa odbiornik śledzenia|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.  Ustaw `initializeData` atrybutu "`true`"do zapisu śledzenia i debugowania danych wyjściowych w strumieniu standard error; ustaw ją "`false`" do zapisu do strumienia wyjścia standardowego.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącej źródło dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Nazwę pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<add>` elementy do dodania <xref:System.Diagnostics.TextWriterTraceListener> `textListener` do `sharedListeners` kolekcji.   `textListener` jest dodawany przez nazwę, aby `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`. `textListener` Odbiornika zapisuje dane wyjściowe śledzenia myListener.log pliku.  
  
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
