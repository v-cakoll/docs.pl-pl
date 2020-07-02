---
title: Obiekty nasłuchujące śledzenia
description: Poznaj detektory śledzenia, które są mechanizmem do zbierania i rejestrowania komunikatów śledzenia przesyłanych w programie .NET. Odbiornik zbiera, przechowuje i kieruje komunikaty.
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
ms.openlocfilehash: d08f86c782284a296090cf63e4b03c8d446a95fc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803526"
---
# <a name="trace-listeners"></a>Obiekty nasłuchujące śledzenia
W przypadku korzystania z **funkcji trace**, **Debug** i <xref:System.Diagnostics.TraceSource> , musisz mieć mechanizm zbierania i rejestrowania wysyłanych komunikatów. Komunikaty śledzenia są odbierane przez *odbiorniki*. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Odbiorniki są dostępne dla **debugowania**, **śledzenia**i <xref:System.Diagnostics.TraceSource> klas, z których każdy może wysyłać dane wyjściowe do różnych obiektów odbiornika. Poniżej przedstawiono najczęściej używane wstępnie zdefiniowane detektory:  
  
- <xref:System.Diagnostics.TextWriterTraceListener>Przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub do elementu, który jest <xref:System.IO.Stream> klasą. Może również zapisywać w konsoli lub w pliku, ponieważ są to <xref:System.IO.Stream> klasy.  
  
- <xref:System.Diagnostics.EventLogTraceListener>Przekierowuje dane wyjściowe do dziennika zdarzeń.  
  
- <xref:System.Diagnostics.DefaultTraceListener>Emituje komunikaty **Write** i **WriteLine** do **Funkcja OutputDebugString** oraz do metody **Debugger. log** . W programie Visual Studio powoduje to wyświetlenie komunikatów debugowania w oknie danych wyjściowych. Komunikaty **potwierdzenia** zakończone **niepowodzeniem** i niepowodzeniem EMITUJĄ również do interfejsu API systemu Windows **Funkcja OutputDebugString** oraz metody **Debugger. log** , a także powodują wyświetlenie okna komunikatu. To zachowanie jest zachowaniem domyślnym dla komunikatów **debugowania** i **śledzenia** , ponieważ **DefaultTraceListener** jest automatycznie dołączany do każdej `Listeners` kolekcji i jest jedynym odbiornikiem.  
  
- <xref:System.Diagnostics.ConsoleTraceListener>Kieruje śledzenie lub debugowanie danych wyjściowych do standardowego wyjścia lub standardowego strumienia błędów.  
  
- <xref:System.Diagnostics.DelimitedListTraceListener>Kierowanie kieruje lub debuguje dane wyjściowe do składnika zapisywania tekstu, takiego jak składnik zapisywania strumienia lub strumień, taki jak strumień pliku. Wynik śledzenia jest w rozdzielonym formacie tekstowym, który używa ogranicznika określonego przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> Właściwość.  
  
- <xref:System.Diagnostics.XmlWriterTraceListener>Kieruje śledzenie lub debugowanie danych wyjściowych w formacie XML zakodowanym do <xref:System.IO.TextWriter> lub do <xref:System.IO.Stream> , takich jak <xref:System.IO.FileStream> .  
  
 Jeśli chcesz, aby każdy odbiornik oprócz <xref:System.Diagnostics.DefaultTraceListener> do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> wyprowadzania, należy dodać go do `Listeners` kolekcji. Aby uzyskać więcej informacji, zobacz [How to: Create and Initialize detektory śledzenia](how-to-create-and-initialize-trace-listeners.md) i [instrukcje: użycie TraceSource i filtrów z odbiornikami śledzenia](how-to-use-tracesource-and-filters-with-trace-listeners.md). Każdy odbiornik w kolekcji **odbiorników** pobiera te same komunikaty z metod danych wyjściowych śledzenia. Załóżmy na przykład, że skonfigurowano dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**. Każdy odbiornik otrzymuje ten sam komunikat. **TextWriterTraceListener** przekierowuje dane wyjściowe do strumienia, a **EventLogTraceListener** przekieruje dane wyjściowe do dziennika zdarzeń.  
  
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
 Można zdefiniować własne detektory, dziedzicząc klasę bazową **TraceListener** i zastępując jej metody przy użyciu dostosowanych metod. Aby uzyskać więcej informacji na temat tworzenia detektorów zdefiniowanych przez dewelopera, zobacz sekcję <xref:System.Diagnostics.TraceListener> w temacie .NET Framework Reference.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
- [Przełączniki śledzenia](trace-switches.md)
