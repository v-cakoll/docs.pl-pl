---
title: <add>, element dla <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927214"
---
# <a name="add-element-for-sharedlisteners"></a>\<Dodaj element > dla \<sharedListeners >
Dodaje odbiornik do `sharedListeners` kolekcji. `sharedListeners`jest kolekcją odbiorników, które mogą odwoływać się [ \<do > źródłowych](source-element.md) lub [ \<> śledzenia](trace-element.md) .  Domyślnie odbiorniki w `sharedListeners` kolekcji nie są umieszczane `Listeners` w kolekcji. Muszą one być dodawane przez nazwę do [ \<źródła >](source-element.md) lub [ \<> śledzenia](trace-element.md). Nie można uzyskać odbiorników w `sharedListeners` kolekcji w kodzie w czasie wykonywania.  
  
 \<> konfiguracji  
&nbsp;&nbsp;\<> System. Diagnostics  
&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners, element >  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Atrybut wymagany.<br /><br /> Określa nazwę odbiornika, który jest używany do dodawania udostępnionego odbiornika do `Listeners` kolekcji.|  
|`type`|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przesłany do konstruktora dla określonej klasy.|  
|`traceOutputOptions`|Atrybut opcjonalny.<br/><br/>Ciąg reprezentujący co najmniej jeden <xref:System.Diagnostics.TraceOptions> element członkowski wyliczenia wskazujący dane, które mają być zapisywane w danych wyjściowych śledzenia. Wiele elementów jest oddzielonych przecinkami. Wartość domyślna to "Brak".|

### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](filter-element-for-add-for-sharedlisteners.md)|Dodaje filtr do odbiornika w `sharedListeners` kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`sharedListeners`|Kolekcja detektorów, które mogą odwoływać się do każdego elementu źródłowego lub śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczane z .NET Framework pochodzą od <xref:System.Diagnostics.TraceListener> klasy. Wartość `name` atrybutu służy do dodawania udostępnionego odbiornika `Listeners` do kolekcji dla śladu lub źródła śledzenia. Wartość `initializeData` atrybutu zależy od typu tworzonego odbiornika. Nie wszystkie detektory śledzenia wymagają określenia `initializeData`.  
  
> [!NOTE]
> W przypadku korzystania z `initializeData` atrybutu może zostać wyświetlone ostrzeżenie kompilatora "initializeData" nie jest zadeklarowany. " To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy <xref:System.Diagnostics.TraceListener>bazowej, która nie `initializeData` rozpoznaje atrybutu. Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartości ich `initializeData` atrybutów.  
  
|Trace — Klasa odbiornika|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` Wartość<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> dla konstruktora.  Ustaw atrybut na "`true`", aby zapisać dane wyjściowe śledzenia i debugowania do strumienia błędu standardowego; Ustaw dla niego wartość`false`"", aby zapisać w standardowym strumieniu wyjściowym. `initializeData`|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Nazwa pliku, w którym są <xref:System.Diagnostics.DelimitedListTraceListener> zapisywane dane.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.EventSchemaTraceListener> .|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.TextWriterTraceListener> .|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.XmlWriterTraceListener> .|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 `<add>` Poniższy przykład pokazuje, <xref:System.Diagnostics.TextWriterTraceListener> `textListener` jak za pomocą elementów dodać do `sharedListeners` kolekcji.   `textListener`jest dodawany przez nazwę do `Listeners` kolekcji dla źródła `TraceSourceApp`śledzenia. `textListener` Odbiornik zapisuje dane wyjściowe śledzenia do pliku listen. log.  
  
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
- [Obiekty nasłuchujące śledzenie](../../../debug-trace-profile/trace-listeners.md)
