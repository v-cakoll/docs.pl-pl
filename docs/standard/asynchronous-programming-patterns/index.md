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
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068407"
---
# <a name="asynchronous-programming-patterns"></a>Wzorce programowania asynchronicznego

Program .NET Framework oferuje trzy wzorce do wykonywania operacji asynchronicznych:  
  
- **Modelu programowania asynchronicznego (APM)** wzorca (nazywane również <xref:System.IAsyncResult> wzorca), gdzie asynchroniczne operacje wymagają `Begin` i `End` metod (na przykład `BeginWrite` i `EndWrite` dla asynchronicznego operacje zapisu). Ten wzorzec nie jest zalecane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
- **Oparte na zdarzeniach asynchroniczny wzorzec (EAP)**, co wymaga metody, która ma `Async` sufiks, a także wymaga przynajmniej jednego zdarzenia, typów delegatów obsługi zdarzeń, a `EventArg`— typy pochodne. Protokół EAP został wprowadzony w programie .NET Framework 2.0. Zaleca się już w nowych wdrożeniach. Aby uzyskać więcej informacji, zobacz [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
- **Oparta na zadaniach asynchronicznej wzorca (TAP)**, który używa jednej metody do reprezentowania rozpoczęcie i zakończenie operacji asynchronicznej. Naciśnij pozycję wprowadzono w programie .NET Framework 4 i jest zalecane podejście do asynchronicznego programowania w programie .NET Framework. [Async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) słów kluczowych w języku C# i [Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operatory w języku Visual Basic Dodaj Obsługa języków w programie TAP. Aby uzyskać więcej informacji, zobacz [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Porównywanie wzorców  

Porównanie szybki sposób trzy wzorce operacji asynchronicznych w modelu, należy wziąć pod uwagę `Read` metodę, która odczytuje określoną ilość danych do dostarczonego buforu, rozpoczynając od określonego przesunięcia:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
Odpowiednikiem APM tej metody może narazić `BeginRead` i `EndRead` metody:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
Odpowiednikiem EAP wystawi następujący zestaw typów i elementów członkowskich:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Odpowiednikiem wzorca TAP może narazić następujące pojedynczego `ReadAsync` metody:  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
Aby uzyskać kompleksowe omówienie wzorca TAP APM i EAP, zobacz linków dostępnych w następnej sekcji.  
  
## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| ----- | ----------- |
| [Model programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | W tym artykule opisano model starszej wersji, który używa <xref:System.IAsyncResult> interfejsu, aby zapewnić zachowanie asynchroniczne. Ten model nie jest zalecane w przypadku nowych wdrożeń. |
| [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | W tym artykule opisano oparte na zdarzeniach model starszej wersji zapewniające zachowanie asynchroniczne. Ten model nie jest zalecane w przypadku nowych wdrożeń. |
| [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | W tym artykule opisano nowy wzorzec asynchroniczny oparty na <xref:System.Threading.Tasks> przestrzeni nazw. Ten model jest zalecane podejście do programowania asynchronicznego w .NET Framework 4 i nowszych wersjach. |

## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne w języku C#](~/docs/csharp/async.md)   
- [Programowanie asynchroniczne w języku F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
