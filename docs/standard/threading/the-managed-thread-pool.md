---
title: Zarządzana Pula wątków
description: Dowiedz się więcej o pulę wątków .NET, która zapewnia tła wątków roboczych
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7721ffaebfefadee332c923d867e68204b5205f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678337"
---
# <a name="the-managed-thread-pool"></a>Zarządzana Pula wątków

<xref:System.Threading.ThreadPool?displayProperty=nameWithType> Klasa udostępnia aplikację z pulą wątków roboczych, które są zarządzane przez system, dzięki czemu możesz skupić się na zadania aplikacji, a nie wątku zarządzania. W przypadku krótkich zadania, które wymagają przetwarzania w tle zarządzana Pula wątków jest łatwy sposób korzystać z wielu wątków. Korzystanie z puli wątków jest znacznie łatwiejsze w Framework 4 lub nowszym, ponieważ tworzysz <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiekty, które wykonują zadania asynchroniczne na wątek puli wątków.  
  
.NET używa wątków z puli wątków na potrzeby wielu celów, w tym [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) operacje, asynchronicznych operacji We/Wy zakończeniu [czasomierza](timers.md) wywołań zwrotnych, zarejestrowany oczekiwania operacji asynchronicznej metody wywołuje się, przy użyciu delegatów, i <xref:System.Net?displayProperty=nameWithType> gniazda połączenia.  

## <a name="thread-pool-characteristics"></a>Właściwości puli wątków

Czy wątków z puli wątków [tła](foreground-and-background-threads.md) wątków. Każdy wątek korzysta z domyślnego rozmiaru stosu, jest wykonywany na domyślny priorytet i znajduje się w wielowątkowych typu apartment. Po ukończeniu jego zadania wątków w puli wątków jest zwracany w kolejce oczekiwania wątków. Od tej chwili może zostać użyte. To ponowne użycie umożliwia aplikacjom uniknąć kosztów tworzenia nowego wątku dla każdego zadania.
  
Istnieje tylko jeden wątek puli na proces.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Wyjątki w wątków z puli wątków

Nieobsługiwanych wyjątków w wątków z puli wątków zakończyć proces. Istnieją trzy wyjątki od tej reguły:  
  
- A <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> jest zgłaszany w wątku z puli wątków, ponieważ <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> została wywołana.  
- Element <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> jest zgłaszany w wątku z puli wątków, ponieważ Trwa zwalnianie domeny aplikacji.  
- Środowisko uruchomieniowe języka wspólnego lub procesu hosta kończy działanie wątku.  
  
Aby uzyskać więcej informacji, zobacz [wyjątki w zarządzanych wątkach](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maksymalna liczba wątków z puli wątków

Liczba operacji, które można umieścić w kolejce puli wątków jest ograniczona jedynie ilością dostępnej pamięci. Jednak w puli wątków ogranicza liczbę wątków, które może być aktywny w procesie jednocześnie. Jeśli wszystkich wątków z puli wątków są zajęte, elementy robocze dodatkowe są umieszczane w kolejce do momentu wątków do wykonania ich stają się dostępne. Począwszy od programu .NET Framework 4, domyślny rozmiar puli wątków dla procesu zależy od wielu czynników, takich jak rozmiar wirtualnej przestrzeni adresowej. Proces może wywołać <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> metodę pozwala ustalić liczbę wątków.  
  
Maksymalna liczba wątków można kontrolować za pomocą <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> i <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> metody.  

> [!NOTE]
> Kod, który jest hostem środowiska uruchomieniowego języka wspólnego można ustawić przy użyciu rozmiaru [ `ICorThreadpool::CorSetMaxThreads` ](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) metody.  
  
### <a name="thread-pool-minimums"></a>Minimalnych puli wątków

Puli wątków zapewnia nowe wątki robocze lub wątki zakończenia operacji We/Wy na żądanie, aż do napotkania określone minimum dla każdej kategorii. Możesz użyć <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> metody uzyskiwania tych wartości minimalnej.  
  
> [!NOTE]
> Gdy zapotrzebowanie jest niskie, rzeczywista liczba wątków z puli wątków może spadną poniżej wartości minimalnej.  
  
Po osiągnięciu co najmniej puli wątków można utworzyć dodatkowe wątki lub poczekaj na ukończenie niektóre zadania. Począwszy od programu .NET Framework 4, puli wątków tworzy i niszczy wątków roboczych w celu zoptymalizowania przepływności, która jest zdefiniowana jako liczbę zadań, kończące się na jednostkę czasu. Zbyt mało wątków może nie mieć optymalnego wykorzystania dostępnych zasobów, natomiast zbyt wiele wątków może zwiększyć rywalizacji o zasoby.  
  
> [!CAUTION]
> Możesz użyć <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> metody w celu zwiększenia minimalna liczba bezczynnych wątków. Jednak niepotrzebnie zwiększenie tych wartości może spowodować problemy z wydajnością. Jeśli zbyt wiele zadań jest uruchomiona w tym samym czasie, wszystkie z nich może pojawić się wolno. W większości przypadków puli wątków będą działać lepiej z własną algorytm wątki alokacji.  

## <a name="using-the-thread-pool"></a>Przy użyciu puli wątków

Począwszy od programu .NET Framework 4 jest najprostszym sposobem, aby użyć puli wątków do użycia [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md). Domyślnie, takie jak typy TPL <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> umożliwia uruchamianie zadań wątków z puli wątków.

Można również użyć puli wątków przez wywołanie metody <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> z kodu zarządzanego (lub [ `ICorThreadpool::CorQueueUserWorkItem` ](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) z niezarządzanego kodu) i przekazanie <xref:System.Threading.WaitCallback?displayProperty=nameWithType> delegować reprezentujący metodę, która wykonuje zadanie.

Innym sposobem korzystania z puli wątków jest do kolejki elementów roboczych, które są powiązane z operacji oczekiwania przy użyciu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody i przekazywanie <xref:System.Threading.WaitHandle?displayProperty=nameWithType> , gdy sygnalizowane lub upłynął limit czasu, wywołuje metodę reprezentowaną przez <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> delegować. Wątków z puli wątków są używane do wywołania metody wywołania zwrotnego.  

Przykłady można znaleźć na stronach odwołania interfejsu API.
  
## <a name="skipping-security-checks"></a>Pomijanie sprawdzania zabezpieczeń

Udostępnia również puli wątków <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> i <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody. Tych metod należy używać tylko wtedy, gdy masz pewność, że stos wywołującego jest bez znaczenia na kontrole zabezpieczeń wykonywane podczas wykonywania zadań w kolejce. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> zarówno przechwytywania wywołującego stosu, w którym jest scalany ze stosu wątku z puli wątków, gdy wątek, który rozpoczyna się wykonanie zadania. Jeśli wymagane jest sprawdzanie zabezpieczeń, cały stos musi być zaznaczone. Chociaż kontroli bezpieczeństwa, ma również negatywnie na wydajność.  

## <a name="when-not-to-use-thread-pool-threads"></a>Kiedy nie należy używać wątków z puli wątków

Istnieje kilka scenariuszy, w których jest odpowiedni do tworzenia i zarządzania nimi wątki zamiast wątków z puli wątków:  
  
- Możesz wymagać od wątku na pierwszym planie.  
- Wymagane jest wątek mieć określony priorytet.  
- Ma zadań, które powodują wątku zablokować na dłuższy czas. Pula wątków ma maksymalną liczbę wątków, więc duża liczba zablokowanych wątków z puli wątków może uniemożliwić uruchomienie zadania.  
- Należy umieścić wątków w jednowątkowym apartamentem. Wszystkie <xref:System.Threading.ThreadPool> wątki są apartamentu wielowątkowych.  
- Należy ma stabilne tożsamości skojarzonych z wątkiem lub dedykować wątku do zadania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
- [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
- [Instrukcje: zwracanie wartości z zadania](../parallel-programming/how-to-return-a-value-from-a-task.md)  
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)  
- [Wątki i wątkowość](threads-and-threading.md)  
- [Asynchroniczne operacje We/Wy pliku](../io/asynchronous-file-i-o.md)  
- [Czasomierze](timers.md)  
