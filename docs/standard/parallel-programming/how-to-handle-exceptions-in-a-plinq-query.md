---
title: 'Instrukcje: Obsługa wyjątków w zapytaniu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b5dce796e546bf041c28864c8bf66b5f51965e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046626"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Instrukcje: Obsługa wyjątków w zapytaniu PLINQ

W pierwszym przykładzie w tym temacie pokazano <xref:System.AggregateException?displayProperty=nameWithType> , jak obsłużyć, które mogą być zgłaszane z zapytania PLINQ, gdy jest ono wykonywane. Drugi przykład pokazuje, jak umieścić bloki try-catch w delegatach, jak najbliżej miejsca, w którym zostanie zgłoszony wyjątek. W ten sposób można je przechwycić zaraz po ich wystąpieniu i prawdopodobnie kontynuować wykonywanie zapytań. Gdy wyjątki mogą być rzutowane z powrotem do wątku sprzęgania, istnieje możliwość, że zapytanie może nadal przetwarzać niektóre elementy po wystąpieniu wyjątku.

W niektórych przypadkach, gdy PLINQ przechodzi do wykonywania sekwencyjnego i wystąpi wyjątek, wyjątek może być propagowany bezpośrednio i nieopakowany w <xref:System.AggregateException>. <xref:System.Threading.ThreadAbortException>Ponadto s są zawsze propagowane bezpośrednio.

> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio przerwie w wierszu, który zgłasza wyjątek, i wyświetla komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.
>
> Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak umieścić bloki try-catch wokół kodu, który wykonuje zapytanie, aby przechwytywać <xref:System.AggregateException?displayProperty=nameWithType>wszystkie zgłoszone elementy.

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

W tym przykładzie zapytanie nie może być kontynuowane po zgłoszeniu wyjątku. Przez czas, gdy kod aplikacji przechwytuje wyjątek, PLINQ już zatrzymał zapytanie we wszystkich wątkach.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak umieścić blok try-catch w delegatze, aby umożliwić przechwytywanie wyjątku i kontynuować wykonywanie zapytania.

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować i uruchomić te przykłady, skopiuj je do przykładu danych PLINQ i Wywołaj metodę z głównego.

## <a name="robust-programming"></a>Niezawodne programowanie

Nie Przechwytuj wyjątku, chyba że wiesz, jak go obsłużyć, aby nie uszkodzić stanu programu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
