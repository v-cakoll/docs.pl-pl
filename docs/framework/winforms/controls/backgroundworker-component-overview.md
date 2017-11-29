---
title: "BackgroundWorker — Informacje o składniku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: BackgroundWorker
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f192081d9b7e30f10373342aef39443ff49e9931
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="8bf11-102">BackgroundWorker — Informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="8bf11-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="8bf11-103">Istnieje wiele często wykonywanych operacji, które może zająć dużo czasu na wykonanie.</span><span class="sxs-lookup"><span data-stu-id="8bf11-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="8bf11-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8bf11-104">For example:</span></span>  
  
-   <span data-ttu-id="8bf11-105">Pobiera obraz</span><span class="sxs-lookup"><span data-stu-id="8bf11-105">Image downloads</span></span>  
  
-   <span data-ttu-id="8bf11-106">Wywołania usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="8bf11-106">Web service invocations</span></span>  
  
-   <span data-ttu-id="8bf11-107">Plik i pobiera (w tym przypadku peer-to-peer aplikacji)</span><span class="sxs-lookup"><span data-stu-id="8bf11-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
-   <span data-ttu-id="8bf11-108">Złożone obliczenia lokalnego</span><span class="sxs-lookup"><span data-stu-id="8bf11-108">Complex local computations</span></span>  
  
-   <span data-ttu-id="8bf11-109">Transakcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="8bf11-109">Database transactions</span></span>  
  
-   <span data-ttu-id="8bf11-110">Dostęp do dysku lokalnego, podane jego szybkość powolnego względem dostęp do pamięci</span><span class="sxs-lookup"><span data-stu-id="8bf11-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="8bf11-111">Operacje, takie jak te mogą spowodować zawieszenie uruchomieniu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8bf11-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="8bf11-112">Gdy reakcje interfejsu użytkownika i muszą stawiać czoła o długie opóźnienia skojarzone z takich operacji <xref:System.ComponentModel.BackgroundWorker> stanowi wygodną rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8bf11-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="8bf11-113"><xref:System.ComponentModel.BackgroundWorker> Składnika daje możliwość wykonania czas operacji asynchronicznie ("w tle"), na przez wątek inny niż główny wątek interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bf11-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="8bf11-114">Aby użyć <xref:System.ComponentModel.BackgroundWorker>, po prostu go metodę czasochłonny proces roboczy do wykonania w tle, a następnie wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8bf11-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="8bf11-115">Twoje wątek wywołujący w dalszym ciągu działać normalnie podczas asynchronicznie metodę procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="8bf11-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="8bf11-116">Po zakończeniu działania metody <xref:System.ComponentModel.BackgroundWorker> alerty wątek wywołujący uruchamiania <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń, która opcjonalnie zawiera wyniki operacji.</span><span class="sxs-lookup"><span data-stu-id="8bf11-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="8bf11-117"><xref:System.ComponentModel.BackgroundWorker> Składnik jest dostępny z **przybornika**w **składniki** kartę. Aby dodać <xref:System.ComponentModel.BackgroundWorker> do formularza, przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="8bf11-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="8bf11-118">Wygląda na to, na pasku składnika i jego właściwości są wyświetlane w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="8bf11-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="8bf11-119">Aby uruchomić operację asynchroniczną, użyj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8bf11-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="8bf11-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>przyjmuje opcjonalny `object` parametr, który może służyć do argument jest przekazywany do metody pracownika.</span><span class="sxs-lookup"><span data-stu-id="8bf11-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="8bf11-121"><xref:System.ComponentModel.BackgroundWorker> Klasy ujawnia <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń, do której z wątku roboczego jest dołączona do <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bf11-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="8bf11-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> Przyjmuje obsługi zdarzeń <xref:System.ComponentModel.DoWorkEventArgs> parametr, który ma <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8bf11-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="8bf11-123">Ta właściwość odbiera parametru z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i mogą zostać przekazane do metody pracownika, która będzie wywoływana w <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bf11-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="8bf11-124">Poniższy przykład przedstawia sposób Przypisz wynik z metody procesu roboczego o nazwie `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="8bf11-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="8bf11-125">Nie jest częścią większego przykładu można znaleźć w [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="8bf11-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="8bf11-126">Aby uzyskać więcej informacji na temat używania programów obsługi zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="8bf11-126">For more information on using event handlers, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8bf11-127">Korzystając z wielowątkowość jakiegokolwiek, możesz narażając samodzielnie do usterki bardzo poważne i złożone.</span><span class="sxs-lookup"><span data-stu-id="8bf11-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="8bf11-128">Zapoznaj się [zarządzanych wątków najlepsze rozwiązania w zakresie](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem rozwiązania, w którym używane wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="8bf11-128">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="8bf11-129">Aby uzyskać więcej informacji na temat używania <xref:System.ComponentModel.BackgroundWorker> , zobacz [porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="8bf11-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf11-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bf11-130">See Also</span></span>  
 [<span data-ttu-id="8bf11-131">NIE w kompilacji: Wielowątkowość w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8bf11-131">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="8bf11-132">Porady: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="8bf11-132">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
