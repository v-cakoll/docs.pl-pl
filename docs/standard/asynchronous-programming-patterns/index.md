---
title: Wzorce programowania asynchronicznego
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d76aef201fead37923a65cfeead16638b09842
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452787"
---
# <a name="asynchronous-programming-patterns"></a>Wzorce programowania asynchronicznego

.NET zawiera trzy wzorce do wykonywania operacji asynchronicznych:  

- **Oparta na zadaniach asynchronicznej wzorca (TAP)**, który używa jednej metody do reprezentowania rozpoczęcie i zakończenie operacji asynchronicznej. Naciśnij pozycję została wprowadzona w programie .NET Framework 4. **Jest to zalecane podejście do programowania asynchronicznego w .NET.** [Async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) słów kluczowych w C# i [Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operatory w języku Visual Basic Dodaj Obsługa języków w programie TAP. Aby uzyskać więcej informacji, zobacz [opartego na zadaniach asynchronicznej wzorca (TAP)](task-based-asynchronous-pattern-tap.md).  

- **Oparte na zdarzeniach asynchroniczny wzorzec (EAP)**, który jest oparty na zdarzeniach model starszej wersji zapewniające zachowanie asynchroniczne. Wymaga metody, która ma `Async` sufiks i jeden lub więcej zdarzeń, typów delegatów obsługi zdarzeń, a `EventArg`— typy pochodne. Protokół EAP został wprowadzony w programie .NET Framework 2.0. Zaleca się już w nowych wdrożeniach. Aby uzyskać więcej informacji, zobacz [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](event-based-asynchronous-pattern-eap.md).  

- **Modelu programowania asynchronicznego (APM)** wzorca (nazywane również <xref:System.IAsyncResult> wzorca), czyli starszego modelu, który wykorzystuje <xref:System.IAsyncResult> interfejsu, aby zapewnić zachowanie asynchroniczne. W tym wzorcu synchroniczne operacje wymagają `Begin` i `End` metod (na przykład `BeginWrite` i `EndWrite` do implementacji asynchronicznego zapisu operacji). Ten wzorzec nie jest zalecane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [modelu programowania asynchronicznego (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Porównanie wzorców

Porównanie szybki sposób trzy wzorce operacji asynchronicznych w modelu, należy wziąć pod uwagę `Read` metodę, która odczytuje określoną ilość danych do dostarczonego buforu, rozpoczynając od określonego przesunięcia:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Odpowiednikiem tej metody wzorca TAP może narazić następujące pojedynczego `ReadAsync` metody:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
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
  
Odpowiednikiem APM może narazić `BeginRead` i `EndRead` metody:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a>Zobacz także

- [Asynchroniczne szczegółowo](../async-in-depth.md)
- [Programowanie asynchroniczne w języku C#](~/docs/csharp/async.md)
- [Programowanie asynchroniczne w języku F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
