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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137999"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Porady: rejestrowanie wywołań zwrotnych żądań anulowania
Poniższy przykład pokazuje, jak zarejestrować delegata, który zostanie wywołany, gdy właściwość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> będzie prawdziwa, z powodu wywołania <xref:System.Threading.CancellationTokenSource.Cancel%2A> na obiekcie, który utworzył token. Ta technika służy do anulowania operacji asynchronicznych, które nie obsługują natywnie ujednoliconej platformy anulowania oraz dla odblokowania metod, które mogą oczekiwać na zakończenie operacji asynchronicznej.  
  
> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie metoda <xref:System.Net.WebClient.CancelAsync%2A> jest zarejestrowana jako metoda do wywołania w przypadku żądania anulowania za pomocą tokenu anulowania.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Jeśli po zarejestrowaniu wywołania zwrotnego zostało już zgłoszone żądanie anulowania, wywołanie zwrotne jest nadal gwarantowane. W tym konkretnym przypadku Metoda <xref:System.Net.WebClient.CancelAsync%2A> nie będzie niczego robić, jeśli żadna operacja asynchroniczna nie jest w toku, więc zawsze jest bezpieczna do wywołania metody.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
