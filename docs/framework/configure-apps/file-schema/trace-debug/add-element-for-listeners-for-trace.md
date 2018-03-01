---
title: "&lt;Dodaj&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: eb624052c3638cb49abe143ebd4173a5ee85a054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Dodaj&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;
Dodaje odbiornika do **odbiorników** kolekcji.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<śledzenia >  
\<obiekty nasłuchujące >  
\<Dodaj >  
  
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
|**Typ**|Atrybut wymagany.<br /><br /> Określa typ odbiornika. Należy użyć ciągu, który spełnia wymagania określone w [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData —**|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla określonej klasy.|  
|**Nazwa**|Atrybut opcjonalny.<br /><br /> Określa nazwę odbiornika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Dodaje filtr do odbiornika w `Listeners` kolekcji dla śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`listeners`|Określa odbiornika zbiera, magazynów i kieruje komunikaty. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`system.diagnostics`|Określa element root dla sekcji konfiguracji ASP.NET.|  
|`trace`|Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klasy udostępnianie takie same **odbiorników** kolekcji. Jeśli obiekt odbiornika zostanie dodany do kolekcji w jednym z tych klas, inne klasy używa tego samego odbiornika. Klasy odbiornika pochodzić od <xref:System.Diagnostics.TraceListener>.  
  
 Jeśli nie określisz `name` atrybutu obiektu nasłuchującego śledzenia <xref:System.Diagnostics.TraceListener.Name%2A> domyślnych ustawień odbiornika śledzenia na ciąg pusty (""). Jeśli aplikacja ma tylko jeden odbiornik, można dodać go bez określania nazwy i usuń go przez określenie pustego ciągu w nazwie. Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę każdego nasłuchującego śledzenia, który służy do identyfikowania i zarządzania nim obiekty nasłuchujące śledzenia poszczególnych w <xref:System.Diagnostics.Debug.Listeners%2A> i <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji.  
  
> [!NOTE]
>  Dodanie więcej niż jeden odbiornik śledzenia tego samego typu i o tej samej nazwie wyniki śledzenia tylko jednego odbiornika tego typu i nazwy dodawane do `Listeners` kolekcji. Jednak programowo można dodać wiele odbiorników identyczne do `Listeners` kolekcji.  
  
 Wartość **initializeData —** atrybutu zależy od typu tworzenia odbiornika. Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia **initializeData —**.  
  
> [!NOTE]
>  Jeśli używasz `initializeData` atrybutu, mogą wystąpić kompilatora ostrzeżenie "atrybutu"initializeData —"nie został zadeklarowany." To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są sprawdzane w abstrakcyjnej klasy podstawowej <xref:System.Diagnostics.TraceListener>, którego nie rozpoznaje `initializeData` atrybutu. Zazwyczaj można zignorować to ostrzeżenie implementacji odbiornika śledzenia, które mają Konstruktor, który przyjmuje parametr.  
  
 Poniższa tabela przedstawia obiekty nasłuchujące śledzenia, które są dołączone do programu .NET Framework oraz opis wartość ich **initializeData —** atrybutów.  
  
|Klasa odbiornika śledzenia|initializeData — wartość atrybutu|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.  Ustaw `initializeData` atrybutu "`true`" zapisu śledzenia i debugowania dane wyjściowe do <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" do zapisu <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nazwa nazwę istniejącego źródła dziennika zdarzeń.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie  **\<Dodaj >** elementy do dodania odbiorniki `MyListener` i `MyEventListener` do **odbiorników** kolekcji. `MyListener`Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku. `MyEventListener`tworzy wpis w dzienniku zdarzeń.  
  
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
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Obiekty nasłuchujące śledzenie](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
