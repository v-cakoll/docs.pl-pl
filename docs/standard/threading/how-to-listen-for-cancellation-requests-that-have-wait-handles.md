---
title: 'Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6543c2e5ea953887e699ee6f9ca3b70e08e5ae85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583919"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania
Metody zostało zablokowane, gdy oczekuje na zdarzenie, aby zostać zgłoszony, nie można sprawdzić wartość token anulowania ani odpowiadają w odpowiednim czasie. Pierwszym przykładzie pokazano, jak rozwiązać ten problem, podczas pracy ze zdarzeniami takich jak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> które nie obsługują natywnie framework ujednoliconego anulowania. Drugi przykład przedstawia usprawnić podejście, która używa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, który obsługuje unified anulowania.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" programu Visual Studio w niektórych przypadkach będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest niegroźne. Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Threading.ManualResetEvent> aby zademonstrować sposób odblokowania uchwyty oczekiwania, które nie obsługują ujednoliconego anulowania.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Threading.ManualResetEventSlim> pokazujący sposób odblokować koordynacji podstawowych, które obsługują unified anulowania. Te same podejście może być używany z innych podstawowych koordynacji lekkie, takich jak <xref:System.Threading.Semaphore> `Slim` i <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Zobacz też  
 [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
