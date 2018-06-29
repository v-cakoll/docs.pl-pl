---
title: Async — omówienie
description: Dowiedz się, jak programowania asynchronicznego to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9084da80ff400bf99fc8641c69bc38c805d039a
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071435"
---
# <a name="async-overview"></a><span data-ttu-id="1debe-103">Async — omówienie</span><span class="sxs-lookup"><span data-stu-id="1debe-103">Async Overview</span></span>

<span data-ttu-id="1debe-104">Nie tak dawno temu aplikacje otrzymano szybciej po prostu przy zakupie nowszej komputerze lub serwerze, a następnie tego trendu zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="1debe-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="1debe-105">W rzeczywistości wycofać.</span><span class="sxs-lookup"><span data-stu-id="1debe-105">In fact, it reversed.</span></span> <span data-ttu-id="1debe-106">Telefony komórkowe pojawił się z 1ghz pojedynczego rdzenia ARM mikroukłady i obciążenia serwera są przenoszone do maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="1debe-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="1debe-107">Użytkownicy nadal mają reakcje interfejsu użytkownika, a właściciele firm serwerów, które firmy.</span><span class="sxs-lookup"><span data-stu-id="1debe-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="1debe-108">Przejście do przenośnych i chmury i podłączonej do Internetu populacji > Użytkownicy 3B spowodowało nowy zestaw wzorców oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="1debe-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="1debe-109">Aplikacje klienckie powinny być zawsze włączone, zawsze połączone i stale reakcji do interakcji z użytkownikiem (na przykład touch) z klasyfikacji magazynu wysoka!</span><span class="sxs-lookup"><span data-stu-id="1debe-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="1debe-110">Usługi powinny obsługiwać największego ruchu przez bezpiecznie skalowanie w górę i w dół.</span><span class="sxs-lookup"><span data-stu-id="1debe-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="1debe-111">Programowanie asynchroniczne to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="1debe-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="1debe-112">.NET oferuje możliwość reakcji i elastycznych z łatwy w użyciu, poziom języka asynchroniczne modele programowania w języku C#, VB i F # dla aplikacji i usług.</span><span class="sxs-lookup"><span data-stu-id="1debe-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="1debe-113">Dlaczego należy pisać kod Async?</span><span class="sxs-lookup"><span data-stu-id="1debe-113">Why Write Async Code?</span></span>

<span data-ttu-id="1debe-114">Nowoczesne aplikacje należy zwiększone użycie operacji We/Wy plików i sieci.</span><span class="sxs-lookup"><span data-stu-id="1debe-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="1debe-115">W efekcie niską użytkowników oraz wykorzystanie sprzętu, chyba że chcesz nauczenia i używania trudne wzorce API we/wy tradycyjnie bloku domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1debe-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="1debe-116">Oparty na zadaniach asynchronicznej interfejsów API i model programowania asynchronicznego poziom języka Odwróć tego modelu, co wykonanie asynchroniczne domyślnej z kilku nowych pojęć, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="1debe-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="1debe-117">Kod Async ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="1debe-117">Async code has the following characteristics:</span></span>

* <span data-ttu-id="1debe-118">Obsługuje więcej żądań serwera według reaguje wątków do obsługi żądań więcej podczas oczekiwania na żądań We/Wy do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="1debe-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="1debe-119">Umożliwia UI być bardziej elastyczny przez reaguje wątków interakcja interfejsu użytkownika podczas oczekiwania na we/wy żądań i przechodzenia długotrwałe pracy innych rdzeni Procesora.</span><span class="sxs-lookup"><span data-stu-id="1debe-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="1debe-120">Wiele nowszej interfejsów API architektury .NET jest asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="1debe-120">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="1debe-121">Jest łatwy do pisania kodu asynchronicznych w .NET!</span><span class="sxs-lookup"><span data-stu-id="1debe-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="1debe-122">Co to jest dalej?</span><span class="sxs-lookup"><span data-stu-id="1debe-122">What's next?</span></span>

<span data-ttu-id="1debe-123">Aby uzyskać więcej informacji, zobacz [Async szczegółowo](async-in-depth.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="1debe-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="1debe-124">[Wzorce programowania asynchronicznego](asynchronous-programming-patterns/index.md) temat zawiera omówienie trzy wzorce programowania asynchronicznego obsługiwane w środowisku .NET:</span><span class="sxs-lookup"><span data-stu-id="1debe-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
-   <span data-ttu-id="1debe-125">[Asynchroniczne programowania modelu (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsze)</span><span class="sxs-lookup"><span data-stu-id="1debe-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
-   <span data-ttu-id="1debe-126">[Oparty na zdarzeniach asynchroniczny wzorzec (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starsze)</span><span class="sxs-lookup"><span data-stu-id="1debe-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
-   <span data-ttu-id="1debe-127">[Oparty na zadaniach asynchronicznej wzorca (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (zalecane w przypadku nowych wdrożeń)</span><span class="sxs-lookup"><span data-stu-id="1debe-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="1debe-128">Aby uzyskać więcej informacji na temat zalecanych model programowania opartego na zadaniach, zobacz [programowania asynchronicznego opartego na zadaniach](parallel-programming/task-based-asynchronous-programming.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="1debe-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
