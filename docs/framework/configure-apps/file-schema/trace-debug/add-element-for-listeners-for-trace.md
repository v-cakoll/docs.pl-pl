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
ms.openlocfilehash: d4ff919991ab1505b2845a225706d32cc1e57d0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920569"
---
# <a name="add-element-for-listeners-for-trace"></a>\<Dodaj > element dla \<odbiorników \<> śledzenia >
Dodaje odbiornik do kolekcji **odbiorników** .  
  
 \<> konfiguracji  
\<system.diagnostics>  
\<> śledzenia  
\<> odbiorników  
\<add>  
  
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
|**type**|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Atrybut opcjonalny.<br /><br /> Ciąg przesłany do konstruktora dla określonej klasy.|  
|**name**|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](filter-element-for-add-for-listeners-for-trace.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji w celu śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`listeners`|Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty. Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`system.diagnostics`|Określa element główny dla sekcji konfiguracji ASP.NET.|  
|`trace`|Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> współużytkują tę samą kolekcję detektorów. Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, inna Klasa używa tego samego odbiornika. Klasy odbiornika pochodzą od <xref:System.Diagnostics.TraceListener>.  
  
 Jeśli nie określisz `name` atrybutu odbiornika śledzenia, wartość <xref:System.Diagnostics.TraceListener.Name%2A> ustawienia odbiornik śledzenia domyślnie będzie pustym ciągiem (""). Jeśli aplikacja ma tylko jeden odbiornik, możesz ją dodać bez określania nazwy i usunąć ją, określając pusty ciąg w polu Nazwa. Jeśli jednak aplikacja ma więcej niż jeden odbiornik, należy określić unikatowe nazwy dla każdego odbiornika śledzenia, co pozwala identyfikować poszczególne detektory śledzenia i zarządzać nimi w ramach <xref:System.Diagnostics.Debug.Listeners%2A> kolekcji i. <xref:System.Diagnostics.Trace.Listeners%2A>  
  
> [!NOTE]
> Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i z tą samą nazwą powoduje tylko jeden odbiornik śledzenia tego typu i nazwę dodawane do `Listeners` kolekcji. Można jednak programowo dodać wiele identycznych odbiorników do `Listeners` kolekcji.  
  
 Wartość atrybutu **initializeData** zależy od typu tworzonego odbiornika. Nie wszystkie detektory śledzenia wymagają określenia **initializeData**.  
  
> [!NOTE]
> W przypadku korzystania z `initializeData` atrybutu może zostać wyświetlone ostrzeżenie kompilatora "initializeData" nie jest zadeklarowany. " To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy <xref:System.Diagnostics.TraceListener>bazowej, która nie `initializeData` rozpoznaje atrybutu. Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.  
  
 W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartość ich atrybutów **initializeData** .  
  
|Trace — Klasa odbiornika|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Wartość<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> dla konstruktora.  Ustaw atrybut na "`true`", aby zapisać dane wyjściowe śledzenia i debugowania <xref:System.Console.Error%2A?displayProperty=nameWithType>do; `initializeData` "`false`" do <xref:System.Console.Out%2A?displayProperty=nameWithType>zapisu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym są <xref:System.Diagnostics.DelimitedListTraceListener> zapisywane dane.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.EventSchemaTraceListener> .|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.TextWriterTraceListener> .|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.XmlWriterTraceListener> .|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak za pomocą  **\<Dodawanie >** elementów dodać `MyListener` odbiorniki i `MyEventListener` do kolekcji **odbiorników** . `MyListener`tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `MyEventListener`tworzy wpis w dzienniku zdarzeń.  
  
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
- [Obiekty nasłuchujące śledzenie](../../../debug-trace-profile/trace-listeners.md)
