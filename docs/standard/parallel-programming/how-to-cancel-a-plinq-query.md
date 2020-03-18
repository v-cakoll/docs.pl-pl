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
ms.openlocfilehash: 272f25d62cb63c60209be3bc54dc5e76fb30df54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134230"
---
# <a name="how-to-cancel-a-plinq-query"></a>Porady: anulowanie zapytania PLINQ
W poniższych przykładach przedstawiono dwa sposoby anulowania kwerendy PLINQ. W pierwszym przykładzie pokazano, jak anulować kwerendę, która składa się głównie z przechodzenia danych. W drugim przykładzie pokazano, jak anulować kwerendę, która zawiera funkcję użytkownika, która jest obliczeniowo drogie.

> [!NOTE]
> Gdy opcja "Tylko mój kod" jest włączona, program Visual Studio zostanie przerwany w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach. Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.
>
> W tym przykładzie jest przeznaczony do wykazania użycia i nie może działać szybciej niż równoważne sekwencyjne LINQ do objects kwerendy. Aby uzyskać więcej informacji na temat przyspieszenia, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Przykład

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

Struktura PLINQ nie toczy <xref:System.OperationCanceledException> się <xref:System.AggregateException?displayProperty=nameWithType>w jeden ; <xref:System.OperationCanceledException> musi być obsługiwany w oddzielnym bloku zaczepu. Jeśli jeden lub więcej delegatów użytkownika zgłasza OperationCanceledException(externalCT) (przy <xref:System.Threading.CancellationToken?displayProperty=nameWithType>użyciu zewnętrznego), ale `AsParallel().WithCancellation(externalCT)`nie ma innego wyjątku, <xref:System.OperationCanceledException> a kwerenda została <xref:System.AggregateException?displayProperty=nameWithType>zdefiniowana jako , następnie PLINQ wyda jeden (externalCT) zamiast . Jednak jeśli jeden delegat użytkownika <xref:System.OperationCanceledException>zgłasza , a inny delegat zgłasza inny typ wyjątku, <xref:System.AggregateException>a następnie oba wyjątki zostaną zwinięte w .

Ogólne wytyczne dotyczące anulowania są następujące:

1. W przypadku wykonywania anulowania delegata użytkownika należy poinformować PLINQ o zewnętrznych <xref:System.Threading.CancellationToken> i wyrzuć <xref:System.OperationCanceledException>(externalCT).

2. Jeśli nastąpi anulowanie i nie zostaną wygenerowane <xref:System.OperationCanceledException> żadne inne <xref:System.AggregateException>wyjątki, należy obsłużyć zamiast .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak obsługiwać anulowanie, gdy masz funkcję kosztowną obliczeniowo w kodzie użytkownika.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Podczas obsługi anulowania w kodzie użytkownika, nie <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> trzeba używać w definicji kwerendy. Jednak zaleca się, aby to <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> zrobić, ponieważ nie ma wpływu na wydajność kwerendy i umożliwia anulowanie obsługiwane przez operatory zapytań i kodu użytkownika.

W celu zapewnienia reakcji systemu, zaleca się sprawdzenie anulowania około raz na milisekundę; jednak każdy okres do 10 milisekund jest uważany za dopuszczalny. Ta częstotliwość nie powinna mieć negatywnego wpływu na wydajność kodu.

Gdy wyliczacz jest usuwany, na przykład, gdy kod rozbija się z foreach (For Each in Visual Basic) pętli, która jest iteracji nad wynikami kwerendy, a następnie kwerenda jest anulowana, ale nie wyjątek.

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md)
