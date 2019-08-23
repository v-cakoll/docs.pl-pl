---
title: 'Instrukcje: Anulowanie zapytania PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce6616d576263db7dce6cf7e52582ee3400d80d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962534"
---
# <a name="how-to-cancel-a-plinq-query"></a>Instrukcje: Anulowanie zapytania PLINQ
W poniższych przykładach pokazano dwa sposoby anulowania zapytania PLINQ. Pierwszy przykład pokazuje, jak anulować zapytanie, które składa się głównie z przechodzenia do danych. Drugi przykład pokazuje, jak anulować zapytanie zawierające funkcję użytkownika, która jest w praktyce kosztowna.  
  
> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio przerwie w wierszu, który zgłasza wyjątek, i wyświetla komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.  
>   
>  Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 Struktura PLINQ nie jest rzutowana <xref:System.OperationCanceledException> <xref:System.AggregateException?displayProperty=nameWithType>na; <xref:System.OperationCanceledException> musi być obsługiwana w oddzielnym bloku catch. Jeśli co najmniej jeden delegat użytkownika zgłosi OperationCanceledException (externalCT) (przy użyciu zewnętrznego <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale nie inny wyjątek, a zapytanie zostało zdefiniowane jako `AsParallel().WithCancellation(externalCT)`, a następnie PLINQ wystawia jeden <xref:System.OperationCanceledException> (externalCT), a nie <xref:System.AggregateException?displayProperty=nameWithType>. Jeśli jednak jeden delegat użytkownika zgłosi <xref:System.OperationCanceledException>, a inny delegat zgłosi inny typ wyjątku, oba wyjątki zostaną przeagregowane <xref:System.AggregateException>do.  
  
 Ogólne wskazówki dotyczące anulowania są następujące:  
  
1. W przypadku wykonywania anulowania delegowania przez <xref:System.Threading.CancellationToken> <xref:System.OperationCanceledException>użytkownika należy poinformować PLINQ o zewnętrznym i wyrzucaniu (externalCT).  
  
2. Jeśli wystąpiło anulowanie i nie są zgłaszane żadne inne wyjątki, należy obsłużyć <xref:System.OperationCanceledException> zamiast. <xref:System.AggregateException>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak obsłużyć anulowanie, gdy w kodzie użytkownika znajduje się Funkcja obliczeniowa kosztowna.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 W przypadku obsługi anulowania w kodzie użytkownika nie trzeba używać <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> w definicji zapytania. Zaleca się jednak, aby to zrobić, ponieważ <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nie ma wpływu na wydajność zapytań i umożliwia anulowanie obsługi przez operatory zapytań oraz kod użytkownika.  
  
 Aby zapewnić czas odpowiedzi systemu, zalecamy sprawdzenie, czy anulowanie ma być anulowane dla każdego milisekundu; Jednak okres do 10 milisekund jest uznawany za akceptowalny. Ta częstotliwość nie powinna mieć negatywnego wpływu na wydajność kodu.  
  
 Gdy moduł wyliczający jest usuwany, na przykład w przypadku przerwania kodu z pętli foreach (dla każdej w Visual Basic), która iteruje względem wyników zapytania, zapytanie zostanie anulowane, ale nie zostanie zgłoszony żaden wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
