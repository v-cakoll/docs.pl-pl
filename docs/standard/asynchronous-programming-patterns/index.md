---
title: Wzorce programowania asynchronicznego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 809385bda48c6fb8dae125fe348228aaee375a6c
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071308"
---
# <a name="asynchronous-programming-patterns"></a>Wzorce programowania asynchronicznego

.NET Framework udostępnia trzy wzorce do wykonywania operacji asynchronicznych:  
  
- **Asynchronicznego programowania modelu (APM)** wzorca (nazywane również <xref:System.IAsyncResult> wzorzec), których wymagają operacji asynchronicznych `Begin` i `End` metody (na przykład `BeginWrite` i `EndWrite` dla asynchronicznego operacje zapisu). Ten wzorzec już zaleca się nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
- **Oparty na zdarzeniach asynchroniczny wzorzec (EAP)**, która wymaga metody, która ma `Async` sufiks, a także wymaga co najmniej jednego zdarzenia, typów obiektu delegowanego obsługi zdarzeń, i `EventArg`-typów pochodnych. Protokół EAP został wprowadzony w .NET Framework 2.0. Zaleca się już w nowych wdrożeniach. Aby uzyskać więcej informacji, zobacz [oparty na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
- **Oparty na zadaniach asynchronicznej wzorca (TAP)**, który używa jednej metody w celu reprezentują rozpoczęcie i zakończenie operacji asynchronicznej. NACIŚNIJ została wprowadzona w .NET Framework 4 i jest zalecane podejście do asynchronicznego programowania w programie .NET Framework. [Async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) słów kluczowych w języku C# i [Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Obsługa języków w programie TAP dodać operatory w języku Visual Basic. Aby uzyskać więcej informacji, zobacz [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Porównywanie wzorce  

Porównanie szybki sposób trzy wzorce operacji asynchronicznych w modelu, należy wziąć pod uwagę `Read` metoda odczytuje określonej ilości danych do podanego buforu, zaczynając od określonego przesunięcia:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
Odpowiednikiem APM tej metody może narazić `BeginRead` i `EndRead` metod:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
Odpowiednik EAP wystawi następujący zestaw typów i członków:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Odpowiednik NACIŚNIJ wystawi jednym następującego `ReadAsync` metody:  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
Kompleksowe omówienie NACIŚNIJ APM i EAP, zobacz łączy znajdujących się w następnej sekcji.  
  
## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| ----- | ----------- |
| [Model programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | W tym artykule opisano model starszej wersji, który używa <xref:System.IAsyncResult> interfejsu, aby zapewnić zachowanie asynchronicznego. Ten model nie jest już zalecany dla nowych aplikacji. |
| [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | W tym artykule opisano oparty na zdarzeniach modelu starszych zapewniające zachowanie asynchroniczne. Ten model nie jest już zalecany dla nowych aplikacji. |
| [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | W tym artykule opisano nowy asynchroniczny wzorzec oparty na <xref:System.Threading.Tasks> przestrzeni nazw. Ten model jest zalecane podejście do programowania asynchronicznego w programie .NET Framework 4 i nowsze wersje. |

## <a name="see-also"></a>Zobacz także

[Programowanie asynchroniczne w języku C#](~/docs/csharp/async.md)   
[Programowanie asynchroniczne w języku F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
[Programowanie asynchroniczne z Async i Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
