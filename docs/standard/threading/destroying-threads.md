---
title: Niszczenie wątków
description: Należy znać opcje, gdy trzeba zniszczyć wątek w programie .NET, na przykład w przypadku odwołania do spółdzielni lub metody Thread. Abort. Dowiedz się, jak obsłużyć ThreadAbortException.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: baf9289413de0e99533f121eb2a404ff0d873511
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768511"
---
# <a name="destroying-threads"></a>Niszczenie wątków

Aby zakończyć wykonywanie wątku, zazwyczaj używany jest [wspólny model anulowania](cancellation-in-managed-threads.md). Czasami nie jest możliwe zatrzymywanie wątku wspólnie, ponieważ uruchamia kod innej firmy, który nie został zaprojektowany w celu uzyskania spółdzielni. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda w .NET Framework może służyć do kończenia wymuszonego wymuszenia wątku zarządzanego. Podczas wywoływania <xref:System.Threading.Thread.Abort%2A> , środowisko uruchomieniowe języka wspólnego generuje <xref:System.Threading.ThreadAbortException> w wątku docelowym, który wątek docelowy może przechwycić. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda nie jest obsługiwana w programie .NET Core. Jeśli konieczne jest zakończenie wykonywania kodu innej firmy w programie .NET Core, należy uruchomić go w osobnym procesie i użyć <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

> [!NOTE]
> Jeśli wątek wykonuje kod niezarządzany, gdy <xref:System.Threading.Thread.Abort%2A> Metoda jest wywoływana, środowisko uruchomieniowe go oznaczy <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> . Wyjątek jest zgłaszany, gdy wątek zwraca kod zarządzany.  
  
 Po przerwaniu wątku nie można go ponownie uruchomić.  
  
 <xref:System.Threading.Thread.Abort%2A>Metoda nie powoduje natychmiastowego przerwania wątku, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonać dowolne ilości kodu w `finally` bloku. Możesz wywołać, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Jeśli musisz poczekać na zakończenie wątku. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>jest wywołaniem blokującym, które nie zwraca, dopóki wątek nie zostanie faktycznie zatrzymany lub upłynie opcjonalny interwał limitu czasu. Przerwany wątek może wywołać <xref:System.Threading.Thread.ResetAbort%2A> metodę lub wykonać nieograniczone przetwarzanie w `finally` bloku, dlatego jeśli nie określisz limitu czasu, oczekiwania nie zostanie zakończone.  
  
 Wątki, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody mogą zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> .  
  
## <a name="handling-threadabortexception"></a>Obsługa ThreadAbortException  
 Jeśli oczekujesz, że wątek zostanie przerwany, w wyniku wywołania <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowania domeny aplikacji, w której działa wątek ( <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używany <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do kończenia wątków), wątek musi obsłużyć <xref:System.Threading.ThreadAbortException> i wykonać dowolne końcowe przetwarzanie w `finally` klauzuli, jak pokazano w poniższym kodzie.  
  
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
  
 Kod czyszczący musi znajdować się w `catch` klauzuli lub `finally` klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest ponownie zgłaszany przez system na końcu `finally` klauzuli lub na końcu `catch` klauzuli, jeśli nie ma `finally` klauzuli.  
  
 Można uniemożliwić ponowne zgłoszenie wyjątku przez system, wywołując <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metodę. Jednak należy to zrobić tylko wtedy, gdy własny kod spowodował <xref:System.Threading.ThreadAbortException> .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Używanie wątków i wątkowości](using-threads-and-threading.md)
