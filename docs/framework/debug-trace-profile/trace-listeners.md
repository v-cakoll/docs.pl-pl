---
title: "Obiekty nasłuchujące śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 042b8a6f7c25c34fc06d5d0bfd4ebce6417b920f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="trace-listeners"></a>Obiekty nasłuchujące śledzenia
Korzystając z **śledzenia**, **debugowania** i <xref:System.Diagnostics.TraceSource>, musi mieć mechanizm zbieranie i rejestrowanie komunikatów, które są wysyłane. Komunikaty śledzenia są odbierane przez *odbiorników*. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Obiekty nasłuchujące są dostępne dla **debugowania**, **śledzenia**, i <xref:System.Diagnostics.TraceSource> klasy, z których każdy może wysłać dane wyjściowe do różnych obiektów odbiornika. Poniżej przedstawiono typowe odbiorników wstępnie zdefiniowane:  
  
-   A <xref:System.Diagnostics.TextWriterTraceListener> przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub niczego, który jest <xref:System.IO.Stream> klasy. Może on również zapisywać w konsoli lub do pliku, ponieważ są one <xref:System.IO.Stream> klasy.  
  
-   <xref:System.Diagnostics.EventLogTraceListener> Przekierowuje dane wyjściowe do dziennika zdarzeń.  
  
-   A <xref:System.Diagnostics.DefaultTraceListener> emituje **zapisu** i **WriteLine** komunikaty **OutputDebugString** i **Debugger.Log** metody. W programie Visual Studio powoduje to komunikaty debugowania pojawią się w oknie danych wyjściowych. **Niepowodzenie** i operacja nie powiodła **Assert** wiadomości również wysyłać do **OutputDebugString** interfejsu API systemu Windows i **Debugger.Log** metody i Przyczyna polu komunikat można wyświetlić. To zachowanie jest to domyślne zachowanie dla **debugowania** i **śledzenia** wiadomości, ponieważ **DefaultTraceListener** jest automatycznie uwzględnione w każdym `Listeners` Kolekcja i jest tylko odbiornika automatycznie dołączane.  
  
-   A <xref:System.Diagnostics.ConsoleTraceListener> kieruje śledzenia i debugowania dane wyjściowe do standardowego wyjścia lub Standardowy strumień błędów.  
  
-   A <xref:System.Diagnostics.DelimitedListTraceListener> kieruje śledzenia i debugowania dane wyjściowe w składniku zapisywania tekstu, takich jak piszący strumienia, lub do strumienia, takich jak strumienia pliku. Dane wyjściowe śledzenia jest format tekstu rozdzielanego używa ogranicznik określony przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> właściwości.  
  
-   <xref:System.Diagnostics.XmlWriterTraceListener> Kieruje śledzenia lub dane wyjściowe debugowania jako dane zakodowane w formacie XML <xref:System.IO.TextWriter> lub <xref:System.IO.Stream>, takich jak <xref:System.IO.FileStream>.  
  
 Jeśli chcesz, aby wszystkie odbiornika oprócz <xref:System.Diagnostics.DefaultTraceListener> do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> danych wyjściowych, należy dodać go do `Listeners` kolekcji. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) i [porady: użycie TraceSource i filtrów z obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md). Wszelkie odbiornika w **odbiorników** kolekcji pobiera tej wiadomości z śledzenie danych wyjściowych metody. Załóżmy na przykład, należy skonfigurować dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**. Każdy odbiornika odbiera tę samą wiadomość. **TextWriterTraceListener** może bezpośrednia dane wyjściowe do strumienia i **EventLogTraceListener** może bezpośrednia dane wyjściowe do dziennika zdarzeń.  
  
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
  
 Debugowania i śledzenia udziału takie same **odbiorników** kolekcji, tak aby w przypadku dodania obiektu odbiornika do **Debug.Listeners** kolekcji w aplikacji, pobiera dodać go do **Trace.Listeners** również kolekcji.  
  
 Poniższy przykład przedstawia użycie odbiornik o wysłanie informacji śledzenia do konsoli:  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Zdefiniowane przez dewelopera odbiorników  
 Możesz definiować własne odbiorników za dziedziczenie z **TraceListener** podstawowa klasa i przesłanianie jej metody o niestandardowych metody. Aby uzyskać więcej informacji o tworzeniu odbiorników zdefiniowane przez deweloperów, zobacz <xref:System.Diagnostics.TraceListener> w odwołania programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
