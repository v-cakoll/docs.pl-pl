---
title: "Niszczenie wątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3bdacb1cc54e3b67a1b4cef4f9fd274e65037faa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="destroying-threads"></a>Niszczenie wątków
<xref:System.Threading.Thread.Abort%2A> Metoda jest używana do zatrzymania wątku zarządzanego trwale. Podczas wywoływania <xref:System.Threading.Thread.Abort%2A>, zgłasza środowisko uruchomieniowe języka wspólnego <xref:System.Threading.ThreadAbortException> w wątek docelowy wątek docelowy może catch. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Jeśli wykonuje wątku niezarządzanego kodu, gdy jego <xref:System.Threading.Thread.Abort%2A> metoda jest wywoływana, środowisko uruchomieniowe oznacza je <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. Wyjątek jest zgłaszany, gdy wątek powróci do kodu zarządzanego.  
  
 Gdy wątek jest przerywana, nie można uruchomić ponownie.  
  
 <xref:System.Threading.Thread.Abort%2A> — Metoda nie powoduje, że wątek przerwania natychmiast, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonania dowolnego ilości kodu w `finally` bloku. Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Jeśli należy poczekać, aż wątek została zakończona. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>to wywołanie blokowania, która nie zwraca aż do wykonywania faktycznie zatrzymania wątku lub opcjonalne limit czasu upłynął. Przerwanego wątku można wywołać <xref:System.Threading.Thread.ResetAbort%2A> metody lub niepowiązany przetwarzania w `finally` zablokować, jeśli nie określisz limit czasu, czas oczekiwania nie jest gwarantowana do końca.  
  
 Wątków, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> — metoda może zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Obsługa ThreadAbortException  
 Jeśli Twoje wątku zostać przerwane w wyniku wywołania metody <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub wyniku zwolnienie domeny aplikacji, w którym jest uruchomiony wątek (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończenie wątków), musi obsługiwać Twoje wątku <xref:System.Threading.ThreadAbortException> i wykonywać żadnych końcowego przetwarzania w `finally` klauzuli, jak pokazano w poniższym kodzie.  
  
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
  
 Oczyszczanie kodu musi być w `catch` klauzuli lub `finally` klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest zgłoszony przez system na końcu `finally` klauzuli, lub na końcu `catch` klauzuli, jeśli istnieje nie `finally` klauzuli.  
  
 System uniemożliwia ponowne generowanie wyjątku przez wywołanie metody <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody. Jednak należy wykonać tylko wtedy, gdy ich w swoim własnym kodem spowodowane <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
