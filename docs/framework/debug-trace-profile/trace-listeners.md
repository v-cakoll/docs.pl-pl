---
title: Obiekty nasłuchujące śledzenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35aec3a311680e398d9f2bba94bf4c9a274c8a04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137907"
---
# <a name="trace-listeners"></a>Obiekty nasłuchujące śledzenia
Korzystając z **śledzenia**, **debugowania** i <xref:System.Diagnostics.TraceSource>, musi mieć mechanizm do gromadzenia i rejestrowania wiadomości, które są wysyłane. Komunikaty śledzenia są odbierane przez *odbiorników*. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Odbiorniki są dostępne dla **debugowania**, **śledzenia**, i <xref:System.Diagnostics.TraceSource> klasy, z których każdy może wysyłać dane wyjściowe do wielu obiektów odbiornika. Często używanych wstępnie zdefiniowanych obiektów nasłuchujących są następujące:  
  
-   A <xref:System.Diagnostics.TextWriterTraceListener> przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub miejscem <xref:System.IO.Stream> klasy. Go także zapisać konsoli lub w pliku, ponieważ są one <xref:System.IO.Stream> klasy.  
  
-   <xref:System.Diagnostics.EventLogTraceListener> Przekierowuje dane wyjściowe do dziennika zdarzeń.  
  
-   A <xref:System.Diagnostics.DefaultTraceListener> emituje **zapisu** i **WriteLine** komunikatów **OutputDebugString** i **Debugger.Log** metody. W programie Visual Studio to powoduje, że komunikaty debugowania pojawią się w oknie danych wyjściowych. **Się nie powieść** , jak i nieudane **Asercja** wiadomości również emisji do **OutputDebugString** interfejsu Windows API i **Debugger.Log** metody i przyczynę, komunikat pole, aby być wyświetlane. To zachowanie jest zachowaniem domyślnym **debugowania** i **śledzenia** wiadomości, ponieważ **DefaultTraceListener** jest automatycznie uwzględnione w każdym `Listeners` zbieranie i jest tylko odbiornik automatycznie dołączane.  
  
-   A <xref:System.Diagnostics.ConsoleTraceListener> kieruje śledzenia i debugowania dane wyjściowe do wyjścia standardowego lub Standardowy strumień błędów.  
  
-   A <xref:System.Diagnostics.DelimitedListTraceListener> kieruje śledzenia i debugowania danych wyjściowych w składniku zapisywania tekstu, takich jak edytor strumienia lub do strumienia, takich jak strumienia pliku. Dane wyjściowe śledzenia znajduje się w format tekstu rozdzielanego, który używa ogranicznik określony przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> właściwości.  
  
-   <xref:System.Diagnostics.XmlWriterTraceListener> Kieruje śledzenia lub dane wyjściowe debugowania jako dane zakodowane w formacie XML do <xref:System.IO.TextWriter> lub <xref:System.IO.Stream>, takich jak <xref:System.IO.FileStream>.  
  
 Jeśli chcesz, aby wszystkie odbiornika oprócz <xref:System.Diagnostics.DefaultTraceListener> do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> danych wyjściowych, należy dodać go do `Listeners` kolekcji. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) i [jak: Użycie TraceSource i filtrów z obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md). Wszelkie odbiornik **odbiorników** kolekcji pobiera tymi samymi komunikatami ze śledzenia danych wyjściowych metody. Załóżmy na przykład, należy skonfigurować dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**. Każdego odbiornika otrzymuje ten sam komunikat. **TextWriterTraceListener** będzie kierować dane wyjściowe do strumienia, a **EventLogTraceListener** będzie kierować dane wyjściowe do dziennika zdarzeń.  
  
 Poniższy przykład przedstawia sposób wysłania danych wyjściowych do **odbiorników** kolekcji.  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 Debugowania i śledzenia współużytkować ten sam **odbiorników** kolekcji, więc jeśli dodasz obiekt detektor **Debug.Listeners** kolekcji w aplikacji, pobiera dodać go do **Trace.Listeners** również kolekcji.  
  
 Poniższy przykład pokazuje, jak wysyłać za pomocą odbiornik informacje śledzenia do konsoli:  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Odbiorniki zdefiniowane dla deweloperów  
 Można zdefiniować własne odbiorników przez dziedziczenie z **TraceListener** bazowa, klasy i przesłanianie jej metod przy użyciu niestandardowych metod. Aby uzyskać więcej informacji na temat tworzenia odbiorników zdefiniowane dla deweloperów, zobacz <xref:System.Diagnostics.TraceListener> w dokumentacji .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
