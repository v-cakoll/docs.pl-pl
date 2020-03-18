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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155935"
---
# <a name="destroying-threads"></a>Niszczenie wątków

Aby zakończyć wykonywanie wątku, zwykle należy użyć [modelu anulowania współpracy](cancellation-in-managed-threads.md). Czasami nie jest możliwe, aby zatrzymać wątek kooperatywnie, ponieważ uruchamia kod innej firmy nie przeznaczony do anulowania współpracy. Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> w .NET Framework może służyć do zakończenia wątku zarządzanego siłą. Po wywołaniu <xref:System.Threading.Thread.Abort%2A>, common language runtime zgłasza <xref:System.Threading.ThreadAbortException> w wątku docelowego, które wątek docelowy może przechwycić. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nie jest obsługiwana w .NET Core. Jeśli musisz zakończyć wykonywanie kodu innej firmy siłą w .NET Core, uruchom go <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>w oddzielnym procesie i użyj .

> [!NOTE]
> Jeśli wątek wykonuje kod niezarządzany, <xref:System.Threading.Thread.Abort%2A> gdy jego metoda jest <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>wywoływana, czas wykonywania oznacza go . Wyjątek jest generowany, gdy wątek zwraca do kodu zarządzanego.  
  
 Po przerwanie wątku nie można go ponownie uruchomić.  
  
 Metoda <xref:System.Threading.Thread.Abort%2A> nie powoduje wątku do przerwania natychmiast, ponieważ wątek <xref:System.Threading.ThreadAbortException> docelowy można przechwycić `finally` i wykonać dowolną ilość kodu w bloku. Można wywołać, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> jeśli trzeba poczekać, aż wątek zostanie zakończony. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>jest wywołanie blokujące, które nie zwraca, dopóki wątek faktycznie przestał wykonywać lub opcjonalny przedział czasu upłynął. Przerwana wątek może wywołać <xref:System.Threading.Thread.ResetAbort%2A> metodę lub wykonać przetwarzanie `finally` nieograniczone w bloku, więc jeśli nie określisz limitu czasu, oczekiwanie nie jest gwarantowane do końca.  
  
 Wątki, które oczekują na <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> wywołanie metody może być przerwane <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>przez inne wątki, które wywołają .  
  
## <a name="handling-threadabortexception"></a>Obsługa ThreadAbortException  
 Jeśli oczekujesz, że wątek zostanie przerwane, albo <xref:System.Threading.Thread.Abort%2A> w wyniku wywołania z własnego kodu lub w wyniku<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zwalniania domeny aplikacji, w którym działa wątek (używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do zakończenia wątków), wątek musi obsługiwać <xref:System.Threading.ThreadAbortException> i wykonać wszelkie końcowe przetwarzanie w `finally` klauzuli, jak pokazano w poniższym kodzie.  
  
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
  
 Kod oczyszczania musi być w `catch` klauzuli `finally` lub klauzuli, <xref:System.Threading.ThreadAbortException> ponieważ jest rethrown przez `finally` system na końcu klauzuli lub na końcu `catch` klauzuli, jeśli nie `finally` ma klauzuli.  
  
 Można zapobiec system z ponownego wymuszenia wyjątku, wywołując <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metodę. Jednak należy to zrobić tylko wtedy, <xref:System.Threading.ThreadAbortException>gdy własny kod spowodował .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Korzystanie z wątków i wątków](../../../docs/standard/threading/using-threads-and-threading.md)
