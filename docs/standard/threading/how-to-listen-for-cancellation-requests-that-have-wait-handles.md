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
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137988"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania
Jeśli metoda jest zablokowana, gdy oczekuje na zdarzenie, które mają być sygnalizowane, nie można sprawdzić wartość tokenu anulowania i odpowiedzieć w odpowiednim czasie. W pierwszym przykładzie pokazano, jak rozwiązać ten problem <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> podczas pracy ze zdarzeniami, takimi jak które nie obsługują natywnie ujednoliconej struktury anulowania. Drugi przykład pokazuje bardziej uproszczone <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>podejście, które używa , który obsługuje ujednolicone anulowanie.  
  
> [!NOTE]
> Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach. Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym <xref:System.Threading.ManualResetEvent> przykładzie użyto do wykazania, jak odblokować uchwyty oczekiwania, które nie obsługują ujednoliconeanulowanie.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Przykład  
 W poniższym <xref:System.Threading.ManualResetEventSlim> przykładzie użyto do wykazania, jak odblokować prymitywy koordynacji, które obsługują ujednolicone anulowanie. To samo podejście może być stosowane z innymi lekkimi prymitywami koordynacyjnymi, takimi jak <xref:System.Threading.Semaphore> `Slim` i <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md)
