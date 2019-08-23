---
title: 'Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach'
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
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950717"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="9bc2e-102">Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="9bc2e-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="9bc2e-103">Poniższy przykład kodu ilustruje sposób użycia składnika, który jest zgodny z [omówieniem asynchronicznego wzorca opartego](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="9bc2e-104">W formularzu dla tego przykładu zostanie `PrimeNumberCalculator` użyty składnik opisany [w temacie How to: Implementacja składnika obsługującego wzorzec](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="9bc2e-105">Gdy uruchamiasz projekt, który używa tego przykładu, zobaczysz formularz "Kalkulator numeru głównego" z siatką i dwoma przyciskami: **Rozpocznij nowe zadanie** i **Anuluj operację**.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="9bc2e-106">Możesz kliknąć przycisk **Rozpocznij nowe zadanie** kilka razy, a dla każdego kliknięcia, operacja asynchroniczna rozpocznie obliczenia, aby określić, czy losowo wygenerowany numer testu jest podstawowy.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="9bc2e-107">Formularz będzie okresowo wyświetlał postęp i wyniki przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="9bc2e-108">Każda operacja ma przypisany unikatowy identyfikator zadania.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="9bc2e-109">Wynik obliczeń jest wyświetlany w kolumnie **wynik** ; Jeśli numer testu nie jest znakiem, jest oznaczony jako kompozytowy i zostanie wyświetlony pierwszy dzielnik.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="9bc2e-110">Wszystkie oczekujące operacje można anulować przy użyciu przycisku **Anuluj** .</span><span class="sxs-lookup"><span data-stu-id="9bc2e-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="9bc2e-111">Można wprowadzić wiele zaznaczeń.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9bc2e-112">Większość cyfr nie będzie podstawowa.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-112">Most numbers will not be prime.</span></span> <span data-ttu-id="9bc2e-113">Jeśli nie odnaleziono numeru początkowego po kilku ukończonych operacjach, wystarczy uruchomić więcej zadań i ostatecznie znaleźć liczby podstawowe.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc2e-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bc2e-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="9bc2e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bc2e-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
