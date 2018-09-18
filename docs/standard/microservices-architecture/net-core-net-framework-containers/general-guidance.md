---
title: Ogólne wskazówki
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Ogólne wskazówki
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: e77065614423cd2e7fdb51258a8c7650280d0400
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45968966"
---
# <a name="general-guidance"></a><span data-ttu-id="16b06-103">Ogólne wskazówki</span><span class="sxs-lookup"><span data-stu-id="16b06-103">General guidance</span></span>

<span data-ttu-id="16b06-104">Ta sekcja zawiera podsumowanie, kiedy należy wybrać .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16b06-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="16b06-105">Firma Microsoft zapewnia więcej szczegółów na temat tych opcji w kolejnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="16b06-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="16b06-106">Skorzystaj z platformy .NET Core z systemem Linux lub kontenerów Windows konteneryzowanej aplikacji serwera platformy Docker po:</span><span class="sxs-lookup"><span data-stu-id="16b06-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="16b06-107">Masz wymagania dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="16b06-107">You have cross-platform needs.</span></span> <span data-ttu-id="16b06-108">Na przykład chcesz użyć kontenery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="16b06-108">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="16b06-109">Architektury aplikacji jest oparta na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="16b06-109">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="16b06-110">Musisz szybko Uruchom kontenery i mają niewielkie rozmiary kontenera w celu osiągnięcia lepszej gęstości lub większej liczbie kontenerów na jednostkę sprzętu w celu obniżenia kosztów.</span><span class="sxs-lookup"><span data-stu-id="16b06-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="16b06-111">Krótko mówiąc podczas tworzenia nowych konteneryzowanych aplikacji platformy .NET, należy rozważyć platformy .NET Core jako domyślnego wyboru.</span><span class="sxs-lookup"><span data-stu-id="16b06-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="16b06-112">Ma wiele zalet i najbardziej zgodnym z kontenerów filozofii i stylu pracy.</span><span class="sxs-lookup"><span data-stu-id="16b06-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="16b06-113">Następującą dodatkową korzyść: za pomocą platformy .NET Core jest uruchomienie obok siebie wersji platformy .NET dla aplikacji w ramach tej samej maszynie.</span><span class="sxs-lookup"><span data-stu-id="16b06-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="16b06-114">Ta korzyść jest niezwykle ważne w przypadku serwerów lub maszyn wirtualnych, które nie korzystają z kontenerów, ponieważ kontenery izolowania wersji platformy .NET, która aplikacja potrzebuje.</span><span class="sxs-lookup"><span data-stu-id="16b06-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="16b06-115">(Tak długo, jak są one zgodne z podstawowego systemu operacyjnego.)</span><span class="sxs-lookup"><span data-stu-id="16b06-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="16b06-116">Należy używać .NET Framework dla konteneryzowanych aplikacji serwera platformy Docker po:</span><span class="sxs-lookup"><span data-stu-id="16b06-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="16b06-117">Aplikacja obecnie korzysta z .NET Framework i ma silną zależności od Windows.</span><span class="sxs-lookup"><span data-stu-id="16b06-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="16b06-118">Musisz użyć interfejsów API Windows, które nie są obsługiwane przez .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16b06-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="16b06-119">Musisz użyć biblioteki .NET innych firm lub pakiety NuGet, które nie są dostępne dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16b06-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="16b06-120">Przy użyciu .NET Framework na platformy Docker można poprawić środowisko wdrażania, minimalizując problemów dotyczących wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="16b06-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="16b06-121">To [scenariusza "metodą lift and shift"](https://aka.ms/liftandshiftwithcontainersebook) jest ważne w przypadku konteneryzowania starsze aplikacje, które zostały pierwotnie opracowana tradycyjnym środowisku .NET Framework, takich jak formularzy sieci Web platformy ASP.NET, MVC sieci web aplikacji lub usługi WCF (Windows Communication Foundation ) usługi.</span><span class="sxs-lookup"><span data-stu-id="16b06-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="16b06-122">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="16b06-122">Additional resources</span></span>

-   <span data-ttu-id="16b06-123">**Książka elektroniczna: modernizacji istniejących aplikacji .NET Framework z platformą Azure i kontenerów Windows**</span><span class="sxs-lookup"><span data-stu-id="16b06-123">**eBook: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

-   <span data-ttu-id="16b06-124">**Przykładowe aplikacje: modernizacji starsze aplikacje sieci web ASP.NET za pomocą kontenerów Windows**</span><span class="sxs-lookup"><span data-stu-id="16b06-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing


>[!div class="step-by-step"]
<span data-ttu-id="16b06-125">[Poprzednie](index.md)
[dalej](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="16b06-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
