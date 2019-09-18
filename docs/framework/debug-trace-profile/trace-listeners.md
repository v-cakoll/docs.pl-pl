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
ms.openlocfilehash: 752a6a5f9608aa260f192ee3e9e0709b7a10e27e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052287"
---
# <a name="trace-listeners"></a>Obiekty nasłuchujące śledzenia
W przypadku korzystania z **funkcji trace**, **Debug** i <xref:System.Diagnostics.TraceSource>, musisz mieć mechanizm zbierania i rejestrowania wysyłanych komunikatów. Komunikaty śledzenia są odbierane przez *odbiorniki*. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Odbiorniki są dostępne dla **debugowania**, **śledzenia**i <xref:System.Diagnostics.TraceSource> klas, z których każdy może wysyłać dane wyjściowe do różnych obiektów odbiornika. Poniżej przedstawiono najczęściej używane wstępnie zdefiniowane detektory:  
  
- Przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub do elementu <xref:System.IO.Stream> , który jest klasą. <xref:System.Diagnostics.TextWriterTraceListener> Może również zapisywać w konsoli lub w pliku, ponieważ są to <xref:System.IO.Stream> klasy.  
  
- <xref:System.Diagnostics.EventLogTraceListener> Przekierowuje dane wyjściowe do dziennika zdarzeń.  
  
- Emituje komunikaty Write i WriteLine do funkcja OutputDebugString oraz do metody Debugger. log. <xref:System.Diagnostics.DefaultTraceListener> W programie Visual Studio powoduje to wyświetlenie komunikatów debugowania w oknie danych wyjściowych. Komunikaty **potwierdzenia** zakończone **niepowodzeniem** i niepowodzeniem EMITUJĄ również do interfejsu API systemu Windows **Funkcja OutputDebugString** oraz metody **Debugger. log** , a także powodują wyświetlenie okna komunikatu. To zachowanie jest zachowaniem domyślnym dla komunikatów **debugowania** i **śledzenia** , ponieważ **DefaultTraceListener** jest automatycznie dołączany `Listeners` do każdej kolekcji i jest jedynym odbiornikiem.  
  
- <xref:System.Diagnostics.ConsoleTraceListener> Kieruje śledzenie lub debugowanie danych wyjściowych do standardowego wyjścia lub standardowego strumienia błędów.  
  
- <xref:System.Diagnostics.DelimitedListTraceListener> Kierowanie kieruje lub debuguje dane wyjściowe do składnika zapisywania tekstu, takiego jak składnik zapisywania strumienia lub strumień, taki jak strumień pliku. Wynik śledzenia jest w rozdzielonym formacie tekstowym, który używa ogranicznika określonego przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> właściwość.  
  
- Kieruje śledzenie lub debugowanie danych wyjściowych w formacie XML zakodowanym <xref:System.IO.TextWriter> do lub do <xref:System.IO.Stream>, takich jak <xref:System.IO.FileStream>. <xref:System.Diagnostics.XmlWriterTraceListener>  
  
 Jeśli chcesz <xref:System.Diagnostics.DefaultTraceListener> , aby każdy odbiornik oprócz do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> wyprowadzania, należy dodać go do `Listeners` kolekcji. Aby uzyskać więcej informacji, zobacz [jak: Utwórz i zainicjuj](how-to-create-and-initialize-trace-listeners.md) detektory [śledzenia i instrukcje: Używaj TraceSource i filtrów z odbiornikami](how-to-use-tracesource-and-filters-with-trace-listeners.md)śledzenia. Każdy odbiornik w kolekcji **odbiorników** pobiera te same komunikaty z metod danych wyjściowych śledzenia. Załóżmy na przykład, że skonfigurowano dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**. Każdy odbiornik otrzymuje ten sam komunikat. **TextWriterTraceListener** przekierowuje dane wyjściowe do strumienia, a **EventLogTraceListener** przekieruje dane wyjściowe do dziennika zdarzeń.  
  
 Poniższy przykład pokazuje, jak wysyłać dane wyjściowe do kolekcji **odbiorników** .  
  
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
  
 Debugowanie i śledzenie współdzielą tę samą kolekcję **detektorów** , więc jeśli obiekt odbiornika zostanie dodany do kolekcji **Debug.** Listeners w aplikacji, zostanie dodany do kolekcji **Trace.** Listeners.  
  
 Poniższy przykład przedstawia sposób użycia odbiornika do wysyłania informacji o śledzeniu do konsoli programu:  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Detektory zdefiniowane przez dewelopera  
 Można zdefiniować własne detektory, dziedzicząc klasę bazową **TraceListener** i zastępując jej metody przy użyciu dostosowanych metod. Aby uzyskać więcej informacji na temat tworzenia detektorów zdefiniowanych przez <xref:System.Diagnostics.TraceListener> dewelopera, zobacz sekcję w temacie .NET Framework Reference.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
- [Przełączniki śledzenia](trace-switches.md)
