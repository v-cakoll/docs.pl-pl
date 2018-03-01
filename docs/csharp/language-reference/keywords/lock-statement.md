---
title: "lock — Instrukcja (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb48c2b1554ad2817406eaef42b4cb336ea46862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lock-statement-c-reference"></a>lock — Instrukcja (odwołanie w C#)
`lock` — Słowo kluczowe oznacza blok instrukcji jako sekcja krytyczna uzyskania wzajemnego wykluczeń dla danego obiektu, wykonywania instrukcji, a następnie zwolnienie blokady. Poniższy przykład zawiera `lock` instrukcji.  
  
```csharp  
class Account  
{  
    decimal balance;  
    private Object thisLock = new Object();  
  
    public void Withdraw(decimal amount)  
    {  
        lock (thisLock)  
        {  
            if (amount > balance)  
            {  
                throw new Exception("Insufficient funds");  
            }  
            balance -= amount;  
        }  
    }  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz [wątku synchronizacji](../../programming-guide/concepts/threading/thread-synchronization.md).  
  
## <a name="remarks"></a>Uwagi  
 `lock` — Słowo kluczowe gwarantuje, że jeden wątek nie wprowadził krytyczne sekcji kodu podczas inny wątek znajduje się w sekcji krytyczne. Jeśli inny wątek próbował wprowadzić kod zablokowany, będzie czekać, blokowanie, dopóki nie zostanie zwolniony obiektu.  
  
 Sekcja [wątki](../../programming-guide/concepts/threading/index.md) omówiono wątków.  
  
 `lock` Wywołania — słowo kluczowe <xref:System.Threading.Monitor.Enter%2A> na początku bloku i <xref:System.Threading.Monitor.Exit%2A> na końcu bloku. A <xref:System.Threading.ThreadInterruptedException> jest generowany, jeśli <xref:System.Threading.Thread.Interrupt%2A> przerwań wątku, który oczekuje na wprowadzenie `lock` instrukcji.  
  
 Ogólnie rzecz biorąc, należy unikać blokowania na `public` typu lub wystąpień poza swój kod sterowania. Typowe konstrukcje `lock (this)`, `lock (typeof (MyType))`, i `lock ("myLock")` narusza niniejsze wytyczne:  
  
-   `lock (this)`jest to problem, jeśli wystąpienie jest dostępny publicznie.  
  
-   `lock (typeof (MyType))`jest problem, jeśli `MyType` jest dostępny publicznie.  
  
-   `lock("myLock")`jest to problem, ponieważ innego kodu w procesie przy użyciu tych samych parametrach współużytkują tego samego blokady.  
  
 Najlepszym rozwiązaniem jest określenie `private` obiekt, aby zablokować, lub `private static` zmienna obiektu, aby chronić dane wspólne dla wszystkich wystąpień.  
  
 Nie można użyć [await](../../../csharp/language-reference/keywords/await.md) — słowo kluczowe w treści `lock` instrukcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera proste używanie wątków bez blokowania w języku C#.  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto wątków i `lock`. Tak długo, jak `lock` instrukcji, blok instrukcji jest sekcja krytyczna i `balance` nigdy nie staną się liczbą ujemną.  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wątkowość](../../programming-guide/concepts/threading/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe instrukcji](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [Operacje blokowane](../../../standard/threading/interlocked-operations.md)  
 [Autoresetevent —](../../../standard/threading/autoresetevent.md)  
 [Synchronizacja wątku](../../programming-guide/concepts/threading/thread-synchronization.md)
