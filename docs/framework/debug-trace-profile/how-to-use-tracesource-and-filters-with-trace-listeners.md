---
title: "Porady: użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b557a9f9f462df2d1afe6d6b61871e0e9f40174
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Porady: użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia
Jedną z nowych funkcji w programie .NET Framework w wersji 2.0 to system rozszerzone śledzenie. Niezmieniona podstawowe lokalnych: śledzenie komunikaty są wysyłane za pośrednictwem przełączników do odbiorników, których dane raportu na średni skojarzone dane wyjściowe. Główną różnicą w wersji 2.0 jest można zainicjować za pomocą wystąpienia śladów <xref:System.Diagnostics.TraceSource> klasy. <xref:System.Diagnostics.TraceSource>jest przeznaczony do działania jako system rozszerzone śledzenie i można użyć zamiast metod statycznych starszej <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy śledzenia. Znanych <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy nadal istnieje, ale zalecaną praktyką jest użycie <xref:System.Diagnostics.TraceSource> klasy śledzenia.  
  
 W tym temacie opisano stosowania <xref:System.Diagnostics.TraceSource> połączone z pliku konfiguracji aplikacji.  Jest to możliwe, chociaż nie jest to zalecane, aby za pomocą śledzenia <xref:System.Diagnostics.TraceSource> bez użycia pliku konfiguracji. Aby uzyskać informacje na śledzenie bez pliku konfiguracji, zobacz [porady: tworzenie i Inicjowanie źródeł śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Aby utworzyć i zainicjować źródła śledzenia  
  
1.  Pierwszym krokiem do instrumentacji aplikacji z włączonym śledzeniem jest można utworzyć źródła śledzenia. W dużych projektów z różnych składników można utworzyć źródła śledzenia osobne dla każdego składnika. Zalecaną praktyką jest użycie nazwy aplikacji dla nazwy źródła śledzenia. Ułatwi być oddzielone różne dane śledzenia. Poniższy kod tworzy nowe źródło śledzenia (`mySource)` i wywołuje metodę (`Activity1`) która śledzi zdarzenia.  Wiadomości śledzenia są zapisywane przez odbiornik śledzenia domyślnego.  
  
    ```  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Tworzenie i Inicjowanie obiektów nasłuchujących śledzenia i filtry  
  
1.  Kod w pierwszej procedurze nie identyfikuje programowo wszystkie obiekty nasłuchujące śledzenia lub filtrów. Kod samodzielnie powoduje komunikaty śledzenia zapisywana nasłuchującego śledzenia domyślnego. Aby skonfigurować obiekty nasłuchujące śledzenia określonych i ich filtrów skojarzony, należy edytować plik konfiguracji, który odpowiada nazwie aplikacji. W tym pliku możesz dodać lub usunąć odbiornik, ustaw właściwości i filtr dla odbiornika lub usunąć odbiorników. W poniższym przykładzie plik konfiguracji pokazuje, jak zainicjować odbiornika śledzenia konsoli i odbiornika śledzenia składnika zapisywania tekstu dla źródła śledzenia, który jest utworzony w poprzedniej procedurze. Oprócz konfigurowania obiektów nasłuchujących śledzenia, plik konfiguracji tworzy filtry dla obu odbiorniki oraz przełącznik źródła dla źródła śledzenia. Przedstawiono dwie metody dodawania obiektów nasłuchujących śledzenia: Dodawanie odbiornika bezpośrednio w źródle śledzenia i dodawanie odbiornik do kolekcji udostępnione obiekty nasłuchujące i dodanie go przez nazwę źródła. Filtry dla dwa odbiorniki są inicjowane z poziomu innego źródła. Powoduje to niektóre komunikaty zapisywana przez tylko jeden z dwóch odbiorników.  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Aby zmienić poziom, w którym odbiornik zapisuje komunikat śledzenia  
  
1.  Plik konfiguracji inicjuje ustawienia źródła śledzenia w czasie aplikacji został zainicjowany. Się zmiany tych ustawień należy zmienić plik konfiguracji i ponowne uruchomienie aplikacji lub programowo odświeżanie aplikacji przy użyciu <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody. Aplikację można dynamicznie zmieniać właściwości ustawione przy użyciu pliku konfiguracji, aby zastąpić wszystkie ustawienia określone przez użytkownika.  Na przykład możesz chcieć mieć pewność, że krytycznych wiadomości zawsze są wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.  
  
    ```  
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
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [Porady: tworzenie i Inicjowanie źródeł śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [Obiekty nasłuchujące śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md)
