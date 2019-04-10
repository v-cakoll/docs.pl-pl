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
ms.openlocfilehash: 6805385ec21deb8748354647ab0f09b3a51353fa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338582"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Instrukcje: Użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia
Jedną z nowych funkcji programu .NET Framework w wersji 2.0 to system rozszerzone śledzenie. Podstawowe założenia pozostaje niezmieniony: komunikaty śledzenia są wysyłane za pośrednictwem przełączników do odbiorników, które wysyłają raporty danych średni skojarzone dane wyjściowe. Główną różnicą w wersji 2.0 to, że ślady mogą być inicjowane za pośrednictwem wystąpień <xref:System.Diagnostics.TraceSource> klasy. <xref:System.Diagnostics.TraceSource> jest przeznaczony do działania jako system rozszerzone śledzenie i mogą być używane zamiast metod statycznych starszej wersji <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy śledzenia. Znanej <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy nadal istnieje, ale zalecaną praktyką jest użycie <xref:System.Diagnostics.TraceSource> klasy do śledzenia.  
  
 W tym temacie opisano korzystanie z <xref:System.Diagnostics.TraceSource> połączone z pliku konfiguracji aplikacji.  Jest to możliwe, chociaż nie jest to zalecane, do śledzenia przy użyciu <xref:System.Diagnostics.TraceSource> bez użycia pliku konfiguracji. Aby uzyskać informacji na temat śledzenia bez pliku konfiguracji, zobacz [jak: Tworzenie i Inicjowanie źródeł śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Aby utworzyć i zainicjować źródła śledzenia  
  
1. Pierwszym krokiem do instrumentacji aplikacji z włączonym śledzeniem jest utworzyć źródła śledzenia. W dużych projektów z różnych składników można utworzyć źródła śledzenia osobne dla każdego składnika. Zaleca się użycie nazwy aplikacji dla nazwy źródła śledzenia. Ułatwi do zachowania ich odrębności różnych śledzenia. Poniższy kod tworzy nowe źródło śledzenia (`mySource)` i wywołuje metodę (`Activity1`) zapisująca zdarzenia.  Komunikaty śledzenia są zapisywane przez odbiornik śledzenia domyślnego.  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Aby utworzyć i zainicjować odbiorniki śledzenia i filtry  
  
1. Kod w pierwszej procedurze nie programowo zidentyfikować wszystkie obiekty nasłuchujące śledzenia lub filtrów. Kod samodzielnie powoduje komunikaty śledzenia zapisywana odbiornik śledzenia domyślnego. Aby skonfigurować detektorów śledzenia określonych i ich skojarzone filtry, Edytuj plik konfiguracyjny, który odpowiada nazwie aplikacji. W tym pliku możesz dodać lub usunąć odbiornik, ustawianie właściwości i filtr dla odbiornika lub usunąć odbiorników. W poniższym przykładzie plik konfiguracji pokazuje, jak zainicjować detektor śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia utworzonego w poprzedniej procedurze. Poza skonfigurowaniem detektorów śledzenia, plik konfiguracyjny tworzy filtry dla obu detektorów oraz tworzy przełącznik źródła dla źródła śledzenia. Do dodawania detektorów śledzenia pokazano dwie techniki: dodanie detektora bezpośrednio do źródła śledzenia i dodanie detektora do kolekcji współdzielonych detektorów, a następnie dodanie go według nazwy do źródła śledzenia. Filtry określone dla obu detektorów są inicjowane z różnymi poziomami źródła. Skutkuje to pewne komunikaty są zapisywane przez tylko jeden z dwóch detektorów.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Aby zmienić poziom, jaką odbiornik zapisuje komunikat śledzenia  
  
1. Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w czasie, w których aplikacja została zainicjowany. Się zmiany tych ustawień należy zmienić plik konfiguracji i ponownie uruchom aplikację lub programowo odświeżyć aplikacji przy użyciu <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody. Aplikacja można dynamicznie zmieniać właściwości ustawione w pliku konfiguracyjnym, aby zastąpić wszelkie ustawienia określone przez użytkownika.  Na przykład możesz chcieć zapewnić, komunikatów krytycznych, są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.  
  
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
- [Instrukcje: Tworzenie i inicjowanie źródeł śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [Obiekty nasłuchujące śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md)
