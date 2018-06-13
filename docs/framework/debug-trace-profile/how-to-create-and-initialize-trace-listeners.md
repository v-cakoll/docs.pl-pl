---
title: 'Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia'
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
ms.openlocfilehash: 943621b953fbe158b3be6ae0695ba7692b7c517f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389203"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia
<xref:System.Diagnostics.Debug?displayProperty=nameWithType> i <xref:System.Diagnostics.Trace?displayProperty=nameWithType> klasy wysyłania komunikatów do obiektów o nazwie nasłuchujących odbierały i przetwarzały tych wiadomości. Jeden taki odbiornika <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, jest automatycznie tworzony i inicjowana, gdy jest włączone śledzenia i debugowania. Jeśli chcesz <xref:System.Diagnostics.Trace> lub <xref:System.Diagnostics.Debug> dane wyjściowe będą kierowane do wszelkich dodatkowych źródeł, należy utworzyć i Inicjowanie obiektów nasłuchujących śledzenia dodatkowe.  
  
 Odbiorniki tworzonych powinien odzwierciedlać potrzeb aplikacji. Na przykład rekordu tekstu zawierającego wszystkie dane wyjściowe śledzenia, utworzyć <xref:System.Diagnostics.TextWriterTraceListener> odbiornika, który zapisuje wszystkie dane wyjściowe do nowego pliku tekstowego, gdy jest włączone. Z drugiej strony, jeśli chcesz wyświetlić dane wyjściowe tylko podczas wykonywania aplikacji, Utwórz <xref:System.Diagnostics.ConsoleTraceListener> odbiornika, który określa, że wszystkie dane wyjściowe okna konsoli. <xref:System.Diagnostics.EventLogTraceListener> Mogą kierować danych wyjściowych śledzenia do dziennika zdarzeń. Aby uzyskać więcej informacji, zobacz [obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Można tworzyć obiektów nasłuchujących śledzenia w [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) lub w kodzie. Firma Microsoft zaleca użycie pliki konfiguracji aplikacji, ponieważ umożliwiają dodawanie, modyfikowanie lub usuwanie obiektów nasłuchujących śledzenia bez konieczności zmiany kodu.  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Tworzenie i używanie nasłuchującego śledzenia przy użyciu pliku konfiguracji  
  
1.  Deklarowanie Twojej nasłuchującego śledzenia w pliku konfiguracyjnym aplikacji. Jeśli odbiornik, które tworzysz wymaga inne obiekty, zadeklarować je również. Poniższy przykład pokazuje, jak utworzyć odbiornik o nazwie `myListener` zapisuje plik tekstowy `TextWriterOutput.log`.  
  
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
  
2.  Użyj <xref:System.Diagnostics.Trace> klasy w kodzie do zapisu obiektów nasłuchujących śledzenia wiadomości.  
  
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
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a>Do utworzenia i użycia nasłuchującego śledzenia w kodzie  
  
-   Dodać obiektu nasłuchującego śledzenia do <xref:System.Diagnostics.Trace.Listeners%2A> zbierania i wysyłania informacji do odbiorniki śledzenia.  
  
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
  
     - lub -  
  
-   Jeśli nie chcesz, aby Twoje odbiornika do odbierania danych wyjściowych śledzenia, nie należy dodawać go do <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji. Można Emituj danych wyjściowych przez odbiornik niezależnie od <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji, wywołując odbiornika dla własnych danych wyjściowych metody. Poniższy przykład przedstawia sposób zapisania wiersza do odbiornika, który nie znajduje się w <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty nasłuchujące śledzenie](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
