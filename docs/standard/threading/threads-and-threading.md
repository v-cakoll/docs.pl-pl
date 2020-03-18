---
title: Wątki i gwintowanie
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
ms.openlocfilehash: ad36789579b95e0129e402765194b9f5e45a4cc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127505"
---
# <a name="threads-and-threading"></a>Wątki i gwintowanie

Wielowątkowość pozwala zwiększyć szybkość reakcji aplikacji i, jeśli aplikacja działa w systemie wieloprocesorowym lub wielordzeniowym, zwiększyć jego przepływność.

## <a name="processes-and-threads"></a>Procesy i wątki

*Proces* jest programem wykonującym. System operacyjny używa procesów do oddzielenia aplikacji, które są wykonywane. *Wątek* jest podstawową jednostką, do której system operacyjny przydziela czas procesora. Każdy wątek ma [priorytet planowania](scheduling-threads.md) i utrzymuje zestaw struktur używanych przez system do zapisywania kontekstu wątku, gdy wykonanie wątku jest wstrzymane. Kontekst wątku zawiera wszystkie informacje, których wątek musi bezproblemowo wznowić wykonywanie, w tym zestaw rejestrów procesora CPU i stosu wątku. Wiele wątków można uruchomić w kontekście procesu. Wszystkie wątki procesu współużytkują jego wirtualną przestrzeń adresową. Wątek można wykonać dowolną część kodu programu, w tym części są obecnie wykonywane przez inny wątek.

> [!NOTE]
> .NET Framework umożliwia izolowanie aplikacji w procesie za pomocą *domen aplikacji.* (Domeny aplikacji nie są dostępne w ustom .NET Core). Aby uzyskać więcej informacji, zobacz [domains aplikacji i wątki](../../framework/app-domains/application-domains.md#application-domains-and-threads) sekcji domen aplikacji artykułu [Domeny aplikacji.](../../framework/app-domains/application-domains.md)

Domyślnie program .NET jest uruchamiany z jednym wątkiem, często nazywanym wątkiem *podstawowym.* Jednak można utworzyć dodatkowe wątki do wykonywania kodu równolegle lub jednocześnie z wątku podstawowego. Te wątki są *worker* często nazywane wątkami roboczymi.

## <a name="when-to-use-multiple-threads"></a>Kiedy używać wielu wątków

Wiele wątków służy do zwiększenia szybkości reakcji aplikacji i skorzystania z systemu wieloprocesorowego lub wielordzeniowego w celu zwiększenia przepustowości aplikacji.

Należy wziąć pod uwagę aplikacji klasycznej, w którym wątek podstawowy jest odpowiedzialny za elementy interfejsu użytkownika i reaguje na akcje użytkownika. Wątki robocze służy do wykonywania czasochłonnych operacji, które w przeciwnym razie zajmują wątku podstawowego i sprawiają, że interfejs użytkownika nie odpowiada. Można również użyć dedykowanego wątku do komunikacji sieciowej lub urządzenia, aby lepiej reagować na przychodzące wiadomości lub zdarzenia.

Jeśli program wykonuje operacje, które można wykonać równolegle, całkowity czas wykonywania można zmniejszyć, wykonując te operacje w oddzielnych wątkach i uruchamiając program w systemie wieloprocesorowym lub wielordzeniowym. W takim systemie użycie wielowątkowości może zwiększyć przepływność wraz ze zwiększoną reakcją.

## <a name="how-to-use-multithreading-in-net"></a>Jak używać wielowątkowości w .NET

Począwszy od .NET Framework 4, zalecanym sposobem wykorzystania wielowątkowości jest użycie [biblioteki równoległej zadań (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [równoległego LINQ (PLINQ).](../parallel-programming/parallel-linq-plinq.md) Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../parallel-programming/index.md).

Zarówno TPL, jak i <xref:System.Threading.ThreadPool> PLINQ opierają się na wątkach. Klasa <xref:System.Threading.ThreadPool?displayProperty=nameWithType> udostępnia aplikację .NET z pulą wątków roboczych. Można również użyć wątków puli wątków. Aby uzyskać więcej informacji, zobacz [Pula zarządzanych wątków](the-managed-thread-pool.md).

W końcu można użyć <xref:System.Threading.Thread?displayProperty=nameWithType> klasy, która reprezentuje wątek zarządzany. Aby uzyskać więcej informacji, zobacz [Korzystanie z wątków i wątków](using-threads-and-threading.md).

Wiele wątków może być konieczne dostęp do zasobu udostępnionego. Aby zachować zasób w stanie nieuszkodzonym i uniknąć warunków wyścigu, należy zsynchronizować dostęp do wątku do niego. Można również koordynować interakcję wielu wątków. Platforma .NET udostępnia szereg typów, których można użyć do synchronizacji dostępu do udostępnionego zasobu lub współrzędnych interakcji wątku. Aby uzyskać więcej informacji, zobacz [Omówienie elementów pierwotnych synchronizacji](overview-of-synchronization-primitives.md).

Do obsługi wyjątków w wątkach. Nieobsługiwane wyjątki w wątkach zazwyczaj kończą proces. Aby uzyskać więcej informacji, zobacz [wyjątki w wątkach zarządzanych](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Zobacz też

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Najlepsze rozwiązania dotyczące wątków zarządzanych](managed-threading-best-practices.md)
- [Przetwarzanie równoległe, współbieżność i programowanie asynchroniczne w programie .NET](../parallel-processing-and-concurrency.md)
- [Informacje o procesach i wątkach](/windows/desktop/procthread/about-processes-and-threads)
