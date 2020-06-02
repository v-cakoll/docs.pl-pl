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
ms.openlocfilehash: 0482d43925f4f547114119a95909501cbf09eedb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279365"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Porady: rejestrowanie wywołań zwrotnych żądań anulowania
Poniższy przykład pokazuje, jak zarejestrować delegata, który zostanie wywołany, gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Właściwość zostanie prawdziwa, z powodu wywołania do <xref:System.Threading.CancellationTokenSource.Cancel%2A> obiektu, który utworzył token. Ta technika służy do anulowania operacji asynchronicznych, które nie obsługują natywnie ujednoliconej platformy anulowania oraz dla odblokowania metod, które mogą oczekiwać na zakończenie operacji asynchronicznej.  
  
> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Net.WebClient.CancelAsync%2A> Metoda jest zarejestrowana jako metoda do wywołania w przypadku żądania anulowania za pomocą tokenu anulowania.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Jeśli po zarejestrowaniu wywołania zwrotnego zostało już zgłoszone żądanie anulowania, wywołanie zwrotne jest nadal gwarantowane. W tym konkretnym przypadku <xref:System.Net.WebClient.CancelAsync%2A> Metoda nie będzie niczego robić, jeśli żadna operacja asynchroniczna nie jest w toku, więc zawsze jest bezpieczna do wywołania metody.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](cancellation-in-managed-threads.md)
