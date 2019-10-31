---
title: Zarządzana pula wątków
description: Informacje o puli wątków .NET, która zapewnia wątki robocze w tle
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
ms.openlocfilehash: 2671ce7c9721b15de8a3805da27040e973a62804
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127539"
---
# <a name="the-managed-thread-pool"></a>Zarządzana pula wątków

Klasa <xref:System.Threading.ThreadPool?displayProperty=nameWithType> udostępnia aplikację z pulą wątków roboczych, które są zarządzane przez system, co pozwala skoncentrować się na zadaniach aplikacji, a nie na zarządzaniu wątkami. Jeśli masz krótkie zadania wymagające przetwarzania w tle, Zarządzana pula wątków jest łatwym sposobem wykorzystania wielu wątków. Korzystanie z puli wątków jest znacznie łatwiejsze w środowisku 4 i nowszych, ponieważ można tworzyć <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów, które wykonują zadania asynchroniczne w wątkach puli wątków.  
  
Platforma .NET wykorzystuje wątki puli wątków w wielu celach, w tym operacje [biblioteki zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) , asynchroniczne uzupełnianie we/wy, wywołania zwrotne [czasomierza](timers.md) , zarejestrowane operacje oczekiwania, wywołania metod asynchronicznych używające delegatów i gniazda <xref:System.Net?displayProperty=nameWithType> Licznik.  

## <a name="thread-pool-characteristics"></a>Charakterystyki puli wątków

Wątki puli wątków są wątkiem w [tle](foreground-and-background-threads.md) . Każdy wątek używa domyślnego rozmiaru stosu, jest uruchamiany zgodnie z priorytetem domyślnym i jest w Apartament wielowątkowy. Gdy wątek w puli wątków ukończy swoje zadanie, jest on zwracany do kolejki oczekujących wątków. Z tego momentu można ponownie użyć tego programu. To ponowne użycie umożliwia aplikacjom uniknięcie kosztów tworzenia nowego wątku dla każdego zadania.
  
Dla każdego procesu istnieje tylko jedna pula wątków.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Wyjątki w wątkach puli wątków

Nieobsłużone wyjątki w wątkach puli wątków przerywają proces. Istnieją trzy wyjątki od tej reguły:  
  
- W wątku puli wątków zostanie wygenerowany <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType>, ponieważ został wywołany <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
- W wątku puli wątków zostanie wygenerowany <xref:System.AppDomainUnloadedException?displayProperty=nameWithType>, ponieważ trwa zwalnianie domeny aplikacji.  
- Środowisko uruchomieniowe języka wspólnego lub proces hosta przerywa wątek.  
  
Aby uzyskać więcej informacji, zobacz [wyjątki w zarządzanych wątkach](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maksymalna liczba wątków puli wątków

Liczba operacji, które można umieścić w kolejce do puli wątków, jest ograniczona tylko przez dostępną pamięć. Jednak Pula wątków ogranicza liczbę wątków, które mogą być aktywne w procesie jednocześnie. Jeśli wszystkie wątki puli wątków są zajęte, dodatkowe elementy robocze są umieszczane w kolejce do momentu udostępnienia wątków do ich wykonania. Począwszy od .NET Framework 4, domyślny rozmiar puli wątków dla procesu zależy od kilku czynników, takich jak rozmiar wirtualnej przestrzeni adresowej. Proces może wywołać metodę <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType>, aby określić liczbę wątków.  
  
Maksymalną liczbę wątków można kontrolować przy użyciu metod <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> i <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.  

> [!NOTE]
> Kod, który hostuje środowisko uruchomieniowe języka wspólnego, może ustawić rozmiar przy użyciu metody [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) .  
  
### <a name="thread-pool-minimums"></a>Minimalna Pula wątków

Pula wątków udostępnia nowe wątki robocze lub wątki zakończenia operacji we/wy na żądanie do momentu osiągnięcia określonej wartości minimalnej dla każdej kategorii. Aby uzyskać te wartości minimalne, można użyć metody <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Gdy zapotrzebowanie jest niskie, rzeczywista liczba wątków puli wątków może spaść poniżej wartości minimalnych.  
  
Po osiągnięciu minimalnej puli wątków można utworzyć dodatkowe wątki lub poczekać na zakończenie niektórych zadań. Począwszy od .NET Framework 4, Pula wątków tworzy i niszczy wątki robocze w celu zoptymalizowania przepływności, która jest definiowana jako liczba zadań ukończonych na jednostkę czasu. Zbyt mało wątków może nie optymalnie korzystać z dostępnych zasobów, a zbyt wiele wątków może zwiększyć rywalizację o zasoby.  
  
> [!CAUTION]
> Za pomocą metody <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> można zwiększyć minimalną liczbę bezczynnych wątków. Jednak niekonieczne zwiększenie tych wartości może spowodować problemy z wydajnością. Jeśli zbyt wiele zadań rozpocznie się w tym samym czasie, wszystkie z nich mogą wydawać się wolne. W większości przypadków Pula wątków będzie działać lepiej wraz z własnym algorytmem do alokowania wątków.  

## <a name="using-the-thread-pool"></a>Korzystanie z puli wątków

Począwszy od .NET Framework 4, najprostszym sposobem korzystania z puli wątków jest użycie [biblioteki zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md). Domyślnie typy TPL, takie jak <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601>, używają wątków puli wątków do uruchamiania zadań.

Można również użyć puli wątków, wywołując <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> z kodu zarządzanego (lub [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) z kodu niezarządzanego) i przekazując delegat <xref:System.Threading.WaitCallback?displayProperty=nameWithType> reprezentujący metodę wykonującą zadanie.

Innym sposobem korzystania z puli wątków jest kolejkowanie elementów roboczych, które są związane z operacją oczekiwania przy użyciu metody <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> i przekazanie <xref:System.Threading.WaitHandle?displayProperty=nameWithType>, które po zasygnalizowaniu lub po przekroczeniu limitu czasu wywołuje metodę reprezentowaną przez delegata <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType>. Wątki puli wątków są używane do wywoływania metod wywołania zwrotnego.  

Aby zapoznać się z przykładami, Sprawdź strony interfejsu API, do których się odwołuje.
  
## <a name="skipping-security-checks"></a>Pomijanie sprawdzania zabezpieczeń

Pula wątków oferuje również metody <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> i <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType>. Te metody są używane tylko wtedy, gdy masz pewność, że stos wywołującego nie ma znaczenia dla żadnych kontroli zabezpieczeń wykonywanych podczas wykonywania zadania w kolejce. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> przechwytują stos wywołującego, który jest scalany ze stosem wątku puli wątków, gdy wątek zacznie wykonać zadanie. Jeśli wymagane jest sprawdzenie zabezpieczeń, należy zaznaczyć cały stos. Chociaż sprawdzanie zapewnia bezpieczeństwo, ma także koszt wydajności.  

## <a name="when-not-to-use-thread-pool-threads"></a>Kiedy nie używać wątków puli wątków

Istnieje kilka scenariuszy, w których warto utworzyć własne wątki i zarządzać nimi zamiast używać wątków puli wątków:  
  
- Wymagany jest wątek pierwszego planu.  
- Wymagany jest wątek mający określony priorytet.  
- Masz zadania, które powodują, że wątek jest blokowany przez długi czas. Pula wątków ma maksymalną liczbę wątków, więc duża liczba zablokowanych wątków puli wątków może uniemożliwić uruchomienie zadań.  
- Należy umieścić wątki w jednowątkowym apartamentie. Wszystkie wątki <xref:System.Threading.ThreadPool> są w Apartament wielowątkowy.  
- Musisz mieć stabilną tożsamość skojarzoną z wątkiem lub przeznaczyć wątek na zadanie.  
  
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
