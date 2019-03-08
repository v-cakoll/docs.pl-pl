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
ms.openlocfilehash: 17874b8b9733ea18d4877e2c79810fcd6247db0b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680242"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Instrukcje: Nasłuchiwanie wielu żądań anulowania
W tym przykładzie pokazano, jak do nasłuchiwania dwa tokeny anulowania jednocześnie tak, aby anulować operację, jeśli żądanie albo tokenu.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" Visual Studio, w niektórych przypadkach przerwania w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest nieszkodliwe. Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda jest używany do łączenia dwóch tokenów do jednego tokenu. Dzięki temu tokenów, które mają być przekazane do metody, które przyjmują odwołania tylko jeden token jako argument. W przykładzie przedstawiono typowy scenariusz, w którym metoda musi być zgodna z obu tokenu, przekazywane z poza klasy i token, który został on wygenerowany wewnątrz klasy.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Kiedy wyrzuca token połączony <xref:System.OperationCanceledException>, token, który jest przekazywany do wyjątku jest token połączony, nie albo tokenów poprzednika. Aby określić, które tokeny zostało anulowane, sprawdź stan tokenów poprzednika bezpośrednio.  
  
 W tym przykładzie <xref:System.AggregateException> powinna być nigdy nie były zgłaszane, ale jej padł w tym miejscu ponieważ w rzeczywistych scenariuszach innych wyjątków, oprócz <xref:System.OperationCanceledException> , są generowane przez delegata zadania są opakowane w <xref:System.AggregateException>.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
