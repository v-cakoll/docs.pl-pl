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
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="a8d33-102">Porady: nasłuchiwanie wielu żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="a8d33-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="a8d33-103">W tym przykładzie pokazano, jak nasłuchiwać dwóch tokenów anulowania jednocześnie, dzięki czemu można anulować operację, jeśli token zażąda go.</span><span class="sxs-lookup"><span data-stu-id="a8d33-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8d33-104">Gdy opcja "Tylko mój kod" jest włączona, visual studio w niektórych przypadkach zostanie przerwana w wierszu, który zgłasza wyjątek i wyświetli komunikat o błędzie z komunikatem "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="a8d33-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="a8d33-105">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="a8d33-105">This error is benign.</span></span> <span data-ttu-id="a8d33-106">Można nacisnąć klawisz F5, aby kontynuować z niego i zobacz zachowanie obsługi wyjątków, który jest pokazany w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="a8d33-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="a8d33-107">Aby zapobiec przerywaniu pierwszego błędu przez program Visual Studio, wystarczy odznaczyć pole wyboru "Tylko mój kod" w obszarze **Narzędzia, Opcje, Debugowanie, Ogólne**.</span><span class="sxs-lookup"><span data-stu-id="a8d33-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8d33-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8d33-108">Example</span></span>  
 <span data-ttu-id="a8d33-109">W poniższym <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> przykładzie metoda jest używana do łączenia dwóch tokenów w jeden token.</span><span class="sxs-lookup"><span data-stu-id="a8d33-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="a8d33-110">Dzięki temu token, który ma zostać przekazany do metod, które przyjmują tylko jeden token anulowania jako argument.</span><span class="sxs-lookup"><span data-stu-id="a8d33-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="a8d33-111">W przykładzie przedstawiono typowy scenariusz, w którym metoda musi obserwować zarówno token przekazany spoza klasy, jak i token wygenerowany wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="a8d33-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="a8d33-112">Gdy połączony token zgłasza <xref:System.OperationCanceledException>, token, który jest przekazywany do wyjątku jest token emisyjny, a nie jeden z tokenów poprzednika.</span><span class="sxs-lookup"><span data-stu-id="a8d33-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="a8d33-113">Aby ustalić, który z tokenów został anulowany, sprawdź stan tokenów poprzednika bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="a8d33-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="a8d33-114">W tym <xref:System.AggregateException> przykładzie nigdy nie powinny być generowane, ale jest złowionych w <xref:System.OperationCanceledException> tym miejscu, ponieważ w rzeczywistych scenariuszach wszelkie inne wyjątki oprócz tego, które są generowane z delegata zadania są opakowane w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="a8d33-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d33-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8d33-115">See also</span></span>

- [<span data-ttu-id="a8d33-116">Anulowanie w wątkach zarządzanych</span><span class="sxs-lookup"><span data-stu-id="a8d33-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
