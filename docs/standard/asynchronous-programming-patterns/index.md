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
ms.openlocfilehash: e3535e2979d2430fcb434a578f94d8d5b3925631
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666572"
---
# <a name="asynchronous-programming-patterns"></a>Wzorce programowania asynchronicznego

Platforma .NET udostępnia trzy wzorce do wykonywania operacji asynchronicznych:  

- **Wzorzec asynchroniczny oparty na zadaniach (TAP)** , który używa pojedynczej metody do reprezentowania inicjacji i ukończenia operacji asynchronicznej. Naciśnij przycisk został wprowadzony w .NET Framework 4. **Jest to zalecane podejście do programowania asynchronicznego w programie .NET.** Słowa kluczowe [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/keywords/await.md) w C# programie oraz operatory [Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic Dodaj obsługę języka dla TAP. Aby uzyskać więcej informacji, zobacz [wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md).  

- **Wzorzec asynchroniczny oparty na zdarzeniach (EAP)** , który jest oparty na zdarzeniach starszym modelu do zapewniania zachowania asynchronicznego. Wymaga metody, która ma `Async` sufiks i jedno lub więcej zdarzeń, typy delegatów obsługi zdarzeń i `EventArg`typy pochodne. Protokół EAP został wprowadzony w .NET Framework 2,0. Nie jest już zalecane w przypadku nowych rozwiązań programistycznych. Aby uzyskać więcej informacji, zobacz [asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md).  

- Wzorzec **modelu programowania asynchronicznego (APM)** (nazywany <xref:System.IAsyncResult> również wzorcem), który jest starszym <xref:System.IAsyncResult> modelem, który używa interfejsu w celu zapewnienia zachowania asynchronicznego. W tym wzorcu operacje synchroniczne wymagają `Begin` , `End` a `BeginWrite` metody (na przykład i `EndWrite` w celu zaimplementowania asynchronicznej operacji zapisu). Ten wzorzec nie jest już zalecany w przypadku nowych rozwiązań programistycznych. Aby uzyskać więcej informacji, zobacz [asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Porównanie wzorców

Aby szybko porównać sposób wykonywania operacji asynchronicznych przez trzy wzorce, należy rozważyć `Read` metodę, która odczytuje określoną ilość danych do podanego buforu, rozpoczynając od określonego przesunięcia:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Odpowiedniki TAP dla tej metody uwidaczniają następujące pojedyncze `ReadAsync` metody:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

Odpowiedniki protokołu EAP uwidaczniają następujący zestaw typów i członków:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Odpowiedniki APM uwidaczniają `BeginRead` metody i `EndRead` :  
  
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

- [Na poziomie Async](../async-in-depth.md)
- [Programowanie asynchroniczne wC#](../../csharp/async.md)
- [Programowanie asynchroniczne wF#](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
