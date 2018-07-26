---
title: lock — Instrukcja (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960962"
---
# <a name="lock-statement-c-reference"></a>lock — Instrukcja (odwołanie w C#)
`lock` — Słowo kluczowe oznacza blok instrukcji jako sekcję krytyczną uzyskując blokadę wykluczania wzajemnego dla danego obiektu, wykonując instrukcję i następnie zwalniając blokadę. Poniższy przykład zawiera `lock` instrukcji.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [synchronizacji wątków](../../programming-guide/concepts/threading/thread-synchronization.md).  
  
## <a name="remarks"></a>Uwagi  
 `lock` — Słowo kluczowe gwarantuje, że jeden wątek nie wprowadził krytycznych części kodu, podczas gdy inny wątek znajduje się w sekcji krytycznych. Jeśli inny wątek próbuje wprowadzić kod zablokowany, po upływie, zablokować, dopóki obiekt jest zwalniane.  
  
 Sekcja [wątki](../../programming-guide/concepts/threading/index.md) w tym artykule omówiono, wątki.  
  
 `lock` Wywołania — słowo kluczowe <xref:System.Threading.Monitor.Enter%2A> na początku bloku i <xref:System.Threading.Monitor.Exit%2A> na końcu bloku. A <xref:System.Threading.ThreadInterruptedException> jest generowany, jeśli <xref:System.Threading.Thread.Interrupt%2A> przerywa działanie wątku, który oczekuje na wprowadzenie `lock` instrukcji.  
  
 Ogólnie rzecz biorąc, należy unikać blokowania na `public` typu lub wystąpień będące poza kontrolą swój kod. Typowe konstrukcje `lock (this)`, `lock (typeof (MyType))`, i `lock ("myLock")` naruszenia niniejszych wytycznych:  
  
-   `lock (this)` jest to problem, jeśli wystąpienie może być publicznie dostępne.  
  
-   `lock (typeof (MyType))` jest to problem, jeśli `MyType` jest publicznie dostępny.  
  
-   `lock("myLock")` jest to problem, ponieważ każdy inny kod proces, korzystając z tych samych parametrach współużytkują ten sam blokady.  
  
 Najlepszym rozwiązaniem jest zdefiniowanie `private` obiektu można zablokować, lub `private static` zmiennej obiektu, aby chronić dane wspólne dla wszystkich wystąpień.  
  
 Nie można użyć [await](../../../csharp/language-reference/keywords/await.md) — słowo kluczowe w treści `lock` instrukcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje prosty użytkowania wątki bez blokowania w języku C#.  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto wątków i `lock`. Tak długo, jak `lock` instrukcji, blok instrukcji to sekcja krytycznego i `balance` nigdy nie będzie liczbą ujemną.  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wątkowość](../../programming-guide/concepts/threading/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe instrukcji](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [Operacje blokowane](../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../standard/threading/autoresetevent.md)  
 [Synchronizacja wątku](../../programming-guide/concepts/threading/thread-synchronization.md)
