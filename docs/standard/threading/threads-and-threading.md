---
title: Gwinty i gwintowanie
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
ms.openlocfilehash: bac2a3ca3278b48b35d0372d52bcb79025ba1148
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739724"
---
# <a name="threads-and-threading"></a>Gwinty i gwintowanie

Wielowątkowość pozwala zwiększyć czas reakcji aplikacji i, jeśli aplikacja działa na systemie wieloprocesorowym lub wielordzeniowym, zwiększyć jej przepływność.

## <a name="processes-and-threads"></a>Procesy i wątki

*Proces* jest programem wykonawczym. System operacyjny używa procesów do oddzielenia aplikacji, które są wykonywane. *Wątek* jest podstawową jednostką, do której system operacyjny przydziela czas procesora. Każdy wątek ma [priorytet planowania](scheduling-threads.md) i utrzymuje zestaw struktur używanych przez system do zapisywania kontekstu wątku, gdy wykonanie wątku jest wstrzymane. Kontekst wątku zawiera wszystkie informacje, które wątek musi bezproblemowo wznowić wykonywanie, w tym zestaw wątku rejestrów procesora CPU i stosu. Wiele wątków można uruchomić w kontekście procesu. Wszystkie wątki procesu współużytkują jego wirtualną przestrzeń adresową. Wątek można wykonać dowolną część kodu programu, w tym części obecnie wykonywane przez inny wątek.

> [!NOTE]
> Program .NET Framework umożliwia izolowanie aplikacji w ramach procesu przy użyciu *domen aplikacji*. (Domeny aplikacji nie są dostępne w programie .NET Core). Aby uzyskać więcej informacji, zobacz [domeny aplikacji i wątki](../../framework/app-domains/application-domains.md#application-domains-and-threads) sekcji [domeny aplikacji](../../framework/app-domains/application-domains.md) artykułu.

Domyślnie program .NET jest uruchamiany z pojedynczym wątkiem, często nazywanym wątkiem *podstawowym.* Jednak można utworzyć dodatkowe wątki do wykonywania kodu równolegle lub jednocześnie z wątku podstawowego. Te wątki są często nazywane wątkami *roboczymi.*

## <a name="when-to-use-multiple-threads"></a>Kiedy używać wielu wątków

Wiele wątków służy do zwiększenia responsywności aplikacji i skorzystać z wieloprocesorowego lub wielordzeniowego systemu w celu zwiększenia przepływności aplikacji.

Należy wziąć pod uwagę aplikacji klasycznej, w którym wątek podstawowy jest odpowiedzialny za elementy interfejsu użytkownika i odpowiada na akcje użytkownika. Użyj wątków roboczych do wykonywania czasochłonnych operacji, które w przeciwnym razie zajęłyby wątek podstawowy i sprawiają, że interfejs użytkownika nie reaguje. Można również użyć dedykowanego wątku do komunikacji sieciowej lub urządzenia, aby lepiej reagować na przychodzące wiadomości lub zdarzenia.

Jeśli program wykonuje operacje, które mogą być wykonywane równolegle, całkowity czas wykonywania można zmniejszyć, wykonując te operacje w oddzielnych wątkach i uruchamiając program w systemie wieloprocesorowym lub wielordzeniowym. W takim systemie użycie wielowątkowości może zwiększyć przepustowość wraz ze zwiększoną responsywnością.

## <a name="how-to-use-multithreading-in-net"></a>Jak korzystać z wielowątkowej w .NET

Począwszy od programu .NET Framework 4, zalecanym sposobem wykorzystania wielowątkowości jest użycie [biblioteki równoległej zadań (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [równoległej LINQ (PLINQ).](../parallel-programming/introduction-to-plinq.md) Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../parallel-programming/index.md).

Zarówno TPL, jak i <xref:System.Threading.ThreadPool> PLINQ polegają na wątkach. Klasa <xref:System.Threading.ThreadPool?displayProperty=nameWithType> udostępnia aplikację .NET z pulą wątków roboczych. Można również użyć wątków puli wątków. Aby uzyskać więcej informacji, zobacz [Pula zarządzanych wątków](the-managed-thread-pool.md).

W końcu można użyć <xref:System.Threading.Thread?displayProperty=nameWithType> klasy, która reprezentuje wątek zarządzany. Aby uzyskać więcej informacji, zobacz [Korzystanie z wątków i wątków](using-threads-and-threading.md).

Wiele wątków może być konieczne, aby uzyskać dostęp do zasobu udostępnionego. Aby utrzymać zasób w stanie nieuszkodzonego i uniknąć warunków wyścigu, należy zsynchronizować dostęp do wątku do niego. Można również koordynować interakcję wielu wątków. .NET udostępnia zakres typów, których można użyć do synchronizowania dostępu do zasobu udostępnionego lub koordynowania interakcji wątku. Aby uzyskać więcej informacji, zobacz [Omówienie ujegłędnych synchronizacji](overview-of-synchronization-primitives.md).

Czy obsługiwać wyjątki w wątkach. Nieobsługiwalne wyjątki w wątkach zazwyczaj kończą proces. Aby uzyskać więcej informacji, zobacz [Wyjątki w wątkach zarządzanych](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Zobacz też

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Najważniejsze wskazówki dotyczące zarządzanych wątków](managed-threading-best-practices.md)
- [Przetwarzanie równoległe, współbieżność i programowanie asynchroniowe w programie .NET](../parallel-processing-and-concurrency.md)
- [Informacje o procesach i wątkach](/windows/desktop/procthread/about-processes-and-threads)
