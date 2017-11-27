---
title: "Porady: nasłuchiwanie wielu żądań anulowania"
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
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="5f74c-102">Porady: nasłuchiwanie wielu żądań anulowania</span><span class="sxs-lookup"><span data-stu-id="5f74c-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="5f74c-103">W tym przykładzie przedstawiono sposób słuchać dwa tokeny anulowania jednocześnie tak, aby anulować operację, jeśli albo token żądania.</span><span class="sxs-lookup"><span data-stu-id="5f74c-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f74c-104">Po włączeniu "Tylko mój kod" programu Visual Studio w niektórych przypadkach będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika."</span><span class="sxs-lookup"><span data-stu-id="5f74c-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="5f74c-105">Ten błąd jest niegroźne.</span><span class="sxs-lookup"><span data-stu-id="5f74c-105">This error is benign.</span></span> <span data-ttu-id="5f74c-106">Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="5f74c-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="5f74c-107">Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.</span><span class="sxs-lookup"><span data-stu-id="5f74c-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f74c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f74c-108">Example</span></span>  
 <span data-ttu-id="5f74c-109">W poniższym przykładzie <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> metoda jest używana do przyłączenia dwa tokeny do jednego tokenu.</span><span class="sxs-lookup"><span data-stu-id="5f74c-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="5f74c-110">Dzięki temu token mają być przekazane do metody przyjmujących token jako argument tylko jeden anulowania.</span><span class="sxs-lookup"><span data-stu-id="5f74c-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="5f74c-111">W przykładzie pokazano typowy scenariusz, w którym metody muszą przestrzegać zarówno token przekazanych z poza klasą a token wygenerowany wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="5f74c-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="5f74c-112">Gdy generuje token połączony <xref:System.OperationCanceledException>, token, który jest przekazywany do wyjątku jest token połączony, nie albo tokenów poprzednik.</span><span class="sxs-lookup"><span data-stu-id="5f74c-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="5f74c-113">Aby ustalić, które tokenów zostało anulowane, sprawdź stan tokenów poprzednik bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="5f74c-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="5f74c-114">W tym przykładzie <xref:System.AggregateException> nigdy nie powinien zostać zgłoszony, ale go tutaj zostanie przechwycony ponieważ w rzeczywistych scenariuszach pozostałe wyjątki, oprócz <xref:System.OperationCanceledException> które są generowane z delegat zadań są ujęte w <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="5f74c-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f74c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f74c-115">See Also</span></span>  
 [<span data-ttu-id="5f74c-116">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="5f74c-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
