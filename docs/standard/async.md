---
title: Async — omówienie
description: Dowiedz się, jak programowania asynchronicznego to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy.
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 85e30292fdc0e0e529eacdd328d4515bba5ee3e8
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="async-overview"></a><span data-ttu-id="72e8b-104">Async — omówienie</span><span class="sxs-lookup"><span data-stu-id="72e8b-104">Async Overview</span></span>

<span data-ttu-id="72e8b-105">Nie tak dawno temu aplikacje otrzymano szybciej po prostu przy zakupie nowszej komputerze lub serwerze, a następnie tego trendu zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="72e8b-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="72e8b-106">W rzeczywistości wycofać.</span><span class="sxs-lookup"><span data-stu-id="72e8b-106">In fact, it reversed.</span></span> <span data-ttu-id="72e8b-107">Telefony komórkowe pojawił się z 1ghz pojedynczego rdzenia ARM mikroukłady i obciążenia serwera są przenoszone do maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="72e8b-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="72e8b-108">Użytkownicy nadal mają reakcje interfejsu użytkownika, a właściciele firm serwerów, które firmy.</span><span class="sxs-lookup"><span data-stu-id="72e8b-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="72e8b-109">Przejście do przenośnych i chmury i podłączonej do Internetu populacji > Użytkownicy 3B spowodowało nowy zestaw wzorców oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="72e8b-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="72e8b-110">Aplikacje klienckie powinny być zawsze włączone, zawsze połączone i stale reakcji do interakcji z użytkownikiem (na przykład touch) z klasyfikacji magazynu wysoka!</span><span class="sxs-lookup"><span data-stu-id="72e8b-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="72e8b-111">Usługi powinny obsługiwać największego ruchu przez bezpiecznie skalowanie w górę i w dół.</span><span class="sxs-lookup"><span data-stu-id="72e8b-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="72e8b-112">Programowanie asynchroniczne to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="72e8b-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="72e8b-113">.NET oferuje możliwość reakcji i elastycznych z łatwy w użyciu, poziom języka asynchroniczne modele programowania w języku C#, VB i F # dla aplikacji i usług.</span><span class="sxs-lookup"><span data-stu-id="72e8b-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="72e8b-114">Dlaczego należy pisać kod Async?</span><span class="sxs-lookup"><span data-stu-id="72e8b-114">Why Write Async Code?</span></span>

<span data-ttu-id="72e8b-115">Nowoczesne aplikacje należy zwiększone użycie operacji We/Wy plików i sieci.</span><span class="sxs-lookup"><span data-stu-id="72e8b-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="72e8b-116">W efekcie niską użytkowników oraz wykorzystanie sprzętu, chyba że chcesz nauczenia i używania trudne wzorce API we/wy tradycyjnie bloku domyślnie.</span><span class="sxs-lookup"><span data-stu-id="72e8b-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="72e8b-117">Oparty na zadaniach asynchronicznej interfejsów API i model programowania asynchronicznego poziom języka Odwróć tego modelu, co wykonanie asynchroniczne domyślnej z kilku nowych pojęć, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="72e8b-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="72e8b-118">Kod Async ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="72e8b-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="72e8b-119">Obsługuje więcej żądań serwera według reaguje wątków do obsługi żądań więcej podczas oczekiwania na żądań We/Wy do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="72e8b-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="72e8b-120">Umożliwia UI być bardziej elastyczny przez reaguje wątków interakcja interfejsu użytkownika podczas oczekiwania na we/wy żądań i przechodzenia długotrwałe pracy innych rdzeni Procesora.</span><span class="sxs-lookup"><span data-stu-id="72e8b-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="72e8b-121">Wiele nowszej interfejsów API architektury .NET jest asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="72e8b-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="72e8b-122">Jest łatwy do pisania kodu asynchronicznych w .NET!</span><span class="sxs-lookup"><span data-stu-id="72e8b-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="72e8b-123">Co to jest dalej?</span><span class="sxs-lookup"><span data-stu-id="72e8b-123">What's next?</span></span>

<span data-ttu-id="72e8b-124">Aby uzyskać więcej informacji, zobacz [Async szczegółowo](async-in-depth.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="72e8b-124">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="72e8b-125">[Wzorce programowania asynchronicznego](/asynchronous-programming-patterns/index.md) temat zawiera omówienie trzy wzorce programowania asynchronicznego obsługiwane w środowisku .NET:</span><span class="sxs-lookup"><span data-stu-id="72e8b-125">The [Asynchronous Programming Patterns](/asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
-   <span data-ttu-id="72e8b-126">[Asynchroniczne programowania modelu (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsze)</span><span class="sxs-lookup"><span data-stu-id="72e8b-126">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
-   <span data-ttu-id="72e8b-127">[Oparty na zdarzeniach asynchroniczny wzorzec (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starsze)</span><span class="sxs-lookup"><span data-stu-id="72e8b-127">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
-   <span data-ttu-id="72e8b-128">[Oparty na zadaniach asynchronicznej wzorca (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (zalecane w przypadku nowych wdrożeń)</span><span class="sxs-lookup"><span data-stu-id="72e8b-128">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="72e8b-129">Aby uzyskać więcej informacji na temat zalecanych model programowania opartego na zadaniach, zobacz [programowania asynchronicznego opartego na zadaniach](parallel-programming/task-based-asynchronous-programming.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="72e8b-129">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
