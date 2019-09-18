---
title: 'Instrukcje: Użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia'
ms.date: 03/30/2017
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1e214266b66f390fecffe802270a4181a6d7a7f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052686"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Instrukcje: Użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia
Jedną z nowych funkcji w .NET Framework wersja 2,0 to udoskonalony system śledzenia. Podstawowa lokalna jest niezmieniona: komunikaty śledzenia są wysyłane przez przełączniki do odbiorników, które raportują dane na skojarzonym nośniku wyjściowym. Podstawową różnicą w wersji 2,0 jest to, że ślady mogą być inicjowane <xref:System.Diagnostics.TraceSource> za pomocą wystąpień klasy. <xref:System.Diagnostics.TraceSource>jest przeznaczony do działania jako udoskonalony system śledzenia i może być używany zamiast metod statycznych starszych <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> śledzenia klas. Znane i <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> podobne klasy nadal istnieją, ale zalecane jest użycie <xref:System.Diagnostics.TraceSource> klasy do śledzenia.  
  
 W tym temacie opisano sposób <xref:System.Diagnostics.TraceSource> użycia programu w połączeniu z plikiem konfiguracji aplikacji.  Jest to możliwe, chociaż nie jest to zalecane, do śledzenia <xref:System.Diagnostics.TraceSource> przy użyciu a bez użycia pliku konfiguracji. Informacje dotyczące śledzenia bez pliku konfiguracji znajdują się w [temacie How to: Utwórz i zainicjuj źródła](how-to-create-and-initialize-trace-sources.md)śledzenia.  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Aby utworzyć i zainicjować Źródło śledzenia  
  
1. Pierwszym krokiem do Instrumentacji aplikacji przy użyciu funkcji śledzenia jest utworzenie źródła śledzenia. W dużych projektach z różnymi składnikami można utworzyć oddzielne źródło śledzenia dla każdego składnika. Zalecanym sposobem jest użycie nazwy aplikacji dla nazwy źródła śledzenia. Ułatwi to zachowanie różnych śladów. Poniższy kod tworzy nowe źródło śledzenia (`mySource)` i wywołuje metodę (`Activity1`), która śledzi zdarzenia.  Komunikaty śledzenia są zapisywane przez domyślny odbiornik śledzenia.  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Aby tworzyć i inicjować detektory i filtry śledzenia  
  
1. Kod w pierwszej procedurze nie identyfikuje programowo żadnych detektorów ani filtrów śledzenia. Sam kod skutkuje zapisaniem komunikatów śledzenia w domyślnym odbiorniku śledzenia. Aby skonfigurować określone detektory śledzenia i powiązane z nimi filtry, należy edytować plik konfiguracji, który odnosi się do nazwy aplikacji. W tym pliku można dodać lub usunąć odbiornik, ustawić właściwości i filtr dla odbiornika lub usunąć detektory. Poniższy przykład pliku konfiguracji pokazuje, jak zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia tekstu składnika zapisywania dla źródła śledzenia, które zostało utworzone w poprzedniej procedurze. Oprócz konfigurowania detektorów śledzenia, plik konfiguracji tworzy filtry dla obu odbiorników i tworzy przełącznik źródła dla źródła śledzenia. Dwie techniki są pokazane w przypadku dodawania detektorów śledzenia: dodanie odbiornika bezpośrednio do źródła śledzenia i dodanie odbiornika do kolekcji udostępnionych odbiorników, a następnie dodanie go według nazwy do źródła śledzenia. Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnymi poziomami źródła. Powoduje to, że niektóre komunikaty są zapisywane tylko przez jeden z dwóch odbiorników.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Aby zmienić poziom, na którym odbiornik zapisuje komunikat śledzenia  
  
1. Plik konfiguracji inicjuje ustawienia dla źródła śledzenia w momencie zainicjowania aplikacji. Aby zmienić te ustawienia, należy zmienić plik konfiguracji i ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody. Aplikacja może dynamicznie zmieniać właściwości ustawiane przez plik konfiguracji w celu zastąpienia wszelkich ustawień określonych przez użytkownika.  Na przykład możesz chcieć zapewnić, że komunikaty krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified   
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =   
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures   
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners   
                // for all event types. This statement will override   
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,   
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,   
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Instrukcje: Tworzenie i inicjowanie źródeł śledzenia](how-to-create-and-initialize-trace-sources.md)
- [Obiekty nasłuchujące śledzenie](trace-listeners.md)
