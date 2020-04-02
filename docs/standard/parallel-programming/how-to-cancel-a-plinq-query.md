---
title: 'Porady: anulowanie zapytania PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: 1b34f0c1785c1a1c007db97f04c799a4b4bd0f8f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588574"
---
# <a name="how-to-cancel-a-plinq-query"></a>Porady: anulowanie zapytania PLINQ
Poniższe przykłady pokazują dwa sposoby anulowania kwerendy PLINQ. W pierwszym przykładzie pokazano, jak anulować kwerendę, która składa się głównie z przechodzenia danych. W drugim przykładzie pokazano, jak anulować kwerendę, która zawiera funkcję użytkownika, która jest kosztowna pod względem obliczeniowym.

> [!NOTE]
> Gdy "Tylko mój kod" jest włączona, Visual Studio zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z napisem "wyjątek nie obsługiwany przez kod użytkownika". Ten błąd jest łagodny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, które jest pokazane w poniższych przykładach. Aby zapobiec przerywaniu pierwszego błędu w programie Visual Studio, po prostu wyczyść pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.
>
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do kwerendy obiektów. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszania w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Przykład

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

Struktura PLINQ nie toczy <xref:System.OperationCanceledException> ani <xref:System.AggregateException?displayProperty=nameWithType>jednego w ; <xref:System.OperationCanceledException> muszą być obsługiwane w oddzielnym bloku połowowym. Jeśli jeden lub więcej delegatów użytkownika zgłasza OperationCanceledException(externalCT) <xref:System.Threading.CancellationToken?displayProperty=nameWithType>(przy użyciu zewnętrznego), ale nie `AsParallel().WithCancellation(externalCT)`ma innego wyjątku, <xref:System.OperationCanceledException> a kwerenda została <xref:System.AggregateException?displayProperty=nameWithType>zdefiniowana jako , plinq wyda pojedynczy (externalCT) zamiast . Jednak jeśli jeden delegat użytkownika <xref:System.OperationCanceledException>zgłasza , a inny delegat zgłasza inny typ wyjątku, a następnie oba wyjątki zostaną zwinięte w . <xref:System.AggregateException>

Ogólne wytyczne dotyczące anulowania są następujące:

1. W przypadku anulowania delegowania użytkownika należy poinformować <xref:System.Threading.CancellationToken> PLINQ o zewnętrznej i rzucać <xref:System.OperationCanceledException>(externalCT).

2. Jeśli nastąpi anulowanie i nie są zgłaszane żadne <xref:System.OperationCanceledException> inne <xref:System.AggregateException>wyjątki, należy obsłużyć zamiast .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak obsługiwać anulowanie, gdy masz funkcje obliczeniowo drogie w kodzie użytkownika.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Podczas obsługi anulowania w kodzie użytkownika, <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nie trzeba używać w definicji kwerendy. Jednak zaleca się, aby <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> to zrobić, ponieważ nie ma wpływu na wydajność kwerendy i umożliwia anulowanie do obsługi przez operatorów zapytań i kodu użytkownika.

Aby zapewnić szybkość reakcji systemu, zaleca się sprawdzenie, czy anulowanie jest około raz na milisekundę; jednak każdy okres do 10 milisekund jest uważany za dopuszczalny. Ta częstotliwość nie powinna mieć negatywnego wpływu na wydajność kodu.

Gdy wyliczacz jest usuwany, na przykład, gdy kod wyłamuje się z foreach (Dla każdego w języku Visual Basic) pętli, która jest iteracji przez wyniki kwerendy, a następnie kwerenda jest anulowana, ale nie wyjątek.

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md)
