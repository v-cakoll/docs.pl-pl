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
ms.openlocfilehash: da1d87464ef30fb549a2c201170e81c45cbdf6fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587737"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="f9c1a-102">BackgroundWorker — Informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="f9c1a-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="f9c1a-103">Istnieje wiele często wykonywanych operacji, które może zająć dużo czasu wykonania.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="f9c1a-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f9c1a-104">For example:</span></span>  
  
- <span data-ttu-id="f9c1a-105">Pobiera obraz</span><span class="sxs-lookup"><span data-stu-id="f9c1a-105">Image downloads</span></span>  
  
- <span data-ttu-id="f9c1a-106">Wywołania usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="f9c1a-106">Web service invocations</span></span>  
  
- <span data-ttu-id="f9c1a-107">Plik przekazuje i pobiera (w tym aplikacji peer-to-peer)</span><span class="sxs-lookup"><span data-stu-id="f9c1a-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="f9c1a-108">Złożone obliczenia lokalne</span><span class="sxs-lookup"><span data-stu-id="f9c1a-108">Complex local computations</span></span>  
  
- <span data-ttu-id="f9c1a-109">Transakcje bazy danych</span><span class="sxs-lookup"><span data-stu-id="f9c1a-109">Database transactions</span></span>  
  
- <span data-ttu-id="f9c1a-110">Dysk lokalny dostęp, biorąc pod uwagę jej szybkość powolnego względem dostępu do pamięci</span><span class="sxs-lookup"><span data-stu-id="f9c1a-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="f9c1a-111">Operacje, takie jak te może spowodować zawieszenie, gdy są one uruchomione interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="f9c1a-112">Gdy chcesz dynamicznym interfejsem użytkownika i napotykają duże opóźnienia skojarzonych z takich operacji <xref:System.ComponentModel.BackgroundWorker> składnik udostępnia wygodne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="f9c1a-113"><xref:System.ComponentModel.BackgroundWorker> Składnika daje możliwość wykonywania czasochłonne operacje asynchronicznie ("w tle") w wątku, który różni się od głównego wątku interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="f9c1a-114">Aby użyć <xref:System.ComponentModel.BackgroundWorker>, wystarczy podać jej metody czasochłonnych procesów roboczych do wykonania w tle, a następnie możesz wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="f9c1a-115">Wątek wywołujący w dalszym ciągu działać normalnie, podczas gdy metodzie wątku roboczego jest uruchamiane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="f9c1a-116">Po zakończeniu działania metody <xref:System.ComponentModel.BackgroundWorker> alerty wątku wywołującego uruchomieniu którego <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenie, które opcjonalnie zawiera wyniki operacji.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="f9c1a-117"><xref:System.ComponentModel.BackgroundWorker> Składnik jest dostępny z **przybornika**w **składniki** kartę. Aby dodać <xref:System.ComponentModel.BackgroundWorker> do formularza, przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="f9c1a-118">Wygląda na to, w zasobniku składnika, a jego właściwości są wyświetlane w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="f9c1a-119">Aby rozpocząć operację asynchroniczną, użyj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="f9c1a-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> przyjmuje opcjonalny `object` parametr, który może służyć do przekazywania argumentów do metody procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="f9c1a-121"><xref:System.ComponentModel.BackgroundWorker> Klasy ujawnia <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń, do której dołączono wątek procesu roboczego za pomocą <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="f9c1a-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> Programu obsługi zdarzeń przyjmuje <xref:System.ComponentModel.DoWorkEventArgs> parametr, który ma <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="f9c1a-123">Ta właściwość odbiera parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i może być przekazywany do metody proces roboczy zostanie wywołana w <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="f9c1a-124">Poniższy przykład pokazuje, jak przypisać wyniku z metody procesu roboczego o nazwie `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="f9c1a-125">Jest on częścią większego przykładu można znaleźć w [jak: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="f9c1a-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="f9c1a-126">Aby uzyskać więcej informacji na temat korzystania z programów obsługi zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9c1a-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f9c1a-127">Korzystając z wielowątkowością jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="f9c1a-128">Zapoznaj się z [zarządzana wątkowość najlepsze](../../../standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="f9c1a-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="f9c1a-129">Aby uzyskać więcej informacji na temat korzystania z <xref:System.ComponentModel.BackgroundWorker> klasy, zobacz [jak: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="f9c1a-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c1a-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9c1a-130">See also</span></span>

- [<span data-ttu-id="f9c1a-131">Zarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="f9c1a-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="f9c1a-132">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="f9c1a-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="f9c1a-133">Instrukcje: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="f9c1a-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
