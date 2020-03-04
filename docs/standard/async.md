---
title: Przegląd Async
description: Dowiedz się, w jaki sposób programowanie asynchroniczne jest prostą techniką, która ułatwia obsługę blokowania operacji we/wy i współbieżnych na wielu rdzeniach.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159731"
---
# <a name="async-overview"></a><span data-ttu-id="f4d3c-103">Przegląd Async</span><span class="sxs-lookup"><span data-stu-id="f4d3c-103">Async Overview</span></span>

<span data-ttu-id="f4d3c-104">Tak długo aplikacje były szybsze po prostu przez zakup nowszego komputera lub serwera, a następnie ten trend został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="f4d3c-105">W rzeczywistości została odwrócona.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-105">In fact, it reversed.</span></span> <span data-ttu-id="f4d3c-106">Pojawiły się telefony komórkowe z 1ghzą pojedyncze podstawowe wióry ARM i obciążenia serwera przenoszone do maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="f4d3c-107">Użytkownicy nadal chcą, aby właściciele interfejsu użytkownika i biznesowe chcą, aby serwery były skalowane wraz z ich działalnością biznesową.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="f4d3c-108">Przejście do urządzeń przenośnych i chmurowych oraz połączona z Internetem populacja > 3B użytkowników spowodowało powstanie nowego zestawu wzorców oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span>

- <span data-ttu-id="f4d3c-109">Aplikacje klienckie powinny być zawsze włączone, zawsze połączone i stale reagować na interakcję z użytkownikiem (na przykład Touch) ze wszystkimi klasyfikacjami w sklepie App Store.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="f4d3c-110">Usługi powinny obsłużyć wzrost ruchu przez bezpieczne skalowanie w górę i w dół.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span>

<span data-ttu-id="f4d3c-111">Programowanie asynchroniczne to kluczowa technika, która ułatwia obsługę blokowania operacji we/wy i współbieżnych na wielu rdzeniach.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="f4d3c-112">Platforma .NET oferuje możliwość, aby aplikacje i usługi były w stanie reagować i elastycznie korzystać z łatwych w użyciu modeli programów asynchronicznych na C#poziomie języka w programie F#, Visual Basic i.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="f4d3c-113">Dlaczego warto pisać kod asynchroniczny?</span><span class="sxs-lookup"><span data-stu-id="f4d3c-113">Why Write Async Code?</span></span>

<span data-ttu-id="f4d3c-114">Nowoczesne aplikacje wykorzystują wiele operacji we/wy plików i sieci.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="f4d3c-115">Interfejsy API we/wy tradycyjnie domyślnie blokują, co powoduje słabą obsługę użytkowników i wykorzystanie sprzętu, chyba że chcesz poznać i korzystać z niewielkich wzorców.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="f4d3c-116">Asynchroniczne interfejsy API oparte na zadaniach i asynchroniczny model programowania na poziomie języka odwracają ten model, dzięki czemu asynchroniczne wykonywanie jest domyślnie z kilkoma nowymi koncepcjami, które należy poznać.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="f4d3c-117">Kod asynchroniczny ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="f4d3c-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="f4d3c-118">Obsługuje więcej żądań serwera, uzyskując wątki do obsługi większej liczby żądań podczas oczekiwania na zwrócenie żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="f4d3c-119">Umożliwia interfejsów użytkownika więcej odpowiedzi przez uzyskanie wątków do interakcji z interfejsem użytkownika podczas oczekiwania na żądania we/wy i przez przeniesienie długotrwałej pracy na inne rdzenie procesora.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="f4d3c-120">Wiele nowszych interfejsów API platformy .NET jest asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="f4d3c-121">W programie .NET można łatwo pisać kod asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="f4d3c-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="f4d3c-122">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="f4d3c-122">What's next?</span></span>

<span data-ttu-id="f4d3c-123">Więcej informacji znajduje się w temacie [Async in głębokości](async-in-depth.md) .</span><span class="sxs-lookup"><span data-stu-id="f4d3c-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="f4d3c-124">Temat [wzorce programowania asynchronicznego](asynchronous-programming-patterns/index.md) zawiera przegląd trzech asynchronicznych wzorców programowania obsługiwanych w programie .NET:</span><span class="sxs-lookup"><span data-stu-id="f4d3c-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="f4d3c-125">[Model programowania asynchronicznego (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsza wersja)</span><span class="sxs-lookup"><span data-stu-id="f4d3c-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="f4d3c-126">[Wzorzec asynchroniczny oparty na zdarzeniach (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starsza wersja)</span><span class="sxs-lookup"><span data-stu-id="f4d3c-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="f4d3c-127">[Wzorzec asynchroniczny oparty na zadaniach (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (zalecany dla nowego programowania)</span><span class="sxs-lookup"><span data-stu-id="f4d3c-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="f4d3c-128">Aby uzyskać więcej informacji na temat zalecanego modelu programowania opartego na zadaniach, zapoznaj się z tematem [programowanie asynchroniczne oparte na zadaniach](parallel-programming/task-based-asynchronous-programming.md) .</span><span class="sxs-lookup"><span data-stu-id="f4d3c-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
