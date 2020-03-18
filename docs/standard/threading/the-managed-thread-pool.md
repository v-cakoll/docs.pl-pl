---
title: Zarządzana pula wątków
description: Dowiedz się więcej o puli wątków .NET, która udostępnia wątki procesu roboczego w tle
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
ms.openlocfilehash: 2671ce7c9721b15de8a3805da27040e973a62804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400632"
---
# <a name="the-managed-thread-pool"></a>Zarządzana pula wątków

Klasa <xref:System.Threading.ThreadPool?displayProperty=nameWithType> udostępnia aplikacji z pulą wątków roboczych, które są zarządzane przez system, co pozwala skoncentrować się na zadaniach aplikacji, a nie zarządzania wątkami. Jeśli masz krótkie zadania, które wymagają przetwarzania w tle, puli zarządzanych wątków jest łatwy sposób, aby skorzystać z wielu wątków. Korzystanie z puli wątków jest znacznie łatwiejsze w ramach <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 4 i nowszych, ponieważ można tworzyć i obiekty, które wykonują zadania asynchroniczne w wątkach puli wątków.  
  
.NET używa wątków puli wątków do wielu celów, w tym operacji [Biblioteki równoległej zadań (TPL),](../parallel-programming/task-parallel-library-tpl.md) asynchronicznego uzupełniania we/wy, wywołania wywołań [skrętu czasowe,](timers.md) zarejestrowanych operacji oczekiwania, wywołań metod asynchronicznych przy użyciu delegatów i <xref:System.Net?displayProperty=nameWithType> połączeń gniazd.  

## <a name="thread-pool-characteristics"></a>Charakterystyka puli wątków

Wątki puli wątków są wątki [w tle.](foreground-and-background-threads.md) Każdy wątek używa domyślnego rozmiaru stosu, działa na domyślnypriorytet i znajduje się w mieszkaniu wielowątkowym. Po wątku w puli wątków kończy swoje zadanie, jest zwracany do kolejki wątków oczekiwania. Od tego momentu można go ponownie wykorzystać. To ponowne użycie umożliwia aplikacjom uniknięcie kosztów tworzenia nowego wątku dla każdego zadania.
  
Istnieje tylko jedna pula wątków na proces.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Wyjątki w wątkach puli wątków

Nieobsługiwane wyjątki w wątkach puli wątków zakończyć proces. Istnieją trzy wyjątki od tej reguły:  
  
- A <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> jest wyrzucone w <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wątku puli wątków, ponieważ został wywołany.  
- A <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> jest generowany w wątku puli wątków, ponieważ domena aplikacji jest zwalniany.  
- Czas wykonywania języka wspólnego lub proces hosta kończy wątek.  
  
Aby uzyskać więcej informacji, zobacz [wyjątki w wątkach zarządzanych](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maksymalna liczba wątków puli wątków

Liczba operacji, które mogą być umieszczane w kolejce do puli wątków jest ograniczona tylko przez dostępną pamięć. Jednak pula wątków ogranicza liczbę wątków, które mogą być aktywne w procesie jednocześnie. Jeśli wszystkie wątki puli wątków są zajęte, dodatkowe elementy robocze są umieszczane w kolejce, dopóki wątki do ich wykonania nie staną się dostępne. Począwszy od .NET Framework 4, domyślny rozmiar puli wątków dla procesu zależy od kilku czynników, takich jak rozmiar wirtualnej przestrzeni adresowej. Proces można wywołać metodę, <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> aby określić liczbę wątków.  
  
Można kontrolować maksymalną liczbę wątków <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> za <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> pomocą i metod.  

> [!NOTE]
> Kod, który obsługuje czas wykonywania języka [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) wspólnego można ustawić rozmiar za pomocą metody.  
  
### <a name="thread-pool-minimums"></a>Minimalne wartości puli wątków

Pula wątków zapewnia nowe wątki robocze lub wątki uzupełniania we/wy na żądanie, dopóki nie osiągnie określonego minimum dla każdej kategorii. Można użyć <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> metody, aby uzyskać te wartości minimalne.  
  
> [!NOTE]
> Gdy popyt jest niski, rzeczywista liczba wątków puli wątków może spaść poniżej wartości minimalnych.  
  
Po osiągnięciu minimum pula wątków może utworzyć dodatkowe wątki lub poczekać, aż niektóre zadania zostaną zakończone. Począwszy od .NET Framework 4, pula wątków tworzy i niszczy wątki robocze w celu optymalizacji przepływwy, która jest zdefiniowana jako liczba zadań, które są kończone na jednostkę czasu. Zbyt mało wątków może nie optymalnie korzystać z dostępnych zasobów, podczas gdy zbyt wiele wątków może zwiększyć rywalizację o zasoby.  
  
> [!CAUTION]
> Można użyć <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> metody, aby zwiększyć minimalną liczbę bezczynnych wątków. Jednak niepotrzebnie zwiększenie tych wartości może powodować problemy z wydajnością. Jeśli zbyt wiele zadań rozpoczyna się w tym samym czasie, wszystkie z nich mogą wydawać się powolne. W większości przypadków pula wątków będzie działać lepiej z własnego algorytmu przydzielania wątków.  

## <a name="using-the-thread-pool"></a>Korzystanie z puli wątków

Począwszy od .NET Framework 4, najprostszym sposobem korzystania z puli wątków jest użycie [biblioteki równoległej zadania (TPL).](../parallel-programming/task-parallel-library-tpl.md) Domyślnie typy TPL, takie jak <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> używać wątków puli wątków do uruchamiania zadań.

Można również użyć puli wątków, wywołując <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) z kodu zarządzanego (lub z kodu niezarządzanego) <xref:System.Threading.WaitCallback?displayProperty=nameWithType> i przekazując pełnomocnika reprezentującego metodę, która wykonuje zadanie.

Innym sposobem użycia puli wątków jest kolejkowanie elementów pracy, <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> które są <xref:System.Threading.WaitHandle?displayProperty=nameWithType> związane z operacją oczekiwania przy użyciu metody i przekazywania, które, gdy sygnalizowane lub po upływ limitu czasu wywołuje metodę reprezentowaną przez pełnomocnika. <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> Wątki puli wątków są używane do wywoływania metod wywołania wywołania.  

W przykładzie sprawdź strony interfejsu API, do których istnieje odwołanie.
  
## <a name="skipping-security-checks"></a>Pomijanie kontroli zabezpieczeń

Pula wątków <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> zapewnia <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> również i metody. Tych metod należy używać tylko wtedy, gdy masz pewność, że stos obiektu wywołującego nie ma znaczenia dla wszelkich kontroli zabezpieczeń wykonywanych podczas wykonywania zadania w kolejce. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> zarówno przechwytywania stosu wywołującego, który jest scalany do stosu wątku puli wątków, gdy wątek rozpoczyna wykonywanie zadania. Jeśli wymagane jest sprawdzenie zabezpieczeń, należy sprawdzić cały stos. Chociaż kontrola zapewnia bezpieczeństwo, ma również koszt wydajności.  

## <a name="when-not-to-use-thread-pool-threads"></a>Kiedy nie używać wątków puli wątków

Istnieje kilka scenariuszy, w których należy tworzyć własne wątki i zarządzać nimi zamiast używać wątków puli wątków:  
  
- Wymagany wątek pierwszego planu.  
- Wymagawątku, aby mieć określony priorytet.  
- Masz zadania, które powodują, że wątek do blokowania przez długi czas. Pula wątków ma maksymalną liczbę wątków, więc duża liczba zablokowanych wątków puli wątków może uniemożliwić uruchamianie zadań.  
- Musisz umieścić nici w mieszkaniu jednowątkowym. Wszystkie <xref:System.Threading.ThreadPool> wątki znajdują się w wielowątkowym mieszkaniu.  
- Musisz mieć stabilną tożsamość skojarzoną z wątkiem lub poświęcić wątek do zadania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md)
- [Porady: zwracanie wartości z zadania](../parallel-programming/how-to-return-a-value-from-a-task.md)
- [Wątkowe obiekty i operacje](threading-objects-and-features.md)
- [Wątki i wątkowość](threads-and-threading.md)
- [Asynchroniczne We/Wy pliku](../io/asynchronous-file-i-o.md)
- [Czasomierze](timers.md)
