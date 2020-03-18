---
title: Przegląd asynchronicznego
description: Dowiedz się, jak programowanie asynchroniczne jest kluczową techniką, która ułatwia obsługę blokowania we/wy i równoczesnych operacji na wielu rdzeniach.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159731"
---
# <a name="async-overview"></a><span data-ttu-id="95d99-103">Przegląd asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="95d99-103">Async Overview</span></span>

<span data-ttu-id="95d99-104">Nie tak dawno temu aplikacje stały się szybsze po prostu kupując nowszy komputer lub serwer, a następnie ten trend się zatrzymał.</span><span class="sxs-lookup"><span data-stu-id="95d99-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="95d99-105">W rzeczywistości, to odwrócił.</span><span class="sxs-lookup"><span data-stu-id="95d99-105">In fact, it reversed.</span></span> <span data-ttu-id="95d99-106">Telefony komórkowe pojawiły się z 1ghz jednordzeniowych chipów ARM i obciążeń serwera przeniesione na maszyny wirtualne.</span><span class="sxs-lookup"><span data-stu-id="95d99-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="95d99-107">Użytkownicy nadal chcą elastycznego interfejsu użytkownika, a właściciele firm chcą serwerów skalowanych wraz z ich działalnością.</span><span class="sxs-lookup"><span data-stu-id="95d99-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="95d99-108">Przejście na urządzenia mobilne i chmurę oraz populację >użytkowników 3B przyłączoną do Internetu zaowocowało nowym zestawem wzorców oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="95d99-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span>

- <span data-ttu-id="95d99-109">Oczekuje się, że aplikacje klienckie będą zawsze włączone, zawsze połączone i stale reagują na interakcję z użytkownikiem (na przykład dotyk) z wysokimi ocenami w sklepach z aplikacjami!</span><span class="sxs-lookup"><span data-stu-id="95d99-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="95d99-110">Oczekuje się, że usługi obsługi skoków ruchu przez bezpiecznie skalowanie w górę iw dół.</span><span class="sxs-lookup"><span data-stu-id="95d99-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span>

<span data-ttu-id="95d99-111">Programowanie asynchroniczne jest kluczową techniką, która ułatwia obsługę blokowania we/wy i równoczesnych operacji na wielu rdzeniach.</span><span class="sxs-lookup"><span data-stu-id="95d99-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="95d99-112">.NET zapewnia aplikacjom i usługom możliwość responsywnego i elastycznego korzystania z łatwych w użyciu modeli programowania asynchronicznego na poziomie języka w językach C#, Visual Basic i F#.</span><span class="sxs-lookup"><span data-stu-id="95d99-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="95d99-113">Dlaczego warto napisać kod Async?</span><span class="sxs-lookup"><span data-stu-id="95d99-113">Why Write Async Code?</span></span>

<span data-ttu-id="95d99-114">Nowoczesne aplikacje szeroko wykorzystują we/wy plików i sieci.</span><span class="sxs-lookup"><span data-stu-id="95d99-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="95d99-115">Interfejsy API we/wy tradycyjnie blokują domyślnie, co powoduje słabe doświadczenia użytkowników i wykorzystanie sprzętu, chyba że chcesz uczyć się i używać trudnych wzorców.</span><span class="sxs-lookup"><span data-stu-id="95d99-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="95d99-116">Asynchroniczne interfejsy API oparte na zadaniach i model programowania asynchronicznego na poziomie języka odwracają ten model, sprawiając, że wykonanie asynchroniczne jest domyślne przy kilku nowych pojęciach do nauczenia się.</span><span class="sxs-lookup"><span data-stu-id="95d99-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="95d99-117">Kod asynchronicznego ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="95d99-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="95d99-118">Obsługuje więcej żądań serwera, yielding wątków do obsługi większej liczby żądań podczas oczekiwania na żądania we/wy do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="95d99-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="95d99-119">Umożliwia interfejsowi użytkownika, aby być bardziej elastyczne przez plonowanie wątków do interakcji interfejsu użytkownika podczas oczekiwania na żądania we/wy i przez przejście długotrwałej pracy do innych rdzeni procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="95d99-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="95d99-120">Wiele nowszych interfejsów API .NET jest asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="95d99-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="95d99-121">Łatwo jest napisać kod asynchronicznego w .NET!</span><span class="sxs-lookup"><span data-stu-id="95d99-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="95d99-122">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="95d99-122">What's next?</span></span>

<span data-ttu-id="95d99-123">Aby uzyskać więcej informacji, zobacz temat [Async w głębi.](async-in-depth.md)</span><span class="sxs-lookup"><span data-stu-id="95d99-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="95d99-124">Temat [Wzorce programowania asynchronicznego](asynchronous-programming-patterns/index.md) zawiera omówienie trzech wzorców programowania asynchronicznego obsługiwanych w programie .NET:</span><span class="sxs-lookup"><span data-stu-id="95d99-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="95d99-125">[Asynchroniczny model programowania (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsze)</span><span class="sxs-lookup"><span data-stu-id="95d99-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="95d99-126">[Wzorzec asynchroniczny oparty na zdarzeniach (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starszy)</span><span class="sxs-lookup"><span data-stu-id="95d99-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="95d99-127">[Wzorzec asynchroniczny (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) oparty na zadaniach (zalecany do nowego rozwoju)</span><span class="sxs-lookup"><span data-stu-id="95d99-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="95d99-128">Aby uzyskać więcej informacji na temat zalecanego modelu programowania opartego na zadaniach, zobacz temat [programowania asynchronicznego opartego na zadaniach.](parallel-programming/task-based-asynchronous-programming.md)</span><span class="sxs-lookup"><span data-stu-id="95d99-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
