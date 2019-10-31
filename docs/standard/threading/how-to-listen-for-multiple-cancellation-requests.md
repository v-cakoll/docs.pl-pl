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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138010"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="460c4-102">Porady: nasłuchiwanie wielu żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="460c4-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="460c4-103">Ten przykład pokazuje, jak nasłuchiwać dwóch tokenów anulowania jednocześnie, aby anulować operację, jeśli token zażąda.</span><span class="sxs-lookup"><span data-stu-id="460c4-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="460c4-104">Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika".</span><span class="sxs-lookup"><span data-stu-id="460c4-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="460c4-105">Ten błąd jest niegroźny.</span><span class="sxs-lookup"><span data-stu-id="460c4-105">This error is benign.</span></span> <span data-ttu-id="460c4-106">Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="460c4-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="460c4-107">Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="460c4-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="460c4-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="460c4-108">Example</span></span>  
 <span data-ttu-id="460c4-109">W poniższym przykładzie metoda <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> służy do przyłączania dwóch tokenów do jednego tokenu.</span><span class="sxs-lookup"><span data-stu-id="460c4-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="460c4-110">Umożliwia to przekazywanie tokenu do metod, które mają tylko jeden token anulowania jako argument.</span><span class="sxs-lookup"><span data-stu-id="460c4-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="460c4-111">W przykładzie pokazano typowy scenariusz, w którym metoda musi obserwować zarówno token przekazaną spoza klasy, jak i token wygenerowany wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="460c4-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="460c4-112">Gdy połączony token zgłasza <xref:System.OperationCanceledException>, token, który jest przesyłany do wyjątku jest połączonym tokenem, a nie tokenem poprzednika.</span><span class="sxs-lookup"><span data-stu-id="460c4-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="460c4-113">Aby określić, które z tokenów zostało anulowane, sprawdź stan tokenów poprzedników bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="460c4-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="460c4-114">W tym przykładzie <xref:System.AggregateException> nigdy nie powinny być zgłaszane, ale jest przechwytywane tutaj, ponieważ w rzeczywistych scenariuszach wszystkie inne wyjątki niż <xref:System.OperationCanceledException>, które są generowane przez delegata zadania, są opakowane w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="460c4-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="460c4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="460c4-115">See also</span></span>

- [<span data-ttu-id="460c4-116">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="460c4-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
