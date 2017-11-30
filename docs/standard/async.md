---
title: "Async — omówienie"
description: "Dowiedz się, jak programowania asynchronicznego to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy."
keywords: .NET, .NET core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: bf0cc4ed21c92a57f3f5b2cfa27ac1f054e15172
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="async-overview"></a><span data-ttu-id="c7d82-104">Async — omówienie</span><span class="sxs-lookup"><span data-stu-id="c7d82-104">Async Overview</span></span>

<span data-ttu-id="c7d82-105">Nie tak dawno temu aplikacje otrzymano szybciej po prostu przy zakupie nowszej komputerze lub serwerze, a następnie tego trendu zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="c7d82-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="c7d82-106">W rzeczywistości wycofać.</span><span class="sxs-lookup"><span data-stu-id="c7d82-106">In fact, it reversed.</span></span> <span data-ttu-id="c7d82-107">Telefony komórkowe pojawił się z 1ghz pojedynczego rdzenia ARM mikroukłady i obciążenia serwera są przenoszone do maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="c7d82-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="c7d82-108">Użytkownicy nadal mają reakcje interfejsu użytkownika, a właściciele firm serwerów, które firmy.</span><span class="sxs-lookup"><span data-stu-id="c7d82-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="c7d82-109">Przejście do przenośnych i chmury i podłączonej do Internetu populacji > Użytkownicy 3B spowodowało nowy zestaw wzorców oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="c7d82-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="c7d82-110">Aplikacje klienckie powinny być zawsze włączone, zawsze połączone i stale reakcji do interakcji z użytkownikiem (na przykład touch) z klasyfikacji magazynu wysoka!</span><span class="sxs-lookup"><span data-stu-id="c7d82-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="c7d82-111">Usługi powinny obsługiwać największego ruchu przez bezpiecznie skalowanie w górę i w dół.</span><span class="sxs-lookup"><span data-stu-id="c7d82-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="c7d82-112">Programowanie asynchroniczne to technika klucza, która umożliwia proste do obsługi jednoczesnych operacji na wiele rdzeni i blokowania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="c7d82-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="c7d82-113">.NET oferuje możliwość reakcji i elastycznych z łatwy w użyciu, poziom języka asynchroniczne modele programowania w języku C#, VB i F # dla aplikacji i usług.</span><span class="sxs-lookup"><span data-stu-id="c7d82-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="c7d82-114">Dlaczego należy pisać kod Async?</span><span class="sxs-lookup"><span data-stu-id="c7d82-114">Why Write Async Code?</span></span>

<span data-ttu-id="c7d82-115">Nowoczesne aplikacje należy zwiększone użycie operacji We/Wy plików i sieci.</span><span class="sxs-lookup"><span data-stu-id="c7d82-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="c7d82-116">W efekcie niską użytkowników oraz wykorzystanie sprzętu, chyba że chcesz nauczenia i używania trudne wzorce API we/wy tradycyjnie bloku domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c7d82-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="c7d82-117">Oparty na zadaniach asynchronicznej interfejsów API i model programowania asynchronicznego poziom języka Odwróć tego modelu, co wykonanie asynchroniczne domyślnej z kilku nowych pojęć, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="c7d82-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="c7d82-118">Kod Async ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="c7d82-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="c7d82-119">Obsługuje więcej żądań serwera według reaguje wątków do obsługi żądań więcej podczas oczekiwania na żądań We/Wy do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="c7d82-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="c7d82-120">Umożliwia UI być bardziej elastyczny przez reaguje wątków interakcja interfejsu użytkownika podczas oczekiwania na we/wy żądań i przechodzenia długotrwałe pracy innych rdzeni Procesora.</span><span class="sxs-lookup"><span data-stu-id="c7d82-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="c7d82-121">Wiele nowszej interfejsów API architektury .NET jest asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="c7d82-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="c7d82-122">Jest łatwy do pisania kodu asynchronicznych w .NET!</span><span class="sxs-lookup"><span data-stu-id="c7d82-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="c7d82-123">Co to jest dalej?</span><span class="sxs-lookup"><span data-stu-id="c7d82-123">What's next?</span></span>

<span data-ttu-id="c7d82-124">Nowości w asynchronicznej pojęcia i programowania w języku, dla [Async szczegółowo](async-in-depth.md) i [programowania asynchronicznego opartego na zadaniach](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="c7d82-124">For a deep dive into async concepts and programming, see [Async in depth](async-in-depth.md) and [Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>
