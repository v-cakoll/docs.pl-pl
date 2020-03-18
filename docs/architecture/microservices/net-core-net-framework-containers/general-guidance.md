---
title: Wskazówki ogólne
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Ogólne wytyczne
ms.date: 09/11/2018
ms.openlocfilehash: 2fa66d7593b764a8df4d9acc20f93d3f8fb26174
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089648"
---
# <a name="general-guidance"></a><span data-ttu-id="52a15-103">Wskazówki ogólne</span><span class="sxs-lookup"><span data-stu-id="52a15-103">General guidance</span></span>

<span data-ttu-id="52a15-104">Ta sekcja zawiera podsumowanie, kiedy wybrać .NET Core lub .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52a15-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="52a15-105">Więcej szczegółów na temat tych wyborów udostępniamy w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="52a15-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="52a15-106">Aby kontenerowa aplikacja serwera Platformy Docker była używana w kontenerach do serwera Platformy Docker, należy używać programu .NET Core z kontenerami systemu Linux lub Kontenerów systemu Windows, gdy:</span><span class="sxs-lookup"><span data-stu-id="52a15-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="52a15-107">Masz potrzeby wieloplatformowe.</span><span class="sxs-lookup"><span data-stu-id="52a15-107">You have cross-platform needs.</span></span> <span data-ttu-id="52a15-108">Na przykład chcesz używać kontenerów Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="52a15-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="52a15-109">Architektura aplikacji jest oparta na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="52a15-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="52a15-110">Musisz szybko uruchomić kontenery i chcesz mieć niewielką powierzchnię na kontener, aby osiągnąć lepszą gęstość lub więcej kontenerów na jednostkę sprzętową, aby obniżyć koszty.</span><span class="sxs-lookup"><span data-stu-id="52a15-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="52a15-111">Krótko mówiąc, podczas tworzenia nowych konteneryzowanych aplikacji .NET należy rozważyć .NET Core jako domyślny wybór.</span><span class="sxs-lookup"><span data-stu-id="52a15-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="52a15-112">Ma wiele zalet i najlepiej pasuje do filozofii pojemników i stylu pracy.</span><span class="sxs-lookup"><span data-stu-id="52a15-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="52a15-113">Dodatkową zaletą korzystania z programu .NET Core jest możliwość uruchamiania obok siebie wersji .NET dla aplikacji na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="52a15-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="52a15-114">Ta korzyść jest ważniejsza dla serwerów lub maszyn wirtualnych, które nie używają kontenerów, ponieważ kontenery izolują wersje .NET, których potrzebuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="52a15-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="52a15-115">(Tak długo, jak są one zgodne z podstawowym systemem operacyjnym).</span><span class="sxs-lookup"><span data-stu-id="52a15-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="52a15-116">Należy użyć .NET Framework dla konteneryzowanej aplikacji serwera Platformy Docker, gdy:</span><span class="sxs-lookup"><span data-stu-id="52a15-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="52a15-117">Aplikacja korzysta obecnie z platformy .NET Framework i ma silne zależności w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="52a15-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="52a15-118">Należy użyć interfejsów API systemu Windows, które nie są obsługiwane przez program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="52a15-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="52a15-119">Należy użyć bibliotek .NET innych firm lub pakietów NuGet, które nie są dostępne dla .NET Core.</span><span class="sxs-lookup"><span data-stu-id="52a15-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="52a15-120">Za pomocą platformy .NET Framework na platformie Docker można poprawić środowisko wdrażania, minimalizując problemy z wdrażaniem.</span><span class="sxs-lookup"><span data-stu-id="52a15-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="52a15-121">Ten [scenariusz "lift and shift"](https://aka.ms/liftandshiftwithcontainersebook) jest ważny dla konteneryzacji starszych aplikacji, które zostały pierwotnie opracowane przy tradycyjnych .NET Framework, takich jak ASP.NET WebForms, Aplikacje internetowe MVC lub Usługi WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="52a15-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="52a15-122">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="52a15-122">Additional resources</span></span>

- <span data-ttu-id="52a15-123">**E-book: Modernizacja istniejących aplikacji .NET Framework za pomocą platformy Azure i kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="52a15-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

- <span data-ttu-id="52a15-124">**Przykładowe aplikacje: modernizacja starszych ASP.NET aplikacji sieci Web przy użyciu kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="52a15-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
><span data-ttu-id="52a15-125">[Poprzedni](index.md)
>[następny](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="52a15-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
