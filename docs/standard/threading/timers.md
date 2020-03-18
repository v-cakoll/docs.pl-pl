---
title: Czasomierze
description: Dowiedz się, co czasomierzy .NET do użycia w środowisku wielowątkowym.
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
ms.openlocfilehash: d7d1fa13b02fe7425fa9b4cb81ba20297a23fe4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128952"
---
# <a name="timers"></a><span data-ttu-id="905a5-103">Czasomierze</span><span class="sxs-lookup"><span data-stu-id="905a5-103">Timers</span></span>

<span data-ttu-id="905a5-104">.NET udostępnia dwa timery do użycia w środowisku wielowątkowym:</span><span class="sxs-lookup"><span data-stu-id="905a5-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="905a5-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, który wykonuje jedną metodę wywołania odwróconego w wątku <xref:System.Threading.ThreadPool> w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="905a5-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="905a5-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, który domyślnie wywołuje <xref:System.Threading.ThreadPool> zdarzenie w wątku w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="905a5-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="905a5-107">Niektóre implementacje .NET mogą zawierać dodatkowe czasomierzy:</span><span class="sxs-lookup"><span data-stu-id="905a5-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="905a5-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: składnik Formularzy systemu Windows, który uruchamia zdarzenie w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="905a5-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="905a5-109">Składnik nie ma interfejsu użytkownika i jest przeznaczony do użytku w środowisku jednowątkowym.</span><span class="sxs-lookup"><span data-stu-id="905a5-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="905a5-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: składnik ASP.NET, który regularnie wykonuje asynchroniczne lub synchroniczne ogłaszania stron internetowych.</span><span class="sxs-lookup"><span data-stu-id="905a5-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="905a5-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: czasoatarka zintegrowana <xref:System.Windows.Threading.Dispatcher> z kolejką, która jest przetwarzana w określonym przedziale czasu i przy określonym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="905a5-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="905a5-112">Klasa System.Threading.Timer</span><span class="sxs-lookup"><span data-stu-id="905a5-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="905a5-113">Klasa <xref:System.Threading.Timer?displayProperty=nameWithType> umożliwia ciągłe wywoływanie delegata w określonych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="905a5-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="905a5-114">Ta klasa służy również do planowania pojedynczego wywołania pełnomocnika w określonym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="905a5-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="905a5-115">Delegat jest wykonywany <xref:System.Threading.ThreadPool> w wątku.</span><span class="sxs-lookup"><span data-stu-id="905a5-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="905a5-116">Podczas tworzenia <xref:System.Threading.Timer?displayProperty=nameWithType> obiektu należy określić <xref:System.Threading.TimerCallback> pełnomocnika, który definiuje metodę wywołania wywołania, opcjonalny obiekt stanu, który jest przekazywany do wywołania wywołania, czas opóźnienia przed pierwszym wywołaniem wywołania wywołania wywołania wywołania i przedział czasu między wywołaniami wywołania.</span><span class="sxs-lookup"><span data-stu-id="905a5-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="905a5-117">Aby anulować czasoator <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> oczekujący, wywołaj metodę.</span><span class="sxs-lookup"><span data-stu-id="905a5-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="905a5-118">Poniższy przykład tworzy czasodwac, który wywołuje podanych delegata po raz pierwszy po jednej sekundzie (1000 milisekund), a następnie wywołuje go co dwie sekundy.</span><span class="sxs-lookup"><span data-stu-id="905a5-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="905a5-119">Obiekt stanu w przykładzie służy do zliczania, ile razy pełnomocnik jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="905a5-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="905a5-120">Czasowat jest zatrzymywany, gdy pełnomocnik został wywołany co najmniej 10 razy.</span><span class="sxs-lookup"><span data-stu-id="905a5-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="905a5-121">Aby uzyskać więcej informacji <xref:System.Threading.Timer?displayProperty=nameWithType>i przykładów, zobacz .</span><span class="sxs-lookup"><span data-stu-id="905a5-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="905a5-122">Klasa System.Timers.Timer</span><span class="sxs-lookup"><span data-stu-id="905a5-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="905a5-123">Innym czasoatorem, który może być <xref:System.Timers.Timer?displayProperty=nameWithType> używany w środowisku wielowątkowym jest to, że domyślnie wywołuje zdarzenie w wątku. <xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="905a5-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="905a5-124">Podczas tworzenia <xref:System.Timers.Timer?displayProperty=nameWithType> obiektu można określić przedział czasu, w <xref:System.Timers.Timer.Elapsed> którym ma zostać wywołane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="905a5-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="905a5-125">Użyj <xref:System.Timers.Timer.Enabled%2A> właściwości, aby wskazać, czy <xref:System.Timers.Timer.Elapsed> czasowcy powinny wywołać zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="905a5-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="905a5-126">Jeśli konieczne <xref:System.Timers.Timer.Elapsed> jest, aby zdarzenie zostało podniesione tylko raz po upływie <xref:System.Timers.Timer.AutoReset%2A> `false`określonego interwału, ustaw wartość .</span><span class="sxs-lookup"><span data-stu-id="905a5-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="905a5-127">Domyślną wartością <xref:System.Timers.Timer.AutoReset%2A> właściwości `true`jest , <xref:System.Timers.Timer.Elapsed> co oznacza, że zdarzenie jest wywoływane regularnie w interwale zdefiniowanym <xref:System.Timers.Timer.Interval%2A> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="905a5-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="905a5-128">Aby uzyskać więcej informacji <xref:System.Timers.Timer?displayProperty=nameWithType>i przykładów, zobacz .</span><span class="sxs-lookup"><span data-stu-id="905a5-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="905a5-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="905a5-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="905a5-130">Wątkowe obiekty i operacje</span><span class="sxs-lookup"><span data-stu-id="905a5-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
