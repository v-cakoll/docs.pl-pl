---
title: "Porady: rejestrowanie wywołań zwrotnych żądań anulowania"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Porady: rejestrowanie wywołań zwrotnych żądań anulowania
Poniższy przykład przedstawia sposób rejestrowania delegata, który będzie wywoływany, gdy <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości jest spełniony wskutek wywołania <xref:System.Threading.CancellationTokenSource.Cancel%2A> dla obiektu, który utworzył token. Użyj tej metody dla anulowania operacji asynchronicznych, które nie obsługują natywnie framework ujednoliconego anulowania, a także metod odblokowywania, które może być oczekiwanie na zakończenie operacji asynchronicznych.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" programu Visual Studio w niektórych przypadkach będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest niegroźne. Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Net.WebClient.CancelAsync%2A> metody jest zarejestrowany jako metodę do wywołania w przypadku anulowania żądania za pośrednictwem token anulowania.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Jeśli już zażądano anulowania, gdy wywołanie zwrotne jest zarejestrowany, nadal jest gwarantowane można wywołać metodę wywołania zwrotnego. W tym przypadku <xref:System.Net.WebClient.CancelAsync%2A> — metoda nie przynosi Jeśli nie asynchroniczne jest operacja w toku, dzięki czemu jest zawsze bezpieczne wywołania metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
