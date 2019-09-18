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
ms.openlocfilehash: a67bd2c0daa8acc81113a1e38ea463753ae34077
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052731"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Instrukcje: Tworzenie i inicjowanie obiektów nasłuchujących śledzenia

Klasy <xref:System.Diagnostics.Debug?displayProperty=nameWithType> i<xref:System.Diagnostics.Trace?displayProperty=nameWithType> wysyłają komunikaty do obiektów o nazwie detektory, które odbierają i przetwarzają te komunikaty. Jeden taki odbiornik <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>jest automatycznie tworzony i inicjowany po włączeniu śledzenia lub debugowania. Jeśli chcesz <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> , aby dane wyjściowe były kierowane do wszelkich dodatkowych źródeł, należy utworzyć i zainicjować dodatkowe detektory śledzenia.

Utworzone odbiorniki powinny odzwierciedlać potrzeby aplikacji. Na przykład, jeśli chcesz, aby rekord tekstowy wszystkich danych wyjściowych śledzenia, Utwórz <xref:System.Diagnostics.TextWriterTraceListener> odbiornik, który zapisuje wszystkie dane wyjściowe w nowym pliku tekstowym, gdy jest włączony. Z drugiej strony, jeśli chcesz wyświetlić dane wyjściowe tylko podczas wykonywania aplikacji, Utwórz <xref:System.Diagnostics.ConsoleTraceListener> odbiornik, który kieruje wszystkie dane wyjściowe do okna konsoli. <xref:System.Diagnostics.EventLogTraceListener> Może kierować dane wyjściowe śledzenia do dziennika zdarzeń. Aby uzyskać więcej informacji, zobacz [detektory śledzenia](trace-listeners.md).

Można utworzyć detektory śledzenia w [pliku konfiguracyjnym aplikacji](../configure-apps/index.md) lub w kodzie. Zalecamy korzystanie z plików konfiguracji aplikacji, ponieważ umożliwiają one Dodawanie, modyfikowanie lub usuwanie detektorów śledzenia bez konieczności zmiany kodu.

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Aby utworzyć odbiornik śledzenia i używać go przy użyciu pliku konfiguracji

1. Zadeklaruj odbiornik śledzenia w pliku konfiguracyjnym aplikacji. Jeśli tworzony odbiornik wymaga innych obiektów, należy je także zadeklarować. Poniższy przykład pokazuje, jak utworzyć odbiornik o nazwie `myListener` zapis w pliku `TextWriterOutput.log`tekstowym.

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

2. <xref:System.Diagnostics.Trace> Użyj klasy w kodzie, aby napisać komunikat do detektorów śledzenia.

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

- Dodaj odbiornik śledzenia do <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji i Wyślij do odbiorników informacje o śledzeniu.

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

- Jeśli nie chcesz, aby odbiornik odbierał dane wyjściowe śledzenia, nie dodawaj go do <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji. Można emitować dane wyjściowe przez odbiornik niezależny <xref:System.Diagnostics.Trace.Listeners%2A> od kolekcji, wywołując własne metody wyjściowe odbiornika. Poniższy przykład pokazuje, jak napisać wiersz do odbiornika, który nie znajduje się w <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji.

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

- [Obiekty nasłuchujące śledzenie](trace-listeners.md)
- [Przełączniki śledzenia](trace-switches.md)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](how-to-add-trace-statements-to-application-code.md)
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
