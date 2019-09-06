---
title: Wskazówki ogólne
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Ogólne wskazówki
ms.date: 09/11/2018
ms.openlocfilehash: 0981cb16d5aa2036391caba0cf6ad3ac5c44ed6f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296529"
---
# <a name="general-guidance"></a><span data-ttu-id="e75f4-103">Wskazówki ogólne</span><span class="sxs-lookup"><span data-stu-id="e75f4-103">General guidance</span></span>

<span data-ttu-id="e75f4-104">Ta sekcja zawiera podsumowanie, kiedy należy wybrać platformę .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e75f4-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="e75f4-105">Więcej informacji o tych opcjach znajduje się w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="e75f4-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="e75f4-106">Należy używać platformy .NET Core z kontenerami systemu Linux lub Windows dla aplikacji serwera platformy Docker, gdy:</span><span class="sxs-lookup"><span data-stu-id="e75f4-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="e75f4-107">Wymagania dotyczące wielu platform.</span><span class="sxs-lookup"><span data-stu-id="e75f4-107">You have cross-platform needs.</span></span> <span data-ttu-id="e75f4-108">Na przykład chcesz użyć kontenerów systemów Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="e75f4-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="e75f4-109">Architektura aplikacji jest oparta na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="e75f4-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="e75f4-110">Należy szybko rozpocząć pracę z kontenerami i mieć niewielki wpływ na kontener, aby osiągnąć lepszą gęstość lub więcej kontenerów na jednostkę sprzętową w celu obniżenia kosztów.</span><span class="sxs-lookup"><span data-stu-id="e75f4-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="e75f4-111">W krótkim czasie podczas tworzenia nowych kontenerów aplikacji .NET należy rozważyć wybór domyślny dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e75f4-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="e75f4-112">Ma wiele korzyści i najlepiej pasuje do tej i stylu pracy kontenerów.</span><span class="sxs-lookup"><span data-stu-id="e75f4-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="e75f4-113">Dodatkową zaletą korzystania z platformy .NET Core jest możliwość uruchamiania równoległych wersji platformy .NET dla aplikacji znajdujących się na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e75f4-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="e75f4-114">Ta korzyść jest bardziej ważna w przypadku serwerów lub maszyn wirtualnych, które nie korzystają z kontenerów, ponieważ kontenery izolują wersje programu .NET, których potrzebuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e75f4-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="e75f4-115">(Pod warunkiem, że są one zgodne z bazowym systemem operacyjnym).</span><span class="sxs-lookup"><span data-stu-id="e75f4-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="e75f4-116">.NET Framework dla aplikacji serwera platformy Docker należy używać w przypadku:</span><span class="sxs-lookup"><span data-stu-id="e75f4-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="e75f4-117">Obecnie aplikacja używa .NET Framework i ma silne zależności w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="e75f4-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="e75f4-118">Należy używać interfejsów API systemu Windows, które nie są obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e75f4-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="e75f4-119">Musisz użyć bibliotek .NET innych firm lub pakietów NuGet, które nie są dostępne dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e75f4-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="e75f4-120">Używanie .NET Framework na platformie Docker może ulepszyć środowisko wdrażania, minimalizując problemy z wdrażaniem.</span><span class="sxs-lookup"><span data-stu-id="e75f4-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="e75f4-121">Ten [scenariusz "Unieś i Shift"](https://aka.ms/liftandshiftwithcontainersebook) jest istotny dla konteneryzowania starszych aplikacji, które zostały pierwotnie opracowane przy użyciu tradycyjnych .NET Framework, takich jak ASP.NET WebForms, Web Apps i WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="e75f4-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e75f4-122">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e75f4-122">Additional resources</span></span>

- <span data-ttu-id="e75f4-123">**eBook: Modernizacja istniejących aplikacji .NET Framework przy użyciu platformy Azure i kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="e75f4-123">**eBook: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

- <span data-ttu-id="e75f4-124">**Przykładowe aplikacje: Modernizacja starszych aplikacji internetowych ASP.NET przy użyciu kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="e75f4-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
><span data-ttu-id="e75f4-125">[Poprzedni](index.md)Następny
>[](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="e75f4-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
