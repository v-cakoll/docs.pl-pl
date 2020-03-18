---
title: 'Porady: rejestrowanie wywołań zwrotnych żądań anulowania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: 87ba1ab9ac095c733a53f766d00ebb7530a8d9c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137999"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Porady: rejestrowanie wywołań zwrotnych żądań anulowania
W poniższym przykładzie pokazano, jak zarejestrować pełnomocnika, który zostanie wywołany, gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość staje się true ze względu <xref:System.Threading.CancellationTokenSource.Cancel%2A> na wywołanie na obiekcie, który utworzył token. Ta technika służy do anulowania operacji asynchronicznych, które nie obsługują natywnie ujednoliconej struktury anulowania i dla metod odblokowywania, które mogą czekać na zakończenie operacji asynchronicznej.  
  
> [!NOTE]
> Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach. Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Net.WebClient.CancelAsync%2A> metoda jest zarejestrowana jako metoda, która ma być wywoływana, gdy anulowanie jest wymagane za pośrednictwem tokenu anulowania.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Jeśli anulowanie zostało już poproszone, gdy wywołanie wywołania odwetowe jest zarejestrowane, wywołanie wywołania wywołania wywołania wywołania jest nadal gwarantowane do wywołania. W tym konkretnym <xref:System.Net.WebClient.CancelAsync%2A> przypadku metoda nie zrobi nic, jeśli nie jest w toku żadna operacja asynchroniczna, więc zawsze można bezpiecznie wywołać metodę.  
  
## <a name="see-also"></a>Zobacz też

- [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md)
