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
ms.openlocfilehash: 116a9633d16b8dd36c82f07a8e727f6f9f98f0ee
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088964"
---
# <a name="add-element-for-sharedlisteners"></a>\<dodać > elementu \<sharedListeners >
Dodaje odbiornik do kolekcji `sharedListeners`. `sharedListeners` jest kolekcją odbiorników, które mogą odwoływać się do [\<źródła >](source-element.md) lub [\<śledzenia >](trace-element.md) .  Domyślnie odbiorniki w kolekcji `sharedListeners` nie są umieszczane w kolekcji `Listeners`. Muszą być dodawane według nazwy do [> źródła\<](source-element.md) lub [\<śledzenia >](trace-element.md). Nie można uzyskać odbiorników w kolekcji `sharedListeners` w kodzie w czasie wykonywania.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sharedListeners >** ](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**

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
|`name`|Atrybut wymagany.<br /><br /> Określa nazwę odbiornika, który jest używany do dodawania udostępnionego odbiornika do kolekcji `Listeners`.|  
|`type`|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przesłany do konstruktora dla określonej klasy.|  
|`traceOutputOptions`|Atrybut opcjonalny.<br/><br/>Ciąg reprezentujący co najmniej jeden <xref:System.Diagnostics.TraceOptions> element członkowski wyliczenia wskazujący dane, które mają być zapisywane w danych wyjściowych śledzenia. Wiele elementów jest oddzielonych przecinkami. Wartość domyślna to "Brak".|

### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Filtr \<](filter-element-for-add-for-sharedlisteners.md)|Dodaje filtr do odbiornika w kolekcji `sharedListeners`.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.|  
|`sharedListeners`|Kolekcja detektorów, które mogą odwoływać się do każdego elementu źródłowego lub śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczane z .NET Framework pochodzą z klasy <xref:System.Diagnostics.TraceListener>. Wartość atrybutu `name` jest używana do dodawania udostępnionego odbiornika do kolekcji `Listeners` dla śladu lub źródła śledzenia. Wartość atrybutu `initializeData` zależy od typu tworzonego odbiornika. Nie wszystkie detektory śledzenia wymagają określenia `initializeData`.  
  
> [!NOTE]
> W przypadku korzystania z atrybutu `initializeData` można uzyskać Ostrzeżenie kompilatora "atrybut" initializeData "nie jest zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy bazowej <xref:System.Diagnostics.TraceListener>, która nie rozpoznaje atrybutu `initializeData`. Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartości atrybutów `initializeData`.  
  
|Trace — Klasa odbiornika|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|Wartość `useErrorStream` konstruktora <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.  Ustaw atrybut `initializeData` na "`true`", aby zapisać dane wyjściowe śledzenia i debugowania do strumienia błędu standardowego; Ustaw dla niego wartość "`false`", aby zapisać w standardowym strumieniu wyjściowym.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Nazwa pliku, do którego <xref:System.Diagnostics.DelimitedListTraceListener> zapisu.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje dane.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym <xref:System.Diagnostics.TextWriterTraceListener> zapisuje dane.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Nazwa pliku, w którym <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje dane.|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać elementów `<add>`, aby dodać `textListener` <xref:System.Diagnostics.TextWriterTraceListener>do kolekcji `sharedListeners`.   `textListener` jest dodawany przez nazwę do kolekcji `Listeners` `TraceSourceApp`źródła śledzenia. Odbiornik `textListener` zapisuje dane wyjściowe śledzenia do pliku listen. log.  
  
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
