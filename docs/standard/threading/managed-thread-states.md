---
title: "Zarządzane stany wątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956472ef0e3b0bab85a4eb0b5585f1a4d1e0a991
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="managed-thread-states"></a>Zarządzane stany wątków
Właściwość <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> zapewnia maska bitowa, która wskazuje bieżący stan wątku. Wątek jest zawsze w co najmniej jedną z możliwych stanów w <xref:System.Threading.ThreadState> wyliczenia i może mieć różne stany w tym samym czasie.  
  
> [!IMPORTANT]
>  Stan wątku jest przydatne w kilku tylko dla scenariuszy debugowania. Kod nigdy nie należy używać stan wątku do synchronizowania działania wątków.  
  
 Podczas tworzenia wątku zarządzanego znajduje się w <xref:System.Threading.ThreadState.Unstarted> stanu. Wątek pozostaje w <xref:System.Threading.ThreadState.Unstarted> stanu, dopóki nie zostanie przeniesiona do stan uruchomienia przez system operacyjny. Wywoływanie <xref:System.Threading.Thread.Start%2A> umożliwia systemowi operacyjnemu wiedzieć, że można uruchomić wątku; nie zmienia stan wątku.  
  
 Niezarządzane wątków, które należy wprowadzić zarządzanego środowiska są już w stanie uruchomienia. Gdy wątek jest w stanie uruchomienia, liczbę akcji może spowodować jego zmiany stanów. W poniższej tabeli wymieniono akcje, które powodują zmianę stanu oraz odpowiadający mu stan nowego.  
  
|Akcja|Wynikowa nowy stan|  
|------------|-------------------------|  
|Konstruktor <xref:System.Threading.Thread> nosi nazwę klasy.|<xref:System.Threading.ThreadState.Unstarted>|  
|Inny wątek wywołania <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|Wątek odpowiada <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> i uruchamiania.|<xref:System.Threading.ThreadState.Running>|  
|Wywołania wątku <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Wywołania wątku <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> na inny obiekt.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Wywołania wątku <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> w innym wątku.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Inny wątek wywołania <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|Wątek odpowiada <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> żądania.|<xref:System.Threading.ThreadState.Suspended>|  
|Inny wątek wywołania <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Inny wątek wywołania <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|Wątek odpowiada <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted>, następnie<xref:System.Threading.ThreadState.Stopped>|  
  
 Ponieważ <xref:System.Threading.ThreadState.Running> stan ma wartość 0, nie można wykonać bitowych testów, aby odnaleźć ten stan. Zamiast tego można użyć następującego testu (w pseudo-kodzie):  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 Wątki są często więcej niż jednego stanu w danym momencie. Na przykład, jeśli wątek jest zablokowany na <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> połączeń i innego wątku wywołania <xref:System.Threading.Thread.Abort%2A> w tym samym wątku, wątek będą zarówno <xref:System.Threading.ThreadState.WaitSleepJoin> i <xref:System.Threading.ThreadState.AbortRequested> Państwa, w tym samym czasie. W takim przypadku natychmiast zwraca wątku z wywołania <xref:System.Threading.Monitor.Wait%2A> lub przerwane, zostanie wyświetlony <xref:System.Threading.ThreadAbortException>.  
  
 Gdy wątek pozostawia <xref:System.Threading.ThreadState.Unstarted> stanu w wyniku wywołania <xref:System.Threading.Thread.Start%2A>, nigdy nie powraca do <xref:System.Threading.ThreadState.Unstarted> stanu. Wątek nigdy nie może pozostać <xref:System.Threading.ThreadState.Stopped> stanu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [Wątkowość](../../../docs/standard/threading/index.md)
