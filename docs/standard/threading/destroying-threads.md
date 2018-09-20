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
ms.openlocfilehash: 9a243c95aff77a5de2b3af15542c0bcc44870333
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323340"
---
# <a name="destroying-threads"></a>Niszczenie wątków
<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda jest używana do zatrzymywania wątków zarządzanych trwałe. Gdy wywołujesz <xref:System.Threading.Thread.Abort%2A>, środowisko uruchomieniowe języka wspólnego generuje <xref:System.Threading.ThreadAbortException> w wątek docelowy może przechwycić wątek docelowy. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Jeśli wykonywany jest wątek niezarządzanego kodu podczas jego <xref:System.Threading.Thread.Abort%2A> metoda jest wywoływana, środowisko uruchomieniowe oznacza je <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. Wyjątek jest generowany, kiedy wątek wraca z kodem zarządzanym.  
  
 Gdy wątek jest przerwany, nie można uruchomić ponownie.  
  
 <xref:System.Threading.Thread.Abort%2A> Metoda nie powoduje, że wątek przerwać natychmiast, ponieważ wątek docelowy może przechwycić <xref:System.Threading.ThreadAbortException> i wykonywanie dowolnych ilości kodu w `finally` bloku. Możesz wywołać <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Jeśli musisz poczekać, aż wątek została zakończona. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> jest wywołania blokowania, która nie zwraca aż wątek faktycznie zatrzymała wykonywanie lub opcjonalny limit czasu upłynął. Przerwanie wątku można wywołać <xref:System.Threading.Thread.ResetAbort%2A> metody lub wykonywania przetwarzania niepowiązanego w `finally` zablokować, więc jeśli nie określisz przekroczenie limitu czasu, czas oczekiwania nie gwarantuje zakończenia.  
  
 Wątki, które oczekują na wywołanie <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metoda może zostać przerwane przez inne wątki, które wywołują <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>ThreadAbortException — Obsługa  
 Jeśli oczekujesz, że wątek przerwanie, w wyniku wywołania metody <xref:System.Threading.Thread.Abort%2A> z własnego kodu lub w wyniku rozładowywania domeny aplikacji, w którym wątek jest uruchomiony (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> używa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończenie wątków), wątek musi obsługiwać. <xref:System.Threading.ThreadAbortException> i wykonywać żadnego przetwarzania końcowego w `finally` klauzuli, jak pokazano w poniższym kodzie.  
  
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
  
 Twój kod czyszczenia musi znajdować się w `catch` klauzuli lub `finally` klauzuli, ponieważ <xref:System.Threading.ThreadAbortException> jest zgłaszany ponownie przez system na końcu `finally` klauzuli lub na końcu `catch` klauzuli w przypadku nie `finally` klauzuli.  
  
 Można zapobiec systemu przez wywołanie metody ponowne generowanie wyjątku <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody. Jednak zrobić, to tylko wtedy, gdy Twój własny kod spowodowało <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
