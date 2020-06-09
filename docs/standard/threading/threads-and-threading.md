---
title: Wątki i wątkowość
description: Informacje o wątkach, takich jak procesy & wątki, kiedy używać wielu wątków, &, jak używać wielowątkowości, aby zwiększyć czas odpowiedzi lub przepływność na platformie .NET.
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
ms.openlocfilehash: b332db80069e18d3b52cd03eef4995eaad3fda7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583404"
---
# <a name="threads-and-threading"></a>Wątki i wątkowość

Wielowątkowość pozwala zwiększyć czas odpowiedzi aplikacji i, jeśli aplikacja działa w wieloprocesorowym lub wielordzeniowym systemie, zwiększyć przepływność.

## <a name="processes-and-threads"></a>Procesy i wątki

*Proces* to program wykonujący. System operacyjny używa procesów do rozdzielania wykonywanych aplikacji. *Wątek* jest jednostką podstawową, do której system operacyjny przydziela czas procesora. Każdy wątek ma [priorytet planowania](scheduling-threads.md) i utrzymuje zestaw struktur, których system używa do zapisywania kontekstu wątku, gdy wykonywanie wątku jest wstrzymane. Kontekst wątku zawiera wszystkie informacje niezbędne do bezproblemowego wznowienia wykonywania wątku, w tym zestaw rejestrów i stosów procesora CPU. W kontekście procesu można uruchomić wiele wątków. Wszystkie wątki procesu współdzielą swoją wirtualną przestrzeń adresową. Wątek może wykonać dowolną część kodu programu, w tym części, które są aktualnie wykonywane przez inny wątek.

> [!NOTE]
> .NET Framework zapewnia sposób izolowania aplikacji w ramach procesu przy użyciu *domen aplikacji*. (Domeny aplikacji nie są dostępne na platformie .NET Core). Aby uzyskać więcej informacji, zobacz sekcję [domeny aplikacji i wątki](../../framework/app-domains/application-domains.md#application-domains-and-threads) w artykule [domeny aplikacji](../../framework/app-domains/application-domains.md) .

Domyślnie program .NET jest uruchamiany z pojedynczym wątkiem, często nazywanym wątkiem *podstawowym* . Można jednak utworzyć dodatkowe wątki do wykonywania kodu równolegle lub współbieżnie przy użyciu wątku głównego. Te wątki są często nazywane wątkami *roboczymi* .

## <a name="when-to-use-multiple-threads"></a>Kiedy używać wielu wątków

Używasz wielu wątków, aby zwiększyć czas odpowiedzi aplikacji i wykorzystać wieloprocesorowy lub wielordzeniowy system w celu zwiększenia przepływności aplikacji.

Rozważ użycie aplikacji klasycznej, w której wątek główny jest odpowiedzialny za elementy interfejsu użytkownika i reaguje na działania użytkownika. Wątki robocze umożliwiają wykonywanie czasochłonnych operacji, które w przeciwnym razie zajmują wątek podstawowy i sprawiają, że interfejs użytkownika nie odpowiada. Można również użyć dedykowanego wątku do komunikacji sieciowej lub urządzenia, aby zwiększyć wydajność przychodzących komunikatów lub zdarzeń.

Jeśli program wykonuje operacje, które mogą być wykonywane równolegle, łączny czas wykonywania można zmniejszyć, wykonując te operacje w oddzielnych wątkach i uruchamiając program w wieloprocesorowym lub wielordzeniowym systemie. W takim systemie użycie wielowątkowości może zwiększyć przepływność oraz zwiększyć czas odpowiedzi.

## <a name="how-to-use-multithreading-in-net"></a>Jak używać wielowątkowości w programie .NET

Począwszy od .NET Framework 4, zalecanym sposobem użycia wielowątkowości jest użycie [biblioteki zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [równoległego LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md). Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../parallel-programming/index.md).

Zarówno TPL, jak i PLINQ są zależne od <xref:System.Threading.ThreadPool> wątków. <xref:System.Threading.ThreadPool?displayProperty=nameWithType>Klasa udostępnia aplikację .NET z pulą wątków roboczych. Można również użyć wątków puli wątków. Aby uzyskać więcej informacji, zobacz [Zarządzana pula wątków](the-managed-thread-pool.md).

Na koniec można użyć <xref:System.Threading.Thread?displayProperty=nameWithType> klasy, która reprezentuje wątek zarządzany. Aby uzyskać więcej informacji, zobacz [Korzystanie z wątków i wątkowości](using-threads-and-threading.md).

Wiele wątków może potrzebować dostępu do zasobu udostępnionego. Aby zachować zasób w stanie nieuszkodzonym i uniknąć sytuacji wyścigu, należy zsynchronizować z nim dostęp do wątku. Możesz również skoordynować interakcję wielu wątków. Platforma .NET udostępnia szereg typów, których można użyć do synchronizowania dostępu do zasobu udostępnionego lub współdziałania wątku współrzędnych. Aby uzyskać więcej informacji, zobacz [Omówienie elementów pierwotnych synchronizacji](overview-of-synchronization-primitives.md).

Obsługa wyjątków w wątkach. Nieobsłużone wyjątki w wątkach zwykle przerywają proces. Aby uzyskać więcej informacji, zobacz [wyjątki w zarządzanych wątkach](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Zobacz też

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Zarządzane wątki z najlepszymi rozwiązaniami](managed-threading-best-practices.md)
- [Równoległe przetwarzanie, współbieżność i programowanie asynchroniczne w programie .NET](../parallel-processing-and-concurrency.md)
- [Informacje o procesach i wątkach](/windows/desktop/procthread/about-processes-and-threads)
