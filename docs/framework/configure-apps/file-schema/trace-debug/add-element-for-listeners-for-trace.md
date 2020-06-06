---
title: <add>Element dla <listeners> elementu<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153675"
---
# <a name="add-element-for-listeners-for-trace"></a>\<add>Element dla \<listeners> elementu\<trace>
Dodaje odbiornik do kolekcji **odbiorników** .  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

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
|**Wprowadź**|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Atrybut opcjonalny.<br /><br /> Ciąg przesłany do konstruktora dla określonej klasy.|  
|**Nazwij**|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji w celu śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`listeners`|Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty. Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`system.diagnostics`|Określa element główny dla sekcji konfiguracji ASP.NET.|  
|`trace`|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Diagnostics.Debug>Klasy i <xref:System.Diagnostics.Trace> współużytkują tę samą kolekcję **detektorów** . Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, inna Klasa używa tego samego odbiornika. Klasy odbiornika pochodzą od <xref:System.Diagnostics.TraceListener> .  
  
 Jeśli nie określisz `name` atrybutu odbiornika śledzenia, wartość <xref:System.Diagnostics.TraceListener.Name%2A> Ustawienia odbiornik śledzenia domyślnie będzie pustym ciągiem (""). Jeśli aplikacja ma tylko jeden odbiornik, możesz ją dodać bez określania nazwy i usunąć ją, określając pusty ciąg w polu Nazwa. Jeśli jednak aplikacja ma więcej niż jeden odbiornik, należy określić unikatowe nazwy dla każdego odbiornika śledzenia, co pozwala identyfikować poszczególne detektory śledzenia i zarządzać nimi w ramach <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji i.  
  
> [!NOTE]
> Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i z tą samą nazwą powoduje tylko jeden odbiornik śledzenia tego typu i nazwę dodawane do `Listeners` kolekcji. Można jednak programowo dodać wiele identycznych odbiorników do `Listeners` kolekcji.  
  
 Wartość atrybutu **initializeData** zależy od typu tworzonego odbiornika. Nie wszystkie detektory śledzenia wymagają określenia **initializeData**.  
  
> [!NOTE]
> W przypadku korzystania z `initializeData` atrybutu może zostać wyświetlone ostrzeżenie kompilatora "initializeData" nie jest zadeklarowany. " To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy bazowej <xref:System.Diagnostics.TraceListener> , która nie rozpoznaje `initializeData` atrybutu. Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartość ich atrybutów **initializeData** .  
  
|Trace — Klasa odbiornika|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`Wartość dla <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.  Ustaw `initializeData` atrybut na " `true` ", aby zapisać dane wyjściowe śledzenia i debugowania do <xref:System.Console.Error%2A?displayProperty=nameWithType> ; " `false` " do zapisu <xref:System.Console.Out%2A?displayProperty=nameWithType> .|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym są <xref:System.Diagnostics.DelimitedListTraceListener> zapisywane dane.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.EventSchemaTraceListener> .|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.TextWriterTraceListener> .|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.XmlWriterTraceListener> .|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać **\<add>** elementów do dodawania odbiorników `MyListener` i `MyEventListener` do kolekcji **odbiorników** . `MyListener`tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `MyEventListener`tworzy wpis w dzienniku zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [Schemat ustawień śledzenia i debugowania](index.md)
- [Obiekty nasłuchujące śledzenia](../../../debug-trace-profile/trace-listeners.md)
