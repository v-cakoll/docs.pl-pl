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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16ba8000544d0b7d35a818d41a75f38e6fd0293d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178572"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="d7272-102">Porady: nasłuchiwanie wielu żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="d7272-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="d7272-103">W tym przykładzie pokazano, jak do nasłuchiwania dwa tokeny anulowania jednocześnie tak, aby anulować operację, jeśli żądanie albo tokenu.</span><span class="sxs-lookup"><span data-stu-id="d7272-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7272-104">Po włączeniu "Tylko mój kod" Visual Studio, w niektórych przypadkach przerwania w wierszu, który zgłasza wyjątek i wyświetlić komunikat o błędzie informujący, że "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="d7272-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="d7272-105">Ten błąd jest nieszkodliwe.</span><span class="sxs-lookup"><span data-stu-id="d7272-105">This error is benign.</span></span> <span data-ttu-id="d7272-106">Naciśnij klawisz F5, aby nadal z niego i wyświetlić zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="d7272-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="d7272-107">Aby zapobiec istotne w przypadku pierwszego błędu programu Visual Studio, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="d7272-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7272-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7272-108">Example</span></span>  
 <span data-ttu-id="d7272-109">W poniższym przykładzie <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda jest używany do łączenia dwóch tokenów do jednego tokenu.</span><span class="sxs-lookup"><span data-stu-id="d7272-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="d7272-110">Dzięki temu tokenów, które mają być przekazane do metody, które przyjmują odwołania tylko jeden token jako argument.</span><span class="sxs-lookup"><span data-stu-id="d7272-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="d7272-111">W przykładzie przedstawiono typowy scenariusz, w którym metoda musi być zgodna z obu tokenu, przekazywane z poza klasy i token, który został on wygenerowany wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="d7272-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="d7272-112">Kiedy wyrzuca token połączony <xref:System.OperationCanceledException>, token, który jest przekazywany do wyjątku jest token połączony, nie albo tokenów poprzednika.</span><span class="sxs-lookup"><span data-stu-id="d7272-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="d7272-113">Aby określić, które tokeny zostało anulowane, sprawdź stan tokenów poprzednika bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="d7272-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="d7272-114">W tym przykładzie <xref:System.AggregateException> powinna być nigdy nie były zgłaszane, ale jej padł w tym miejscu ponieważ w rzeczywistych scenariuszach innych wyjątków, oprócz <xref:System.OperationCanceledException> , są generowane przez delegata zadania są opakowane w <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="d7272-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7272-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7272-115">See also</span></span>

- [<span data-ttu-id="d7272-116">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="d7272-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
