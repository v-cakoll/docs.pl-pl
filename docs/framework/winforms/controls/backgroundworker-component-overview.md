---
title: BackgroundWorker — Informacje o składniku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046109"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="0b43c-102">BackgroundWorker — Informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="0b43c-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="0b43c-103">Istnieje wiele często wykonywanych operacji, których wykonanie może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="0b43c-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="0b43c-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0b43c-104">For example:</span></span>  
  
- <span data-ttu-id="0b43c-105">Pobieranie obrazów</span><span class="sxs-lookup"><span data-stu-id="0b43c-105">Image downloads</span></span>  
  
- <span data-ttu-id="0b43c-106">Wywołania usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="0b43c-106">Web service invocations</span></span>  
  
- <span data-ttu-id="0b43c-107">Pobieranie i przekazywanie plików (w tym aplikacji równorzędnych)</span><span class="sxs-lookup"><span data-stu-id="0b43c-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="0b43c-108">Złożone obliczenia lokalne</span><span class="sxs-lookup"><span data-stu-id="0b43c-108">Complex local computations</span></span>  
  
- <span data-ttu-id="0b43c-109">Transakcje bazy danych</span><span class="sxs-lookup"><span data-stu-id="0b43c-109">Database transactions</span></span>  
  
- <span data-ttu-id="0b43c-110">Dostęp do dysku lokalnego z uwzględnieniem wolnej szybkości względem dostępu do pamięci</span><span class="sxs-lookup"><span data-stu-id="0b43c-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="0b43c-111">Operacje takie jak te mogą spowodować, że interfejs użytkownika będzie zablokowany, gdy są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="0b43c-111">Operations like these can cause your user interface to block while they are running.</span></span> <span data-ttu-id="0b43c-112">Jeśli potrzebujesz interfejsu użytkownika, który ma duże opóźnienia związane z takimi operacjami, <xref:System.ComponentModel.BackgroundWorker> składnik oferuje wygodne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="0b43c-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="0b43c-113"><xref:System.ComponentModel.BackgroundWorker> Składnik daje możliwość asynchronicznego wykonywania czasochłonnych operacji ("w tle") na wątku innym niż główny wątek interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b43c-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="0b43c-114">Aby korzystać z <xref:System.ComponentModel.BackgroundWorker>programu, wystarczy wskazać, jakie czasochłonne metody procesu roboczego w tle, a następnie <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="0b43c-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="0b43c-115">Wątek wywołujący nadal działa normalnie, gdy metoda proces roboczy jest uruchamiana asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="0b43c-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="0b43c-116">Gdy metoda zostanie zakończona, <xref:System.ComponentModel.BackgroundWorker> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> wyzwala wywołujący wątek przez wygenerowanie zdarzenia, które opcjonalnie zawiera wyniki operacji.</span><span class="sxs-lookup"><span data-stu-id="0b43c-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="0b43c-117">Składnik jest dostępny z przybornika na karcie **składniki** . <xref:System.ComponentModel.BackgroundWorker> Aby dodać <xref:System.ComponentModel.BackgroundWorker> do formularza, <xref:System.ComponentModel.BackgroundWorker> przeciągnij składnik na formularz.</span><span class="sxs-lookup"><span data-stu-id="0b43c-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="0b43c-118">Pojawia się on na pasku składnika, a jego właściwości są wyświetlane w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="0b43c-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="0b43c-119">Aby rozpocząć operację asynchroniczną, użyj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0b43c-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="0b43c-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>przyjmuje opcjonalny `object` parametr, który może służyć do przekazywania argumentów do metody Worker.</span><span class="sxs-lookup"><span data-stu-id="0b43c-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="0b43c-121">Klasa ujawnia zdarzenie, do którego <xref:System.ComponentModel.BackgroundWorker.DoWork> wątek roboczy jest dołączany przez procedurę obsługi zdarzeń. <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="0b43c-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="0b43c-122">Program obsługi <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń <xref:System.ComponentModel.DoWorkEventArgs> przyjmuje<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> parametr, który ma właściwość.</span><span class="sxs-lookup"><span data-stu-id="0b43c-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="0b43c-123">Ta właściwość odbiera parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i może zostać przesłany do metody procesu roboczego, która zostanie wywołana <xref:System.ComponentModel.BackgroundWorker.DoWork> w programie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0b43c-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="0b43c-124">Poniższy przykład pokazuje, jak przypisać wynik z metody procesu roboczego o nazwie `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="0b43c-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="0b43c-125">Jest to część większego przykładu, którą można znaleźć w [następujących tematach: Implementowanie formularza korzystającego z operacji](how-to-implement-a-form-that-uses-a-background-operation.md)w tle.</span><span class="sxs-lookup"><span data-stu-id="0b43c-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="0b43c-126">Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b43c-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0b43c-127">W przypadku korzystania z wielowątkowości dowolnego sortowania użytkownik może ujawnić sobie bardzo poważne i złożone usterki.</span><span class="sxs-lookup"><span data-stu-id="0b43c-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="0b43c-128">Przed zaimplementowaniem dowolnego rozwiązania, które używa wielowątkowości, należy zapoznać się z [zarządzanymi wątkami](../../../standard/threading/managed-threading-best-practices.md) .</span><span class="sxs-lookup"><span data-stu-id="0b43c-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="0b43c-129">Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker> używania klasy, [zobacz How to: Uruchom operację w tle](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="0b43c-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b43c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b43c-130">See also</span></span>

- [<span data-ttu-id="0b43c-131">Zarządzane wątki</span><span class="sxs-lookup"><span data-stu-id="0b43c-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="0b43c-132">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="0b43c-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="0b43c-133">Instrukcje: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="0b43c-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
