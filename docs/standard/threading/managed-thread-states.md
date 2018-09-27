---
title: Zarządzane stany wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a55409cd2c3bed2bc09db10622de1cceab934112
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235286"
---
# <a name="managed-thread-states"></a>Zarządzane stany wątków
Właściwość <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> zapewnia maska bitowa, która wskazuje bieżący stan wątku. Wątek jest zawsze w co najmniej jednym z możliwych stanów w <xref:System.Threading.ThreadState> wyliczenia i może być różne stany, w tym samym czasie.  
  
> [!IMPORTANT]
>  Stan wątku jest przydatne w kilku tylko dla debugowania scenariuszy. Kod powinien nigdy nie używaj stan wątku do synchronizowania działania wątków.  
  
 Podczas tworzenia wątków zarządzanych jest <xref:System.Threading.ThreadState.Unstarted> stanu. Wątek pozostaje w <xref:System.Threading.ThreadState.Unstarted> stan do momentu jej jest przenoszony do stanu uruchomienia przez system operacyjny. Wywoływanie <xref:System.Threading.Thread.Start%2A> umożliwia systemowi operacyjnemu wiedzieć, że można uruchomić wątku; nie zmienia stan wątku.  
  
 Niezarządzanych wątków, które należy wprowadzić w środowisku zarządzanym są już w stanie uruchomionym. Gdy wątek jest w stanie uruchomionym, liczba akcji może spowodować jej na zmianę stanów. W poniższej tabeli wymieniono czynności, które powodują zmianę stanu, wraz z odpowiednim stanie nowe.  
  
|Akcja|Wynikowy nowy stan|  
|------------|-------------------------|  
|Konstruktor <xref:System.Threading.Thread> nosi nazwę klasy.|<xref:System.Threading.ThreadState.Unstarted>|  
|Inny wątek wywoła <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|Wątek reaguje na <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> i zacznie działać.|<xref:System.Threading.ThreadState.Running>|  
|Wywołania wątku <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Wywołania wątku <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> na inny obiekt.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Wywołania wątku <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> w innym wątku.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Inny wątek wywoła <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|Wątek reaguje na <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> żądania.|<xref:System.Threading.ThreadState.Suspended>|  
|Inny wątek wywoła <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Inny wątek wywoła <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|Wątek reaguje na <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted>, następnie <xref:System.Threading.ThreadState.Stopped>|  
  
 Ponieważ <xref:System.Threading.ThreadState.Running> stan ma wartość 0, nie jest możliwe przeprowadzenie bitowych testów w celu odnalezienia tego stanu. Zamiast tego można używać następującego testu (w pseudo-kodzie):  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 Wątki są często więcej niż jednego stanu w danym momencie. Na przykład, jeśli wątek jest zablokowany na <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> wywołanie, a drugi wątek wywołuje <xref:System.Threading.Thread.Abort%2A> na tym samym wątku wątek będzie w obu <xref:System.Threading.ThreadState.WaitSleepJoin> i <xref:System.Threading.ThreadState.AbortRequested> Państwa, w tym samym czasie. W takim przypadku tak szybko, jak wątek wraca z wywołania <xref:System.Threading.Monitor.Wait%2A> lub jest przerwany, będzie ona otrzymywać <xref:System.Threading.ThreadAbortException>.  
  
 Po opuszczeniu wątku <xref:System.Threading.ThreadState.Unstarted> stanu wyniku wywołania <xref:System.Threading.Thread.Start%2A>, nigdy nie powraca do <xref:System.Threading.ThreadState.Unstarted> stanu. Wątek może nigdy nie opuszczają <xref:System.Threading.ThreadState.Stopped> stanu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadState>  
- [Wątkowość](../../../docs/standard/threading/index.md)
