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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960089"
---
# <a name="destroying-threads"></a>Niszczenie wątków
<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda służy do trwałego zatrzymania wątku zarządzanego. Podczas wywoływania <xref:System.Threading.Thread.Abort%2A>, środowisko uruchomieniowe języka wspólnego <xref:System.Threading.ThreadAbortException> generuje w wątku docelowym, który wątek docelowy może przechwycić. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Jeśli wątek wykonuje kod niezarządzany, gdy <xref:System.Threading.Thread.Abort%2A> Metoda jest wywoływana, środowisko uruchomieniowe go <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>oznaczy. Wyjątek jest zgłaszany, gdy wątek zwraca kod zarządzany.  
  
 Po przerwaniu wątku nie można go ponownie uruchomić.  
  
 Metoda nie powoduje natychmiastowego przerwania wątku, ponieważ wątek docelowy może <xref:System.Threading.ThreadAbortException> przechwycić i wykonać dowolne `finally` ilości kodu w bloku. <xref:System.Threading.Thread.Abort%2A> Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> , jeśli musisz poczekać na zakończenie wątku. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>jest wywołaniem blokującym, które nie zwraca, dopóki wątek nie zostanie faktycznie zatrzymany lub upłynie opcjonalny interwał limitu czasu. Przerwany wątek może wywołać <xref:System.Threading.Thread.ResetAbort%2A> metodę lub wykonać nieograniczone przetwarzanie `finally` w bloku, dlatego jeśli nie określisz limitu czasu, oczekiwania nie zostanie zakończone.  
  
 Wątki, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody mogą zostać przerwane przez inne wątki, które wywołują. <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>  
  
## <a name="handling-threadabortexception"></a>Obsługa ThreadAbortException  
 Jeśli oczekujesz, że wątek zostanie przerwany, w wyniku wywołania <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowania domeny aplikacji, w której działa wątek (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używany <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do kończenia wątków), wątek musi obsłużyć i wykonać wszelkie końcowe przetwarzanie `finally` w klauzuli, jak pokazano w poniższym kodzie. <xref:System.Threading.ThreadAbortException>  
  
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
  
 Kod czyszczący musi znajdować `catch` się w klauzuli `finally` lub klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest ponownie zgłaszany `finally` przez system na końcu klauzuli lub na końcu `catch` klauzuli, jeśli nie `finally` ma klauzuli.  
  
 Można uniemożliwić ponowne zgłoszenie wyjątku przez system, wywołując <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metodę. Jednak należy to zrobić tylko wtedy, <xref:System.Threading.ThreadAbortException>gdy własny kod spowodował.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
