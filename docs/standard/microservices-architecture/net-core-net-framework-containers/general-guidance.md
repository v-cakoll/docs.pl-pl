---
title: "Ogólne wskazówki"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Ogólne wskazówki"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a><span data-ttu-id="41ec3-104">Ogólne wskazówki</span><span class="sxs-lookup"><span data-stu-id="41ec3-104">General guidance</span></span>

<span data-ttu-id="41ec3-105">Ta sekcja zawiera podsumowanie kiedy należy wybrać oprogramowanie .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41ec3-105">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="41ec3-106">Udostępniamy więcej szczegółów na temat tych opcji w kolejnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="41ec3-106">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="41ec3-107">Konteneryzowanych Docker aplikacji serwera należy używać .NET Core z systemem Linux lub kontenery systemu Windows, gdy:</span><span class="sxs-lookup"><span data-stu-id="41ec3-107">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="41ec3-108">Możesz korzystać z wielu platform.</span><span class="sxs-lookup"><span data-stu-id="41ec3-108">You have cross-platform needs.</span></span> <span data-ttu-id="41ec3-109">Na przykład chcesz używać kontenery systemu Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="41ec3-109">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="41ec3-110">Architektury aplikacji jest oparty na mikrousług.</span><span class="sxs-lookup"><span data-stu-id="41ec3-110">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="41ec3-111">Potrzebne do szybkiego uruchamiania kontenery i ma mało miejsca na kontener, aby osiągnąć lepszą gęstość lub więcej kontenerów na jednostkę sprzętu w celu zmniejszenia kosztów.</span><span class="sxs-lookup"><span data-stu-id="41ec3-111">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="41ec3-112">Krótko mówiąc podczas tworzenia nowych konteneryzowanych aplikacji .NET, należy rozważyć .NET Core jako domyślny wybór.</span><span class="sxs-lookup"><span data-stu-id="41ec3-112">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="41ec3-113">Ma wiele korzyści i najbardziej zgodnym z zasady kontenery klas i stylu pracy.</span><span class="sxs-lookup"><span data-stu-id="41ec3-113">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="41ec3-114">Dodatkową korzyścią z używania platformy .NET Core jest uruchomienie obok siebie wersje programu .NET dla aplikacji w tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="41ec3-114">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="41ec3-115">Świadczenie jest większe znaczenie dla serwerów i maszyn wirtualnych, które nie korzystają z kontenerów, ponieważ kontenery izolować wersje programu .NET, który aplikacja potrzebuje.</span><span class="sxs-lookup"><span data-stu-id="41ec3-115">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="41ec3-116">(O ile są one zgodne z podstawowego systemu operacyjnego.)</span><span class="sxs-lookup"><span data-stu-id="41ec3-116">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="41ec3-117">Konteneryzowanych Docker aplikacji serwera należy używać .NET Framework z kontenerami systemu Windows, gdy:</span><span class="sxs-lookup"><span data-stu-id="41ec3-117">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="41ec3-118">Aplikacja obecnie korzysta z platformy .NET Framework i ma silne zależności w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="41ec3-118">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="41ec3-119">Należy użyć interfejsów API systemu Windows, które nie są obsługiwane przez oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41ec3-119">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="41ec3-120">Należy użyć bibliotek .NET innych firm lub pakietów NuGet, które nie są dostępne dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41ec3-120">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="41ec3-121">Za pomocą .NET Framework na Docker może poprawić komfort pracy wdrażania zminimalizować problemy z wdrażaniem.</span><span class="sxs-lookup"><span data-stu-id="41ec3-121">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="41ec3-122">To [ *scenariusza "przyrostu i przesunięcia"* ](https://aka.ms/liftandshiftwithcontainersebook) jest ważna w przypadku starszych aplikacji, które pierwotnie opracowano z tradycyjnego .NET Framework, takich jak formularzy sieci Web ASP.NET, MVC sieci web aplikacji lub usługi WCF (containerizing Usługi Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="41ec3-122">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="41ec3-123">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="41ec3-123">Additional resources</span></span>

-   <span data-ttu-id="41ec3-124">**Książka elektroniczna: modernizacji istniejących aplikacji .NET Framework z platformy Azure i kontenery Windows**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="41ec3-124">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="41ec3-125">**Przykładowe aplikacje: modernizacji starsze aplikacje sieci web ASP.NET przy użyciu systemu Windows kontenery**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="41ec3-125">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="41ec3-126">[Poprzednie] (index.md) [dalej] (net-core kontenera scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="41ec3-126">[Previous] (index.md) [Next] (net-core-container-scenarios.md)</span></span>
