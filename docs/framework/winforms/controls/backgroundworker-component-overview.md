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
ms.openlocfilehash: 1f7da963db34434ee2631e9e2c0367abbd628656
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749171"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="54cdb-102">BackgroundWorker — Informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="54cdb-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="54cdb-103">Istnieje wiele często wykonywanych operacji, które może zająć dużo czasu wykonania.</span><span class="sxs-lookup"><span data-stu-id="54cdb-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="54cdb-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="54cdb-104">For example:</span></span>  
  
-   <span data-ttu-id="54cdb-105">Pobiera obraz</span><span class="sxs-lookup"><span data-stu-id="54cdb-105">Image downloads</span></span>  
  
-   <span data-ttu-id="54cdb-106">Wywołania usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="54cdb-106">Web service invocations</span></span>  
  
-   <span data-ttu-id="54cdb-107">Plik przekazuje i pobiera (w tym aplikacji peer-to-peer)</span><span class="sxs-lookup"><span data-stu-id="54cdb-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
-   <span data-ttu-id="54cdb-108">Złożone obliczenia lokalne</span><span class="sxs-lookup"><span data-stu-id="54cdb-108">Complex local computations</span></span>  
  
-   <span data-ttu-id="54cdb-109">Transakcje bazy danych</span><span class="sxs-lookup"><span data-stu-id="54cdb-109">Database transactions</span></span>  
  
-   <span data-ttu-id="54cdb-110">Dysk lokalny dostęp, biorąc pod uwagę jej szybkość powolnego względem dostępu do pamięci</span><span class="sxs-lookup"><span data-stu-id="54cdb-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="54cdb-111">Operacje, takie jak te może spowodować zawieszenie, gdy są one uruchomione interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="54cdb-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="54cdb-112">Gdy chcesz dynamicznym interfejsem użytkownika i napotykają duże opóźnienia skojarzonych z takich operacji <xref:System.ComponentModel.BackgroundWorker> składnik udostępnia wygodne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="54cdb-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="54cdb-113"><xref:System.ComponentModel.BackgroundWorker> Składnika daje możliwość wykonywania czasochłonne operacje asynchronicznie ("w tle") w wątku, który różni się od głównego wątku interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54cdb-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="54cdb-114">Aby użyć <xref:System.ComponentModel.BackgroundWorker>, wystarczy podać jej metody czasochłonnych procesów roboczych do wykonania w tle, a następnie możesz wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="54cdb-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="54cdb-115">Wątek wywołujący w dalszym ciągu działać normalnie, podczas gdy metodzie wątku roboczego jest uruchamiane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="54cdb-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="54cdb-116">Po zakończeniu działania metody <xref:System.ComponentModel.BackgroundWorker> alerty wątku wywołującego uruchomieniu którego <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenie, które opcjonalnie zawiera wyniki operacji.</span><span class="sxs-lookup"><span data-stu-id="54cdb-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="54cdb-117"><xref:System.ComponentModel.BackgroundWorker> Składnik jest dostępny z **przybornika**w **składniki** kartę. Aby dodać <xref:System.ComponentModel.BackgroundWorker> do formularza, przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="54cdb-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="54cdb-118">Wygląda na to, w zasobniku składnika, a jego właściwości są wyświetlane w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="54cdb-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="54cdb-119">Aby rozpocząć operację asynchroniczną, użyj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="54cdb-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="54cdb-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> przyjmuje opcjonalny `object` parametr, który może służyć do przekazywania argumentów do metody procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="54cdb-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="54cdb-121"><xref:System.ComponentModel.BackgroundWorker> Klasy ujawnia <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń, do której dołączono wątek procesu roboczego za pomocą <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="54cdb-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="54cdb-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> Programu obsługi zdarzeń przyjmuje <xref:System.ComponentModel.DoWorkEventArgs> parametr, który ma <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="54cdb-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="54cdb-123">Ta właściwość odbiera parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i może być przekazywany do metody proces roboczy zostanie wywołana w <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="54cdb-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="54cdb-124">Poniższy przykład pokazuje, jak przypisać wyniku z metody procesu roboczego o nazwie `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="54cdb-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="54cdb-125">Jest on częścią większego przykładu można znaleźć w [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="54cdb-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="54cdb-126">Aby uzyskać więcej informacji na temat korzystania z programów obsługi zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="54cdb-126">For more information on using event handlers, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="54cdb-127">Korzystając z wielowątkowością jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek.</span><span class="sxs-lookup"><span data-stu-id="54cdb-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="54cdb-128">Zapoznaj się z [zarządzana wątkowość najlepsze](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="54cdb-128">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="54cdb-129">Aby uzyskać więcej informacji na temat korzystania z <xref:System.ComponentModel.BackgroundWorker> klasy, zobacz [porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="54cdb-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54cdb-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54cdb-130">See Also</span></span>  
 [<span data-ttu-id="54cdb-131">NIE w kompilacji: Wielowątkowość w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54cdb-131">NOT IN BUILD: Multithreading in Visual Basic</span></span>](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="54cdb-132">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="54cdb-132">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
