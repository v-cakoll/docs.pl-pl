---
title: 'Instrukcje: Nasłuchiwanie wielu żądań anulowania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2684f0fd43f84573933fc0a7107ce4f9035bc092
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913306"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Instrukcje: Nasłuchiwanie wielu żądań anulowania
Ten przykład pokazuje, jak nasłuchiwać dwóch tokenów anulowania jednocześnie, aby anulować operację, jeśli token zażąda.  
  
> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> Metoda jest używana do przyłączania dwóch tokenów do jednego tokenu. Umożliwia to przekazywanie tokenu do metod, które mają tylko jeden token anulowania jako argument. W przykładzie pokazano typowy scenariusz, w którym metoda musi obserwować zarówno token przekazaną spoza klasy, jak i token wygenerowany wewnątrz klasy.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Gdy połączony token zgłasza <xref:System.OperationCanceledException>, token, który jest przesyłany do wyjątku jest połączonym tokenem, a nie tokenem poprzednika. Aby określić, które z tokenów zostało anulowane, sprawdź stan tokenów poprzedników bezpośrednio.  
  
 W tym przykładzie <xref:System.AggregateException> nigdy nie powinno być zgłaszane, ale jest przechwytywane tutaj, ponieważ w rzeczywistych scenariuszach wszystkie inne wyjątki niż <xref:System.OperationCanceledException> te, które zostały zgłoszone przez <xref:System.AggregateException>delegata zadania, są opakowane w.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
