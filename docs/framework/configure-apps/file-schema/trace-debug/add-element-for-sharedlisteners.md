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
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153610"
---
# <a name="add-element-for-sharedlisteners"></a>\<dodaj element> dla \<sharedListeners>
Dodaje odbiornik do `sharedListeners` kolekcji. `sharedListeners`jest zbiorem odbiorników, do których można odwoływać [ \<się>](source-element.md) lub [ \<śledzenia>.](trace-element.md)  Domyślnie odbiorniki w `sharedListeners` kolekcji nie `Listeners` są umieszczane w kolekcji. Należy je dodać według nazwy do [ \<>źródłowego](source-element.md) lub [ \<>śledzenia ](trace-element.md). Nie jest możliwe, aby uzyskać `sharedListeners` odbiorników w kolekcji w kodzie w czasie wykonywania.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**

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
|`name`|Atrybut wymagany.<br /><br /> Określa nazwę odbiornika, który jest używany do dodawania `Listeners` udostępnionego odbiornika do kolekcji.|  
|`type`|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu spełniającego wymagania określone w określaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy.|  
|`traceOutputOptions`|Atrybut opcjonalny.<br/><br/>Reprezentacja ciągu jednego <xref:System.Diagnostics.TraceOptions> lub więcej elementów członkowskich wyliczenia, który wskazuje dane, które mają być zapisywane do danych wyjściowych śledzenia. Wiele elementów jest oddzielonych przecinkami. Wartością domyślną jest "Brak".|

### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>filtra](filter-element-for-add-for-sharedlisteners.md)|Dodaje filtr do odbiornika `sharedListeners` w kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.|  
|`sharedListeners`|Kolekcja odbiorników, do których można odwoływać się do dowolnego źródła lub elementu śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy odbiornika dostarczane z .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy. Wartość atrybutu `name` jest używana do dodawania udostępnionego `Listeners` odbiornika do kolekcji dla śledzenia lub źródła śledzenia. Wartość atrybutu `initializeData` zależy od typu odbiornika, który tworzysz. Nie wszystkie detektory śledzenia `initializeData`wymagają określenia .  
  
> [!NOTE]
> Korzystając z `initializeData` atrybutu, może pojawić się ostrzeżenie kompilatora "Atrybut 'initializeData' nie jest zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są <xref:System.Diagnostics.TraceListener>sprawdzane względem abstrakcyjnej klasy podstawowej, która nie rozpoznaje atrybutu. `initializeData` Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornika śledzenia, które mają konstruktora, który przyjmuje parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone `initializeData` do programu .NET Framework i opisano wartość ich atrybutów.  
  
|Śledzenie klasy detektora|initializeDane wartość atrybutu|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|Wartość `useErrorStream` konstruktora. <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>  Ustaw `initializeData` atrybut na`true`" ", aby zapisać śledzenie i debugowanie danych wyjściowych do standardowego strumienia błędów; ustawić go`false`na " ", aby zapisać do standardowego strumienia wyjściowego.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Nazwa pliku, do <xref:System.Diagnostics.DelimitedListTraceListener> który zapisuje się.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<add>` pokazano, <xref:System.Diagnostics.TextWriterTraceListener> `textListener` jak `sharedListeners` używać elementów, aby dodać do kolekcji.   `textListener`jest dodawany według `Listeners` nazwy do `TraceSourceApp`kolekcji dla źródła śledzenia . Odbiornik `textListener` zapisuje dane wyjściowe śledzenia do pliku myListener.log.  
  
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
