---
title: 'Instrukcje: Tworzenie i inicjowanie obiektów nasłuchujących śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea5db2ba1060479f55bbd7f67266d36085a2535f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979894"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Instrukcje: Tworzenie i inicjowanie obiektów nasłuchujących śledzenia

<xref:System.Diagnostics.Debug?displayProperty=nameWithType> i <xref:System.Diagnostics.Trace?displayProperty=nameWithType> klasy wysyłania komunikatów do obiektów o nazwie obiektów nasłuchujących odbierać i przetwarzać te komunikaty. Jedno takie odbiornik <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, jest automatycznie tworzone i inicjowana, gdy włączone jest śledzenie lub debugowania. Jeśli chcesz <xref:System.Diagnostics.Trace> lub <xref:System.Diagnostics.Debug> dane wyjściowe były kierowane do żadnych dodatkowych źródeł, należy utworzyć i zainicjować odbiorniki śledzenia dodatkowe.

Odbiorniki, tworzonych powinny odzwierciedlać potrzeb aplikacji. Na przykład rekord tekstu z wszystkich danych wyjściowych śledzenia, utworzyć <xref:System.Diagnostics.TextWriterTraceListener> odbiornika, który zapisuje wszystkie dane wyjściowe w nowy plik tekstowy, gdy jest włączone. Z drugiej strony, jeśli chcesz wyświetlić dane wyjściowe tylko podczas wykonywania aplikacji, należy utworzyć <xref:System.Diagnostics.ConsoleTraceListener> odbiornika, który określa, że wszystkie dane wyjściowe do okna konsoli. <xref:System.Diagnostics.EventLogTraceListener> Można skierować dane wyjściowe śledzenia do dziennika zdarzeń. Aby uzyskać więcej informacji, zobacz [detektorów śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md).

Możesz utworzyć śledzenia słuchaczy w [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) lub w kodzie. Firma Microsoft zaleca korzystanie z plików konfiguracji aplikacji, ponieważ umożliwiają dodawanie, modyfikowanie lub usuwanie obiektów nasłuchujących śledzenia bez konieczności zmian w kodzie.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Tworzenie i używanie odbiornika śledzenia przy użyciu pliku konfiguracji

1. Zadeklaruj detektor śledzenia w pliku konfiguracyjnym aplikacji. Jeśli odbiornik, który tworzysz wymaga wszystkimi innymi obiektami, je zadeklarować także. Poniższy przykład pokazuje, jak utworzyć odbiornik o nazwie `myListener` zapisuje plik tekstowy `TextWriterOutput.log`.

    ```xml
    <configuration>
      <system.diagnostics>
        <trace autoflush="false" indentsize="4">
          <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />
            <remove name="Default" />
          </listeners>
        </trace>
      </system.diagnostics>
    </configuration>
    ```

2. Użyj <xref:System.Diagnostics.Trace> klasy w kodzie, aby zapisać komunikat do odbiorników śledzenia.

    ```vb
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

### <a name="to-create-and-use-a-trace-listener-in-code"></a>Tworzenie i używanie odbiornika śledzenia w kodzie

- Dodawanie odbiornika śledzenia do <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji i wysłać informacje, do odbiorników śledzenia.

    ```vb
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

    \- lub —

- Jeśli nie chcesz otrzymywać dane wyjściowe śledzenia z odbiornikiem, nie należy dodawać go do <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji. Może emitować dane wyjściowe za pośrednictwem niezależne od odbiornika <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji przez wywołanie metody własnych odbiornika danych wyjściowych metody. Poniższy przykład pokazuje, jak zapisywać odbiornik, który nie znajduje się w linię <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji.

    ```vb
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")
    myListener.WriteLine("Test message.")
    ' You must close or flush the trace listener to empty the output buffer.
    myListener.Flush()
    ```

    ```csharp
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");
    myListener.WriteLine("Test message.");
    // You must close or flush the trace listener to empty the output buffer.
    myListener.Flush();
    ```

## <a name="see-also"></a>Zobacz także

- [Obiekty nasłuchujące śledzenie](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
