---
title: Czasomierze
description: Dowiedz się, jakie czasomierzy .NET do użycia w środowisku wielowątkowym.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: ae41c535d8bc1c0a05174b9051ba34f1a0a34638
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875069"
---
# <a name="timers"></a><span data-ttu-id="fd832-103">Czasomierze</span><span class="sxs-lookup"><span data-stu-id="fd832-103">Timers</span></span>

<span data-ttu-id="fd832-104">.NET oferuje dwa typy czasomierzy do użycia w środowisku wielowątkowym:</span><span class="sxs-lookup"><span data-stu-id="fd832-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="fd832-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, który wykonuje metodę pojedynczego wywołania zwrotnego w <xref:System.Threading.ThreadPool> wątku w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="fd832-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="fd832-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, która domyślnie wywołuje zdarzenie, na <xref:System.Threading.ThreadPool> wątku w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="fd832-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="fd832-107">Niektóre implementacje platformy .NET mogą obejmować czasomierzy dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="fd832-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="fd832-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: składnik Windows Forms, który uruchamia zdarzenie w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="fd832-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="fd832-109">Składnik nie ma interfejsu użytkownika i jest przeznaczony do użytku w środowisku apartamentem.</span><span class="sxs-lookup"><span data-stu-id="fd832-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="fd832-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: składnik ASP.NET, który wykonuje ogłaszania zwrotnego asynchronicznego lub synchronicznego strony sieci web w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="fd832-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="fd832-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: czasomierz, który jest zintegrowany z <xref:System.Windows.Threading.Dispatcher> kolejki, która jest przetwarzana z określonym interwałem czasu i z priorytetem.</span><span class="sxs-lookup"><span data-stu-id="fd832-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="fd832-112">Klasa System.Threading.Timer</span><span class="sxs-lookup"><span data-stu-id="fd832-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="fd832-113"><xref:System.Threading.Timer?displayProperty=nameWithType> Klasy umożliwia ciągłe wywołanie delegata w określonych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="fd832-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="fd832-114">Możesz również użyć tej klasy można zaplanować wywołanie delegata w określonym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="fd832-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="fd832-115">Delegat jest wykonywane na <xref:System.Threading.ThreadPool> wątku.</span><span class="sxs-lookup"><span data-stu-id="fd832-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="fd832-116">Po utworzeniu <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu, należy określić <xref:System.Threading.TimerCallback> delegata, który definiuje metody wywołania zwrotnego, obiekt opcjonalne stanu, który jest przekazywany do wywołania zwrotnego, ilość czasu, opóźnienie przed pierwszym wywołaniem wywołania zwrotnego i przedział czasu między wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="fd832-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="fd832-117">Aby anulować oczekujące czasomierza, należy wywołać <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fd832-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="fd832-118">Poniższy przykład tworzy czasomierz, który wywołuje delegata podane po raz pierwszy po sekundzie (1000 milisekund), a następnie wywołuje on co 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="fd832-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="fd832-119">Obiekt stanu, w przykładzie jest używany policzyć ile razy nosi nazwę delegata.</span><span class="sxs-lookup"><span data-stu-id="fd832-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="fd832-120">Czasomierz został zatrzymany, gdy delegat została wywołana co najmniej 10 razy.</span><span class="sxs-lookup"><span data-stu-id="fd832-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="fd832-121">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd832-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="fd832-122">Klasa System.Timers.Timer</span><span class="sxs-lookup"><span data-stu-id="fd832-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="fd832-123">Jest inny czasomierz, które mogą być używane w środowisku wielowątkowym <xref:System.Timers.Timer?displayProperty=nameWithType> która domyślnie wywołuje zdarzenie, na <xref:System.Threading.ThreadPool> wątku.</span><span class="sxs-lookup"><span data-stu-id="fd832-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="fd832-124">Po utworzeniu <xref:System.Timers.Timer?displayProperty=nameWithType> obiektu, można określić interwał czasu, w którego zostanie wywołane <xref:System.Timers.Timer.Elapsed> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd832-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="fd832-125">Użyj <xref:System.Timers.Timer.Enabled%2A> właściwości, aby wskazać, jeśli czasomierz, powinny wywoływać <xref:System.Timers.Timer.Elapsed> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd832-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="fd832-126">Jeśli potrzebujesz <xref:System.Timers.Timer.Elapsed> zdarzenia tylko jeden raz po upływie określonego interwału, ustaw <xref:System.Timers.Timer.AutoReset%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="fd832-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="fd832-127">Wartość domyślna <xref:System.Timers.Timer.AutoReset%2A> właściwość `true`, co oznacza, że <xref:System.Timers.Timer.Elapsed> zdarzenie jest zgłaszane w regularnie w odstępach czasu zdefiniowanych przez <xref:System.Timers.Timer.Interval%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd832-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="fd832-128">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd832-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fd832-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd832-129">See also</span></span>

 <xref:System.Threading.Timer?displayProperty=nameWithType>  
 <xref:System.Timers.Timer?displayProperty=nameWithType>  
 [<span data-ttu-id="fd832-130">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="fd832-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
