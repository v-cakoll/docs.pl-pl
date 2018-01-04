---
title: 'Porady: anulowanie zapytania PLINQ'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5ed3d38cdfd70e7588ba0c4d94816c7105c7cf3e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-cancel-a-plinq-query"></a>Porady: anulowanie zapytania PLINQ
W poniższych przykładach pokazano dwa sposoby Anulowanie zapytania PLINQ. Pierwszym przykładzie pokazano, jak można anulować kwerendę, która składa się przede wszystkim z przechodzenie danych. Drugim przykładzie pokazano, jak można anulować kwerendę, która zawiera funkcję użytkownika, która jest kosztowna w praktyce.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" programu Visual Studio będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest niegroźne. Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
>   
>  W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 PLINQ framework nie Przywracanie pojedynczego <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> muszą być obsługiwane w bloku catch oddzielne. Jeśli co najmniej jeden użytkownik delegatów zgłasza OperationCanceledException(externalCT) (przy użyciu zewnętrznego <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale nie inne wyjątku i zapytania został zdefiniowany jako `AsParallel().WithCancellation(externalCT)`, następnie PLINQ wystawi pojedynczy <xref:System.OperationCanceledException> (externalCT) zamiast <xref:System.AggregateException?displayProperty=nameWithType>. Jednak jeśli delegowanie jeden użytkownik zgłasza <xref:System.OperationCanceledException>i delegowanego innego zgłasza innego typu wyjątku, a następnie będzie przeprowadzana zarówno wyjątki <xref:System.AggregateException>.  
  
 Ogólne wskazówki dotyczące anulowania jest następujący:  
  
1.  W przypadku anulowania delegowanie użytkownika powinien informować PLINQ o zewnętrznej <xref:System.Threading.CancellationToken> i zgłosić <xref:System.OperationCanceledException>(externalCT).  
  
2.  Jeśli występuje anulowania, a nie inne wyjątki są zgłaszane, następnie należy powinna obsługiwać <xref:System.OperationCanceledException> zamiast <xref:System.AggregateException>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób obsługi anulowania, gdy funkcja praktyce kosztowne w kodzie użytkownika.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Podczas obsługi anulowania w kodzie użytkownika, nie trzeba użyć <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> w definicji zapytania. Jednak zaleca się, że można to zrobić, ponieważ <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nie ma wpływu na wydajność zapytań i umożliwia anulowanie mają być obsługiwane przez operatorów zapytań i kodu użytkownika.  
  
 Aby zapewnić czas reakcji systemu, firma Microsoft zaleca, wyszukaj anulowania wokół raz dla milisekund; Jednak każdy okres maksymalnie 10 milisekund jest uważany za akceptowalne. Tej częstotliwości nie powinna mieć negatywny wpływ na wydajność kodu.  
  
 Jeśli moduł wyliczający zostanie usunięty, na przykład jeśli kod dzieli poza pętli foreach (dla każdej z nich w Visual Basic), która jest iteracja w wynikach zapytania, a następnie zapytanie zostało anulowane, ale nie wyjątku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.ParallelEnumerable>  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
