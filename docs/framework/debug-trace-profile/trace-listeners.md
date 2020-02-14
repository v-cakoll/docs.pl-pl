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
ms.openlocfilehash: a51c046a296fbb62d21c7784cf7c1e78b700f3e9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216139"
---
# <a name="trace-listeners"></a>Obiekty nasłuchujące śledzenia
W przypadku korzystania z **funkcji trace**, **Debug** i <xref:System.Diagnostics.TraceSource>należy mieć mechanizm zbierania i rejestrowania wysyłanych komunikatów. Komunikaty śledzenia są odbierane przez *odbiorniki*. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Odbiorniki są dostępne dla klas **debugowania**, **śledzenia**i <xref:System.Diagnostics.TraceSource>, z których każdy może wysyłać dane wyjściowe do różnych obiektów odbiornika. Poniżej przedstawiono najczęściej używane wstępnie zdefiniowane detektory:  
  
- <xref:System.Diagnostics.TextWriterTraceListener> przekierowuje dane wyjściowe do wystąpienia klasy <xref:System.IO.TextWriter> lub do wszystkiego, który jest klasą <xref:System.IO.Stream>. Może również zapisywać w konsoli lub w pliku, ponieważ są to <xref:System.IO.Stream> klas.  
  
- <xref:System.Diagnostics.EventLogTraceListener> przekierowuje dane wyjściowe do dziennika zdarzeń.  
  
- <xref:System.Diagnostics.DefaultTraceListener> emituje komunikaty **Write** i **WriteLine** do **Funkcja OutputDebugString** i do metody **Debugger. log** . W programie Visual Studio powoduje to wyświetlenie komunikatów debugowania w oknie danych wyjściowych. Komunikaty **potwierdzenia** zakończone **niepowodzeniem** i niepowodzeniem EMITUJĄ również do interfejsu API systemu Windows **Funkcja OutputDebugString** oraz metody **Debugger. log** , a także powodują wyświetlenie okna komunikatu. To zachowanie jest zachowaniem domyślnym dla komunikatów **debugowania** i **śledzenia** , ponieważ **DefaultTraceListener** jest automatycznie dołączane do każdej kolekcji `Listeners` i jest jedynym odbiornikiem.  
  
- <xref:System.Diagnostics.ConsoleTraceListener> kieruje śledzenie lub debugowanie danych wyjściowych do standardowego wyjścia lub standardowego strumienia błędów.  
  
- <xref:System.Diagnostics.DelimitedListTraceListener> kieruje śledzenie lub debugowanie danych wyjściowych do składnika zapisywania tekstu, takiego jak składnik zapisywania strumienia lub strumień, taki jak strumień pliku. Wynik śledzenia jest w rozdzielonym formacie tekstowym, który używa ogranicznika określonego przez właściwość <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>.  
  
- <xref:System.Diagnostics.XmlWriterTraceListener> kieruje śledzenie lub debugowanie danych wyjściowych jako dane zakodowane w formacie XML do <xref:System.IO.TextWriter> lub do <xref:System.IO.Stream>, takich jak <xref:System.IO.FileStream>.  
  
 Jeśli chcesz, aby każdy odbiornik oprócz <xref:System.Diagnostics.DefaultTraceListener> odbierać **debugowanie**, **śledzenie** i <xref:System.Diagnostics.TraceSource> dane wyjściowe, należy dodać go do kolekcji `Listeners`. Aby uzyskać więcej informacji, zobacz [How to: Create and Initialize detektory śledzenia](how-to-create-and-initialize-trace-listeners.md) i [instrukcje: użycie TraceSource i filtrów z odbiornikami śledzenia](how-to-use-tracesource-and-filters-with-trace-listeners.md). Każdy odbiornik w kolekcji **odbiorników** pobiera te same komunikaty z metod danych wyjściowych śledzenia. Załóżmy na przykład, że skonfigurowano dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**. Każdy odbiornik otrzymuje ten sam komunikat. **TextWriterTraceListener** przekierowuje dane wyjściowe do strumienia, a **EventLogTraceListener** przekieruje dane wyjściowe do dziennika zdarzeń.  
  
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
 Można zdefiniować własne detektory, dziedzicząc klasę bazową **TraceListener** i zastępując jej metody przy użyciu dostosowanych metod. Aby uzyskać więcej informacji na temat tworzenia detektorów zdefiniowanych przez dewelopera, zobacz <xref:System.Diagnostics.TraceListener> w .NET Framework Reference.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
- [Przełączniki śledzenia](trace-switches.md)
