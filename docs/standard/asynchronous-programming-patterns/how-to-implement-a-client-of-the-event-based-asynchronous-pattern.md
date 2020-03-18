---
title: 'Porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "69950717"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="52111-102">Porady: implementacja klienta wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="52111-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="52111-103">W poniższym przykładzie kodu pokazano, jak używać składnika, który jest zgodny z [omówieniem asynchronicznego wzorca opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52111-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="52111-104">Formularz w tym przykładzie `PrimeNumberCalculator` używa składnika opisanego w [jak: Implementowanie składnika, który obsługuje asynchroniczny wzorzec oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="52111-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="52111-105">Po uruchomieniu projektu, który używa tego przykładu, zostanie wyświetlony formularz "Kalkulator liczb pierwszych" z siatką i dwoma przyciskami: **Rozpocznij nowe zadanie** i **Anuluj**.</span><span class="sxs-lookup"><span data-stu-id="52111-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="52111-106">Można kliknąć przycisk **Rozpocznij nowe zadanie** kilka razy z rzędu, a dla każdego kliknięcia operacja asynchroniczna rozpocznie obliczenia, aby ustalić, czy losowo wygenerowany numer testu jest pierwszorzędny.</span><span class="sxs-lookup"><span data-stu-id="52111-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="52111-107">Formularz będzie okresowo wyświetlał postęp i wyniki przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="52111-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="52111-108">Każdej operacji przypisywany jest unikatowy identyfikator zadania.</span><span class="sxs-lookup"><span data-stu-id="52111-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="52111-109">Wynik obliczeń jest wyświetlany w **kolumnie Wynik;** jeśli numer testowy nie jest pierwszy, jest oznaczony jako **Composite,** a jego pierwszy dzielnik jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="52111-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="52111-110">Każdą oczekującą operację można anulować za pomocą przycisku **Anuluj.**</span><span class="sxs-lookup"><span data-stu-id="52111-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="52111-111">Można dokonywać wielu selekcji.</span><span class="sxs-lookup"><span data-stu-id="52111-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52111-112">Większość liczb nie będzie pierwszorzędna.</span><span class="sxs-lookup"><span data-stu-id="52111-112">Most numbers will not be prime.</span></span> <span data-ttu-id="52111-113">Jeśli po kilku zakończonych operacjach nie znaleziono liczby pierwszej, po prostu uruchom więcej zadań, a ostatecznie znajdziesz kilka liczb pierwszych.</span><span class="sxs-lookup"><span data-stu-id="52111-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52111-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="52111-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="52111-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52111-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
