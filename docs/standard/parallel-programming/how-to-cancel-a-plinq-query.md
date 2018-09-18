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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5008ede5054e8e6970bcb6f804fa1888244238f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973095"
---
# <a name="how-to-cancel-a-plinq-query"></a>Porady: anulowanie zapytania PLINQ
W poniższych przykładach pokazano dwa sposoby Anulowanie zapytania PLINQ. Pierwszy przykład pokazuje, jak anulować kwerendę, która składa się przede wszystkim z przechodzenia danych. Drugi przykład pokazuje, jak anulować kwerendę, która zawiera funkcję użytkownika, która jest obliczeniowo kosztowne.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" Visual Studio będzie przerwania w wierszu, który zgłasza wyjątek i wyświetlać komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest nieszkodliwe. Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
>   
>  W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty. Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 PLINQ framework nieoperacyjnym pojedynczej <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> muszą być obsługiwane w bloku catch oddzielne. Jeśli co najmniej jeden delegatów użytkownika zgłasza OperationCanceledException(externalCT) (przy użyciu zewnętrznego <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale nie innych wyjątków i zapytania została zdefiniowana jako `AsParallel().WithCancellation(externalCT)`, PLINQ wystawi jeden, a następnie <xref:System.OperationCanceledException> (externalCT) zamiast <xref:System.AggregateException?displayProperty=nameWithType>. Jednak jeśli delegowanie jeden użytkownik zgłasza <xref:System.OperationCanceledException>, delegowanego innego zgłasza inny typ wyjątku, a następnie zarówno wyjątki zostanie wycofana do <xref:System.AggregateException>.  
  
 Ogólne wskazówki na temat anulowania jest następująca:  
  
1.  Jeśli wykonujesz anulowania pełnomocnika użytkownika informowało PLINQ o zewnętrznej <xref:System.Threading.CancellationToken> i zgłosić <xref:System.OperationCanceledException>(externalCT).  
  
2.  Jeśli żadne inne wyjątki są zgłaszane następuje anulowanie, następnie należy obsługiwać <xref:System.OperationCanceledException> zamiast <xref:System.AggregateException>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób obsługi anulowania, gdy masz obciążającymi funkcji w kodzie użytkownika.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Podczas obsługi anulowania w kodzie użytkownika, nie trzeba używać <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> w definicji podzapytania. Jednak zaleca się, możesz to zrobić, ponieważ <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nie ma wpływu na wydajność zapytań i umożliwia anulowanie, które mają być obsługiwane przez operatorów zapytań, a kod użytkownika.  
  
 Aby zapewnić czas reakcji systemu, zaleca się sprawdzenie, czy anulowania wokół raz na milisekundę; Jednak każdy okres, maksymalnie 10 milisekund jest uważany za akceptowalne. Tę częstotliwość nie powinna mieć negatywny wpływ na wydajność kodu.  
  
 Po usunięciu moduł wyliczający, na przykład gdy kodu przerywa poza pętlę foreach (dla każdego w języku Visual Basic), która jest Iterowanie wyników zapytania, a następnie zapytanie zostało anulowane, ale jest zgłaszany żaden wyjątek.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable>  
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
