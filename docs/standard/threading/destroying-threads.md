---
title: Niszczenie wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155935"
---
# <a name="destroying-threads"></a>Niszczenie wątków

Aby zakończyć wykonywanie wątku, zazwyczaj używany jest [wspólny model anulowania](cancellation-in-managed-threads.md). Czasami nie jest możliwe zatrzymywanie wątku wspólnie, ponieważ uruchamia kod innej firmy, który nie został zaprojektowany w celu uzyskania spółdzielni. Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> w .NET Framework może służyć do kończenia wymuszania wątku zarządzanego. Gdy wywołasz <xref:System.Threading.Thread.Abort%2A>, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Threading.ThreadAbortException> w wątku docelowym, który może zostać przechwycony przez wątek docelowy. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nie jest obsługiwana w programie .NET Core. Jeśli konieczne jest zakończenie wykonywania kodu innej firmy w programie .NET Core, należy uruchomić go w osobnym procesie i użyć <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.

> [!NOTE]
> Jeśli wątek wykonuje kod niezarządzany, gdy jego Metoda <xref:System.Threading.Thread.Abort%2A> jest wywoływana, środowisko uruchomieniowe go oznaczy <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. Wyjątek jest zgłaszany, gdy wątek zwraca kod zarządzany.  
  
 Po przerwaniu wątku nie można go ponownie uruchomić.  
  
 Metoda <xref:System.Threading.Thread.Abort%2A> nie powoduje natychmiastowego przerwania wątku, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonać dowolne ilości kodu w bloku `finally`. Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, jeśli chcesz poczekać na zakończenie wątku. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> jest wywołaniem blokującym, które nie zwraca, dopóki wątek nie zostanie faktycznie zatrzymany lub upłynie opcjonalny interwał limitu czasu. Przerwany wątek może wywołać metodę <xref:System.Threading.Thread.ResetAbort%2A> lub wykonać nieograniczone przetwarzanie w bloku `finally`, dlatego jeśli nie określisz limitu czasu, oczekiwania nie zostanie zakończone.  
  
 Wątki, które oczekują na wywołanie metody <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> mogą zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Obsługa ThreadAbortException  
 Jeśli oczekujesz, że wątek zostanie przerwany, w wyniku wywołania <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowania domeny aplikacji, w której działa wątek (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do zakończenia wątków), wątek musi obsłużyć <xref:System.Threading.ThreadAbortException> i wykonać wszelkie końcowe przetwarzanie w klauzuli `finally`, jak pokazano w poniższym kodzie.  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try
{  
    // Code that is executing when the thread is aborted.  
}
catch (ThreadAbortException ex)
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.
}  
// Do not put clean-up code here, because the exception
// is rethrown at the end of the Finally clause.  
```  
  
 Kod czyszczący musi znajdować się w klauzuli `catch` lub klauzuli `finally`, ponieważ <xref:System.Threading.ThreadAbortException> jest ponownie zgłaszany przez system na końcu klauzuli `finally` lub na końcu klauzuli `catch`, jeśli nie ma klauzuli `finally`.  
  
 Można uniemożliwić ponowne zgłoszenie wyjątku przez system, wywołując metodę <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>. Jednak należy to zrobić tylko wtedy, gdy własny kod spowodował <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
