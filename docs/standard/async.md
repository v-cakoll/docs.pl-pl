---
title: Async — omówienie
description: Dowiedz się, jak programowanie async technika sprawia, że prosta do obsługi blokowania We/Wy i jednoczesnych operacji na wiele rdzeni.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: aa08389d896fa81dbed8a63bb22a97e151016392
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628805"
---
# <a name="async-overview"></a><span data-ttu-id="3ac82-103">Async — omówienie</span><span class="sxs-lookup"><span data-stu-id="3ac82-103">Async Overview</span></span>

<span data-ttu-id="3ac82-104">Nie tak dawno temu aplikacje szybciej po prostu kupując nowszej komputer lub serwer, a następnie ten trend zatrzymano usługę.</span><span class="sxs-lookup"><span data-stu-id="3ac82-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="3ac82-105">W rzeczywistości odwrócona.</span><span class="sxs-lookup"><span data-stu-id="3ac82-105">In fact, it reversed.</span></span> <span data-ttu-id="3ac82-106">Telefony komórkowe pojawiły się o 1ghz jednordzeniowy ARM mikroukładami i obciążenia serwera są przenoszone do maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="3ac82-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="3ac82-107">Użytkownicy nadal mają dynamicznym interfejsie użytkownika i właściciele firm ma serwerów, które można skalować z działalności.</span><span class="sxs-lookup"><span data-stu-id="3ac82-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="3ac82-108">Przejścia dla urządzeń przenośnych i chmury i podłączonej do Internetu populacji > Użytkownicy 3B spowodowało nowy zestaw wzorców oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="3ac82-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="3ac82-109">Aplikacje klienckie powinny być zawsze włączone zawsze połączone i stale elastyczna na interakcję z użytkownikiem (na przykład touch) przy użyciu klasyfikacji magazynu wysoka!</span><span class="sxs-lookup"><span data-stu-id="3ac82-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="3ac82-110">Usługi powinny obsługiwać skokami ruchu, bez problemu zmieniała skalując w górę i w dół.</span><span class="sxs-lookup"><span data-stu-id="3ac82-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="3ac82-111">Programowanie asynchroniczne to technika sprawia, że prosta do obsługi blokowania We/Wy i jednoczesnych operacji na wiele rdzeni.</span><span class="sxs-lookup"><span data-stu-id="3ac82-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="3ac82-112">.NET zapewnia możliwość dynamicznego i elastyczne z łatwe w użyciu, poziom języka programowania modelami asynchronicznymi w dla aplikacji i usług C#, VB i F#.</span><span class="sxs-lookup"><span data-stu-id="3ac82-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="3ac82-113">Dlaczego należy pisać kod asynchroniczny?</span><span class="sxs-lookup"><span data-stu-id="3ac82-113">Why Write Async Code?</span></span>

<span data-ttu-id="3ac82-114">Nowoczesne aplikacje należy zwiększone użycie operacji We/Wy plików i sieci.</span><span class="sxs-lookup"><span data-stu-id="3ac82-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="3ac82-115">Interfejsów API we/wy tradycyjnie Blokuj domyślnie powodujące niską użytkowej oraz wykorzystania zasobów sprzętowych, chyba że chcesz do nauczenia i używania pokonywania wyzwań wynikających ze wzorców.</span><span class="sxs-lookup"><span data-stu-id="3ac82-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="3ac82-116">Oparta na zadaniach asynchronicznej interfejsów API i model programowania asynchronicznego poziomu języka Odwróć ten model, dzięki czemu wykonanie asynchroniczne domyślnej z kilku nowych pojęć, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="3ac82-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="3ac82-117">Kod asynchroniczny ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="3ac82-117">Async code has the following characteristics:</span></span>

* <span data-ttu-id="3ac82-118">Obsługuje więcej żądań serwera według reaguje wątków może obsługiwać więcej żądania podczas oczekiwania na żądań We/Wy do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="3ac82-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="3ac82-119">Umożliwia UI większą responsywność reaguje wątków interakcja interfejsu użytkownika podczas oczekiwania na We/Wy i przechodzenie długotrwała praca, inne rdzeni procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="3ac82-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="3ac82-120">Wiele z nowszych interfejsów API platformy .NET są asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="3ac82-120">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="3ac82-121">To ułatwia pisanie kodu asynchronicznego w .NET!</span><span class="sxs-lookup"><span data-stu-id="3ac82-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="3ac82-122">Co dalej?</span><span class="sxs-lookup"><span data-stu-id="3ac82-122">What's next?</span></span>

<span data-ttu-id="3ac82-123">Aby uzyskać więcej informacji, zobacz [Async szczegółowo](async-in-depth.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="3ac82-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="3ac82-124">[Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) temat zawiera omówienie trzech asynchronicznych wzorcach programowania, obsługiwane na platformie .NET:</span><span class="sxs-lookup"><span data-stu-id="3ac82-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="3ac82-125">[Modelu programowania asynchronicznego (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsza wersja)</span><span class="sxs-lookup"><span data-stu-id="3ac82-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="3ac82-126">[Oparte na zdarzeniach asynchroniczny wzorzec (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starsza wersja)</span><span class="sxs-lookup"><span data-stu-id="3ac82-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="3ac82-127">[Oparta na zadaniach asynchronicznej wzorca (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (zalecane w przypadku nowych wdrożeń)</span><span class="sxs-lookup"><span data-stu-id="3ac82-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="3ac82-128">Aby uzyskać więcej informacji na temat zalecanych modelu programowania opartego na zadaniach, zobacz [programowania asynchronicznego opartego na zadaniach](parallel-programming/task-based-asynchronous-programming.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="3ac82-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
