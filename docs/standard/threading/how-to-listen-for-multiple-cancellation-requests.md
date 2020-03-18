---
title: 'Porady: nasłuchiwanie wielu żądań anulowania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: e35472040b6ee1263ebc4c4968fa1822045a2064
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138010"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Porady: nasłuchiwanie wielu żądań anulowania
W tym przykładzie pokazano, jak nasłuchiwać dwóch tokenów anulowania jednocześnie, dzięki czemu można anulować operację, jeśli token zażąda go.  
  
> [!NOTE]
> Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach. Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> przykładzie metoda jest używana do łączenia dwóch tokenów w jeden token. Dzięki temu token, który ma zostać przekazany do metod, które przyjmują tylko jeden token anulowania jako argument. W przykładzie przedstawiono typowy scenariusz, w którym metoda musi obserwować zarówno token przekazany spoza klasy, jak i token wygenerowany wewnątrz klasy.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Gdy połączony token zgłasza <xref:System.OperationCanceledException>, token, który jest przekazywany do wyjątku jest token emisyjny, a nie jeden z tokenów poprzednika. Aby ustalić, który z tokenów został anulowany, sprawdź stan tokenów poprzednika bezpośrednio.  
  
 W tym <xref:System.AggregateException> przykładzie nigdy nie powinny być generowane, ale jest złowionych w <xref:System.OperationCanceledException> tym miejscu, ponieważ w rzeczywistych scenariuszach wszelkie inne wyjątki oprócz tego, które są generowane z delegata zadania są opakowane w <xref:System.AggregateException>.  
  
## <a name="see-also"></a>Zobacz też

- [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md)
