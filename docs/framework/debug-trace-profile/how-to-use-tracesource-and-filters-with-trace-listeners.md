---
title: 'Porady: użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia'
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
ms.openlocfilehash: 7d2b9da72ae0b2a5c60eb90da0b56b45634e6e05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181815"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Porady: użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia
Jedną z nowych funkcji w .NET Framework w wersji 2.0 jest ulepszony system śledzenia. Podstawowe założenie pozostaje niezmienione: komunikaty śledzenia są wysyłane za pośrednictwem przełączników do odbiorników, które zgłaszają dane do skojarzonego nośnika wyjściowego. Podstawową różnicą dla wersji 2.0 jest to, że <xref:System.Diagnostics.TraceSource> ślady mogą być inicjowane za pośrednictwem wystąpień klasy. <xref:System.Diagnostics.TraceSource>jest przeznaczony do działania jako ulepszony system śledzenia i może być stosowany <xref:System.Diagnostics.Trace> zamiast <xref:System.Diagnostics.Debug> metod statycznych starszych i klas śledzenia. Znane <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy nadal istnieją, ale zalecaną <xref:System.Diagnostics.TraceSource> praktyką jest użycie klasy do śledzenia.  
  
 W tym temacie opisano <xref:System.Diagnostics.TraceSource> użycie pliku konfiguracji aplikacji w połączeniu z plikiem.  Jest możliwe, choć nie zalecane, <xref:System.Diagnostics.TraceSource> do śledzenia przy użyciu bez użycia pliku konfiguracyjnego. Aby uzyskać informacje na temat śledzenia bez pliku konfiguracyjnego, zobacz [Jak: Tworzenie i inicjowanie źródeł śledzenia](how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Aby utworzyć i zainicjować źródło śledzenia  
  
1. Pierwszym krokiem do instrumentowania aplikacji z śledzenia jest utworzenie źródła śledzenia. W dużych projektach z różnymi składnikami można utworzyć oddzielne źródło śledzenia dla każdego składnika. Zalecaną praktyką jest użycie nazwy aplikacji dla nazwy źródła śledzenia. Ułatwi to oddzielanie różnych śladów. Poniższy kod tworzy nowe`mySource)` źródło śledzenia (`Activity1`i wywołuje metodę ( ), która śledzi zdarzenia.  Komunikaty śledzenia są zapisywane przez domyślny odbiornik śledzenia.  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Aby utworzyć i zainicjować detektory śledzenia i filtry  
  
1. Kod w pierwszej procedurze nie programowo zidentyfikować żadnych detektorów śledzenia lub filtrów. Sam kod powoduje, że komunikaty śledzenia są zapisywane do domyślnego odbiornika śledzenia. Aby skonfigurować określone detektory śledzenia i skojarzone z nimi filtry, należy edytować plik konfiguracyjny odpowiadający nazwie aplikacji. W tym pliku można dodać lub usunąć odbiornika, ustawić właściwości i filtr dla odbiornika lub usunąć odbiorniki. W poniższym przykładzie pliku konfiguracji pokazano, jak zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia, który jest tworzony w poprzedniej procedurze. Oprócz konfigurowania odbiorników śledzenia plik konfiguracyjny tworzy filtry dla obu odbiorników i tworzy przełącznik źródłowy dla źródła śledzenia. Dwie techniki są wyświetlane do dodawania detektorów śledzenia: dodawanie odbiornika bezpośrednio do źródła śledzenia i dodawanie odbiornika do kolekcji odbiorników udostępnionych, a następnie dodanie go według nazwy do źródła śledzenia. Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnych poziomów źródła. Powoduje to, że niektóre wiadomości są zapisywane przez tylko jednego z dwóch odbiorników.  
  
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
  
1. Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w momencie zainicjowania aplikacji. Aby zmienić te ustawienia, należy zmienić plik konfiguracyjny i <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu tej metody. Aplikacja może dynamicznie zmieniać właściwości ustawione przez plik konfiguracyjny, aby zastąpić wszystkie ustawienia określone przez użytkownika.  Na przykład można zapewnić, że wiadomości krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Instrukcje: Tworzenie i inicjowanie źródeł śledzenia](how-to-create-and-initialize-trace-sources.md)
- [Obiekty nasłuchujące śledzenia](trace-listeners.md)
