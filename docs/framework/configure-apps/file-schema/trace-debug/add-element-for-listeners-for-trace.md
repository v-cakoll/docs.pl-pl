---
title: <add>Element <listeners> dla<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153675"
---
# <a name="add-element-for-listeners-for-trace"></a>\<dodaj element> dla \<> dla> \<śledzenia
Dodaje odbiornik do kolekcji **Odbiorniki.**  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**

## <a name="syntax"></a>Składnia  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Typu**|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu spełniającego wymagania określone w określaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**Initializedata**|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy.|  
|**Nazwa**|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>filtra](filter-element-for-add-for-listeners-for-trace.md)|Dodaje filtr do odbiornika `Listeners` w kolekcji dla śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`listeners`|Określa odbiornik, który zbiera, przechowuje i kieruje wiadomości. Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`system.diagnostics`|Określa element główny sekcji konfiguracji ASP.NET.|  
|`trace`|Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 I <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> klasy współużytkuje tę samą kolekcję **odbiorników.** Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, druga klasa używa tego samego odbiornika. Klasy odbiornika pochodzą z <xref:System.Diagnostics.TraceListener>.  
  
 Jeśli nie określisz `name` atrybutu odbiornika śledzenia, <xref:System.Diagnostics.TraceListener.Name%2A> odbiornik śledzenia domyślnie pusty ciąg (""). Jeśli aplikacja ma tylko jeden odbiornik, można dodać go bez określania nazwy i usunąć go, określając pusty ciąg dla nazwy. Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatowe nazwy dla każdego odbiornika śledzenia, <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> co pozwala na identyfikowanie i zarządzanie poszczególnych odbiorników śledzenia w ramach i kolekcji.  
  
> [!NOTE]
> Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i o tej samej nazwie powoduje `Listeners` tylko jeden odbiornik śledzenia tego typu i nazwy dodawane do kolekcji. Jednak programowo można dodać wiele identycznych `Listeners` odbiorników do kolekcji.  
  
 Wartość atrybutu **initializeData** zależy od typu odbiornika, który tworzysz. Nie wszystkie detektory śledzenia wymagają określenia **initializeData**.  
  
> [!NOTE]
> Korzystając z `initializeData` atrybutu, może pojawić się ostrzeżenie kompilatora "Atrybut 'initializeData' nie jest zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są <xref:System.Diagnostics.TraceListener>sprawdzane względem abstrakcyjnej klasy podstawowej, która nie rozpoznaje atrybutu. `initializeData` Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornika śledzenia, które mają konstruktora, który przyjmuje parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do programu .NET Framework i opisano wartość ich atrybutów **initializeData.**  
  
|Śledzenie klasy detektora|initializeDane wartość atrybutu|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Wartość `useErrorStream` konstruktora. <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>  Ustaw `initializeData` atrybut na`true`" ", aby zapisać śledzenie <xref:System.Console.Error%2A?displayProperty=nameWithType>i debugowanie danych wyjściowych ; "`false`", aby <xref:System.Console.Out%2A?displayProperty=nameWithType>napisać do .|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku, do <xref:System.Diagnostics.DelimitedListTraceListener> który zapisuje się.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa nazwy istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie ** \<** pokazano, jak używać dodaj `MyListener`>`MyEventListener` elementów, aby dodać odbiorniki i **odbiorników** kolekcji. `MyListener`tworzy plik `MyListener.log` wywoływany i zapisuje dane wyjściowe do pliku. `MyEventListener`tworzy wpis w dzienniku zdarzeń.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
