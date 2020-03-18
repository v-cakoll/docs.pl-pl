---
title: Wzorce programowania asynchronicznego
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: e1efe9c3eb57f317def91e527506c358eb086679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160056"
---
# <a name="asynchronous-programming-patterns"></a>Wzorce programowania asynchronicznego

.NET udostępnia trzy wzorce do wykonywania operacji asynchronicznych:  

- **Oparty na zadaniach wzorzec asynchroniczny (TAP),** który używa pojedynczej metody do reprezentowania inicjowania i zakończenia operacji asynchronicznej. TAP został wprowadzony w .NET Framework 4. **Jest to zalecane podejście do programowania asynchronicznego w .NET.** [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) słów kluczowych w języku C# i [Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) operatorów w języku Visual Basic dodać obsługę języka tap. Aby uzyskać więcej informacji, zobacz [Asynchroniczny wzorzec (TAP) oparty na zadaniach](task-based-asynchronous-pattern-tap.md).  

- **Oparty na zdarzeniach wzorzec asynchroniczny (EAP),** który jest opartym na zdarzeniach starszym modelu zapewniającym zachowanie asynchroniczne. Wymaga metody, która `Async` ma sufiks i jeden lub więcej zdarzeń, typy delegatów obsługi obsługi zdarzeń i `EventArg`typy pochodne. EAP został wprowadzony w .NET Framework 2.0. Nie jest już zalecany do nowego rozwoju. Aby uzyskać więcej informacji, zobacz [Wzorce asynchroniczne oparte na zdarzeniach (EAP).](event-based-asynchronous-pattern-eap.md)  

- **Asynchroniczny model programowania (APM)** wzorzec (nazywany również <xref:System.IAsyncResult> wzorzec), który jest starszy model, który używa <xref:System.IAsyncResult> interfejsu, aby zapewnić zachowanie asynchroniczne. W tym wzorcu operacje `Begin` `End` synchroniczne wymagają `BeginWrite` i `EndWrite` metody (na przykład i zaimplementować operację zapisu asynchronicznego). Ten wzorzec nie jest już zalecany do nowego rozwoju. Aby uzyskać więcej informacji, zobacz [Asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Porównanie wzorców

Aby uzyskać szybkie porównanie sposobu, w jaki trzy wzorce modelu operacji asynchronicznych, należy wziąć pod uwagę `Read` metodę, która odczytuje określoną ilość danych do dostarczonego buforu, począwszy od określonego odsunięcia:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Odpowiednik TAP tej metody uwidacznia następujące pojedynczej `ReadAsync` metody:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

Odpowiednik EAP będzie narazić następujący zestaw typów i elementów członkowskich:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Odpowiednik APM będzie `BeginRead` narazić i `EndRead` metody:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a>Zobacz też

- [Async w głębi](../async-in-depth.md)
- [Programowanie asynchroniczne w języku C #](../../csharp/async.md)
- [Programowanie asynchroniczne w f #](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Programowanie asynchroniczne z asynchroniczną i oczekiwaną (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
