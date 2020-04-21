---
title: Czasomierze
description: Dowiedz się, co .NET czasomierze do użycia w środowisku wielowątkowym.
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
ms.openlocfilehash: d463eb2a8d598dc5ba9b2fb51a6fc08c563e6fe4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739488"
---
# <a name="timers"></a><span data-ttu-id="11f6f-103">Czasomierze</span><span class="sxs-lookup"><span data-stu-id="11f6f-103">Timers</span></span>

<span data-ttu-id="11f6f-104">.NET udostępnia dwa czasomierze do użycia w środowisku wielowątkowym:</span><span class="sxs-lookup"><span data-stu-id="11f6f-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="11f6f-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, który wykonuje metodę pojedynczego <xref:System.Threading.ThreadPool> wywołania zwrotnego w wątku w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="11f6f-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="11f6f-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, który domyślnie wywołuje zdarzenie <xref:System.Threading.ThreadPool> w wątku w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="11f6f-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="11f6f-107">Niektóre implementacje platformy .NET mogą zawierać dodatkowe czasomierze:</span><span class="sxs-lookup"><span data-stu-id="11f6f-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="11f6f-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: składnik Windows Forms, który uruchamia zdarzenie w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="11f6f-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="11f6f-109">Składnik nie ma interfejsu użytkownika i jest przeznaczony do użytku w środowisku jednowątkowym.</span><span class="sxs-lookup"><span data-stu-id="11f6f-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="11f6f-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: składnik ASP.NET, który wykonuje asynchroniczne lub synchroniczne postbacks strony sieci Web w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="11f6f-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="11f6f-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: czasomierz, który <xref:System.Windows.Threading.Dispatcher> jest zintegrowany z kolejką, która jest przetwarzana w określonym przedziale czasu i w określonym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="11f6f-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="11f6f-112">Klasa System.Threading.Timer</span><span class="sxs-lookup"><span data-stu-id="11f6f-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="11f6f-113">Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> umożliwia ciągłe wywoływanie delegata w określonych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="11f6f-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="11f6f-114">Tej klasy można również użyć do zaplanowania pojedynczego wywołania do pełnomocnika w określonym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="11f6f-114">You can also use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="11f6f-115">Pełnomocnik jest wykonywany <xref:System.Threading.ThreadPool> w wątku.</span><span class="sxs-lookup"><span data-stu-id="11f6f-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="11f6f-116">Podczas tworzenia <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu, należy <xref:System.Threading.TimerCallback> określić pełnomocnika, który definiuje metodę wywołania zwrotnego, opcjonalny obiekt stanu, który jest przekazywany do wywołania zwrotnego, czas opóźnienia przed pierwszym wywołaniem wywołania zwrotnego i przedział czasu między wywołaniami zwrotnymi.</span><span class="sxs-lookup"><span data-stu-id="11f6f-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="11f6f-117">Aby anulować oczekujący czasomierz, należy wywołać <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="11f6f-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="11f6f-118">Poniższy przykład tworzy czasomierz, który wywołuje podane delegata po raz pierwszy po jednej sekundzie (1000 milisekund), a następnie wywołuje go co dwie sekundy.</span><span class="sxs-lookup"><span data-stu-id="11f6f-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="11f6f-119">Obiekt stanu w przykładzie jest używany do zliczania, ile razy delegat jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="11f6f-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="11f6f-120">Czasomierz jest zatrzymany, gdy pełnomocnik został wywołany co najmniej 10 razy.</span><span class="sxs-lookup"><span data-stu-id="11f6f-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="11f6f-121">Aby uzyskać więcej informacji <xref:System.Threading.Timer?displayProperty=nameWithType>i przykładów, zobacz .</span><span class="sxs-lookup"><span data-stu-id="11f6f-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="11f6f-122">Klasa System.Timers.Timer</span><span class="sxs-lookup"><span data-stu-id="11f6f-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="11f6f-123">Innym czasomierzem, który może być używany <xref:System.Timers.Timer?displayProperty=nameWithType> w środowisku wielowątkowym jest to, że domyślnie wywołuje zdarzenie w wątku. <xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="11f6f-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="11f6f-124">Podczas tworzenia <xref:System.Timers.Timer?displayProperty=nameWithType> obiektu można określić przedział czasu, w <xref:System.Timers.Timer.Elapsed> którym ma zostać utworzone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="11f6f-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="11f6f-125">Użyj <xref:System.Timers.Timer.Enabled%2A> właściwości, aby wskazać, czy <xref:System.Timers.Timer.Elapsed> czasomierz powinien podnieść zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="11f6f-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="11f6f-126">Jeśli chcesz, <xref:System.Timers.Timer.Elapsed> aby zdarzenie zostało podniesione tylko raz po upływie <xref:System.Timers.Timer.AutoReset%2A> określonego `false`interwału, ustaw na .</span><span class="sxs-lookup"><span data-stu-id="11f6f-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="11f6f-127">Domyślną wartością <xref:System.Timers.Timer.AutoReset%2A> właściwości `true`jest , <xref:System.Timers.Timer.Elapsed> co oznacza, że zdarzenie jest <xref:System.Timers.Timer.Interval%2A> wywoływane regularnie w przedziale zdefiniowanym przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="11f6f-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="11f6f-128">Aby uzyskać więcej informacji <xref:System.Timers.Timer?displayProperty=nameWithType>i przykładów, zobacz .</span><span class="sxs-lookup"><span data-stu-id="11f6f-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="11f6f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11f6f-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="11f6f-130">Wątki obiektów i operacji</span><span class="sxs-lookup"><span data-stu-id="11f6f-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
