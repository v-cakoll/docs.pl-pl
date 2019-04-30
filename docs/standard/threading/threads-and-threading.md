---
title: Wątki i wątkowość
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095bd92921c9cd54d3a7d97ed07b35526b85c57f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682992"
---
# <a name="threads-and-threading"></a>Wątki i wątkowość

Wielowątkowość pozwala na zwiększenie szybkości reakcji aplikacji i, jeśli aplikacja działa w systemie wieloprocesorowym lub wieloma procesorami, zwiększyć jej przepustowość.

## <a name="processes-and-threads"></a>Procesy i wątki

A *procesu* jest wykonywania programu. System operacyjny używa procesów do rozdzielania aplikacji, które są wykonywane. A *wątku* to podstawowa jednostka, do której system operacyjny przydziela czas procesora. Każdy wątek ma [priorytet planowania](scheduling-threads.md) i obsługuje zestaw struktur, wówczas system używa do zapisania kontekst wątku, gdy wykonywanie wątków jest wstrzymany. Kontekst wątku zawiera wszystkie informacje, które trzeba bezbłędnie wznowić wykonania, w tym wątku zestaw rejestrów Procesora i stosu wątku. Wiele wątków można uruchomić w ramach procesu. Wszystkie wątki procesów udostępnianie jej wirtualnej przestrzeni adresowej. Wątek może wykonać dowolną część kodu programu, w tym części wykonywane przez inny wątek.

> [!NOTE]
> .NET Framework zapewnia sposób izolowania aplikacji w ramach procesu przy użyciu *domen aplikacji*. (Domen aplikacji nie są dostępne na platformie .NET Core). Aby uzyskać więcej informacji, zobacz [domeny aplikacji i wątków](../../framework/app-domains/application-domains.md#application-domains-and-threads) części [domen aplikacji](../../framework/app-domains/application-domains.md) artykułu.

Domyślnie .NET program została uruchomiona z jednym wątkiem, często nazywane *głównej* wątku. Jednak może utworzyć dodatkowe wątki na wykonanie kodu w sposób równoległy lub równocześnie z wątku głównego. Te wątki są często nazywane *procesu roboczego* wątków.

## <a name="when-to-use-multiple-threads"></a>Kiedy należy używać wielu wątków

Aby zwiększyć szybkość reakcji aplikacji i korzystać z zalet systemem wieloprocesorowym lub wielordzeniowych w celu zwiększenia przepływności aplikacji za pomocą wielu wątków.

Należy wziąć pod uwagę aplikacji pulpitu, w którym wątek główny jest odpowiedzialny za elementy interfejsu użytkownika i reaguje na czynności użytkownika. Użyj wątków roboczych, aby wykonywać czasochłonne operacje, w przeciwnym razie może zajmować wątek główny i utworzyć interfejs użytkownika przestanie odpowiadać. Możesz również użyć dedykowany wątek służący do komunikacji sieciowej lub urządzenia szybciej odpowiadać przychodzących komunikatów lub zdarzeń.

Jeśli program wykonuje operacje, które może odbywać się równolegle, można zmniejszyć łączny czas wykonywania przez wykonywanie tych operacji w oddzielnych wątkach i uruchomienie go w systemie wieloprocesorowym lub wielordzeniowych. W systemie, korzystanie z wielowątkowością może zwiększyć przepływność wraz z większą elastyczność.

## <a name="how-to-use-multithreading-in-net"></a>Jak używać wielowątkowości w .NET

Począwszy od programu .NET Framework 4, zalecanym sposobem wykorzystywać wielowątkowości jest użycie [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [Parallel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md). Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../parallel-programming/index.md).

Program PLINQ i TPL zależą od <xref:System.Threading.ThreadPool> wątków. <xref:System.Threading.ThreadPool?displayProperty=nameWithType> Klasa udostępnia aplikację .NET z pulą wątków roboczych. Możesz także użyć wątków z puli wątków. Aby uzyskać więcej informacji, zobacz [zarządzana Pula wątków](the-managed-thread-pool.md).

Ostatnio, możesz użyć <xref:System.Threading.Thread?displayProperty=nameWithType> klasa, która reprezentuje wątków zarządzanych. Aby uzyskać więcej informacji, zobacz [używanie wątków i wątkowości](using-threads-and-threading.md).

Wiele wątków może być konieczne do uzyskania dostępu do zasobu udostępnionego. Zasób w stanie nieuszkodzonym i uniknąć Sytuacje wyścigu, należy zsynchronizować do niego dostęp wątku. Można również do koordynowania interakcję wielu wątków. .NET oferuje wiele różnych typów, które służy do synchronizowania dostępu do zasobu udostępnionego lub koordynowania interakcji wątku. Aby uzyskać więcej informacji, zobacz [Przegląd elementów podstawowych synchronizacji](overview-of-synchronization-primitives.md).

Obsługa wyjątków w wątkach. Nieobsługiwanych wyjątków w wątkach ogólnie zakończyć proces. Aby uzyskać więcej informacji, zobacz [wyjątki w zarządzanych wątkach](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Zobacz także

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Zarządzana wątkowość — najlepsze rozwiązania](managed-threading-best-practices.md)
- [Przetwarzanie równoległe, współbieżność i programowania asynchronicznego w .NET](../parallel-processing-and-concurrency.md)
- [Procesy i wątki — informacje](/windows/desktop/procthread/about-processes-and-threads)