---
title: <add> Element <listeners> dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ba0ffc4f95b9af7fcd319068501ce0bb9714c2ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089585"
---
# <a name="add-element-for-listeners-for-trace"></a>\<Dodaj >, Element dla \<odbiorników > dla \<śledzenia >
Dodaje odbiornik do **odbiorników** kolekcji.  
  
 \<Konfiguracja >  
\<system.diagnostics>  
\<trace>  
\<listeners>  
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
|**type**|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy.|  
|**Nazwa**|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji dla śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`listeners`|Określa odbiornik, który zbiera, magazynów i przekazuje komunikaty. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`system.diagnostics`|Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.|  
|`trace`|Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klasy współużytkować ten sam **odbiorników** kolekcji. Jeśli dodasz obiektu odbiornika do kolekcji w jednym z tych klas, inne klasy używa tego samego odbiornika. Klasy odbiornika pochodzić od <xref:System.Diagnostics.TraceListener>.  
  
 Jeśli nie określisz `name` atrybut odbiornik śledzenia <xref:System.Diagnostics.TraceListener.Name%2A> domyślnych ustawień odbiornika śledzenia na ciąg pusty (""). Jeśli aplikacja ma tylko jeden odbiornik, możesz dodać go bez określenia nazwy i usuń go, określając pusty ciąg jako nazwę. Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatowej nazwy dla każdego odbiornik śledzenia, dzięki czemu można zidentyfikować i zarządzanie nimi poszczególnych śledzenia słuchaczy w ramach <xref:System.Diagnostics.Debug.Listeners%2A> i <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji.  
  
> [!NOTE]
>  Dodawanie więcej niż jeden odbiornik śledzenia tego samego typu i o takiej samej nazwij skutkuje odbiornik śledzenia tylko jeden tego typu i dodawane do `Listeners` kolekcji. Jednak można programowo dodać wiele odbiorników identyczne do `Listeners` kolekcji.  
  
 Wartość **initializeData** atrybutu zależy od typu tworzenia odbiornika. Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia **initializeData**.  
  
> [!NOTE]
>  Kiedy używasz `initializeData` atrybutu, może wystąpić kompilatora ostrzeżenie "atrybut"initializeData"nie został zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjna klasa bazowa <xref:System.Diagnostics.TraceListener>, który nie rozpoznaje `initializeData` atrybutu. Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornik śledzenia, które ma konstruktora, który przyjmuje parametr.  
  
 W poniższej tabeli przedstawiono detektorów śledzenia, które są dołączone do programu .NET Framework i przedstawiono zalety ich **initializeData** atrybutów.  
  
|Klasa odbiornik śledzenia|wartość atrybutu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.  Ustaw `initializeData` atrybutu "`true`" do zapisu, śledzenia i debugowania dane wyjściowe do <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" do zapisu <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa Nazwa istniejące źródło dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwę pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać  **\<Dodaj >** elementy do dodania odbiorniki `MyListener` i `MyEventListener` do **odbiorników** kolekcji. `MyListener` Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `MyEventListener` tworzy wpis w dzienniku zdarzeń.  
  
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
- [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
