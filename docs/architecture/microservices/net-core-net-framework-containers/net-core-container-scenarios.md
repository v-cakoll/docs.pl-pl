---
title: Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Kiedy należy wybrać platformę .NET Core dla kontenerów platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 54ed1b4bbb16352b8c99204383f85ffb25d62be7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296501"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a><span data-ttu-id="2a1cd-103">Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="2a1cd-103">When to choose .NET Core for Docker containers</span></span>

<span data-ttu-id="2a1cd-104">Modularność i lekki charakter platformy .NET Core sprawia, że jest idealnym rozwiązaniem dla kontenerów.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-104">The modularity and lightweight nature of .NET Core makes it perfect for containers.</span></span> <span data-ttu-id="2a1cd-105">Po wdrożeniu i uruchomieniu kontenera jego obraz jest znacznie mniejszy od platformy .NET Core niż z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-105">When you deploy and start a container, its image is far smaller with .NET Core than with .NET Framework.</span></span> <span data-ttu-id="2a1cd-106">Z drugiej strony, aby użyć .NET Framework dla kontenera, należy oprzeć obraz na podstawowym obrazie systemu Windows Server, który jest dużo większy niż obrazy systemu Windows nano Server lub Linux, które są używane dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-106">In contrast, to use .NET Framework for a container, you must base your image on the Windows Server Core image, which is a lot heavier than the Windows Nano Server or Linux images that you use for .NET Core.</span></span>

<span data-ttu-id="2a1cd-107">Ponadto platforma .NET Core jest międzyplatformowa, dzięki czemu można wdrażać aplikacje serwera przy użyciu obrazów z systemem Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-107">Additionally, .NET Core is cross-platform, so you can deploy server apps with Linux or Windows container images.</span></span> <span data-ttu-id="2a1cd-108">Jeśli jednak używasz tradycyjnego .NET Framework, możesz wdrażać tylko obrazy oparte na systemie Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-108">However, if you are using the traditional .NET Framework, you can only deploy images based on Windows Server Core.</span></span>

<span data-ttu-id="2a1cd-109">Poniżej znajduje się bardziej szczegółowy opis dlaczego należy wybrać platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-109">The following is a more detailed explanation of why to choose .NET Core.</span></span>

## <a name="developing-and-deploying-cross-platform"></a><span data-ttu-id="2a1cd-110">Tworzenie i wdrażanie wielu platform</span><span class="sxs-lookup"><span data-stu-id="2a1cd-110">Developing and deploying cross platform</span></span>

<span data-ttu-id="2a1cd-111">Jasno, jeśli celem jest posiadanie aplikacji (aplikacji sieci Web lub usługi), która może być uruchamiana na wielu platformach obsługiwanych przez platformę Docker (Linux i Windows), właściwy wybór to .NET Core, ponieważ .NET Framework obsługuje tylko system Windows.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-111">Clearly, if your goal is to have an application (web app or service) that can run on multiple platforms supported by Docker (Linux and Windows), the right choice is .NET Core, because .NET Framework only supports Windows.</span></span>

<span data-ttu-id="2a1cd-112">Program .NET Core obsługuje również macOS jako platformę programistyczną.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-112">.NET Core also supports macOS as a development platform.</span></span> <span data-ttu-id="2a1cd-113">Jednak podczas wdrażania kontenerów na hoście platformy Docker ten host musi (obecnie) być oparty na systemie Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-113">However, when you deploy containers to a Docker host, that host must (currently) be based on Linux or Windows.</span></span> <span data-ttu-id="2a1cd-114">Na przykład w środowisku deweloperskim można użyć maszyny wirtualnej z systemem Linux działającej na komputerze Mac.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-114">For example, in a development environment, you could use a Linux VM running on a Mac.</span></span>

<span data-ttu-id="2a1cd-115">[Program Visual Studio](https://www.visualstudio.com/vs/) udostępnia zintegrowane środowisko programistyczne (IDE) dla systemu Windows i obsługuje programowanie platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-115">[Visual Studio](https://www.visualstudio.com/vs/) provides an integrated development environment (IDE) for Windows and supports Docker development.</span></span>

<span data-ttu-id="2a1cd-116">[Visual Studio dla komputerów Mac](https://www.visualstudio.com/vs/visual-studio-mac/) to IDE, ewolucja Xamarin Studio, która działa w macOS i obsługuje tworzenie aplikacji opartych na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-116">[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="2a1cd-117">Powinno to być preferowany wybór dla deweloperów pracujących na komputerach Mac, którzy chcą również korzystać z zaawansowanego środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-117">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="2a1cd-118">Możesz również użyć [Visual Studio Code](https://code.visualstudio.com/) (vs Code) w systemach MacOS, Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-118">You can also use [Visual Studio Code](https://code.visualstudio.com/) (VS Code) on macOS, Linux, and Windows.</span></span> <span data-ttu-id="2a1cd-119">VS Code w pełni obsługuje platformę .NET Core, w tym IntelliSense i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-119">VS Code fully supports .NET Core, including IntelliSense and debugging.</span></span> <span data-ttu-id="2a1cd-120">Ponieważ VS Code jest lekkim edytorem, można go użyć do tworzenia kontenerów aplikacji na komputerach Mac w połączeniu z [interfejsem wiersza polecenia platformy](../../../core/tools/index.md)Docker i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-120">Because VS Code is a lightweight editor, you can use it to develop containerized apps on the Mac in conjunction with the Docker CLI and the [.NET Core command-line interface (CLI)](../../../core/tools/index.md).</span></span> <span data-ttu-id="2a1cd-121">Możesz również wskazać platformę .NET Core za pomocą większości edytorów innych firm, takich jak subwapno, Emacs:, VI i projekt typu open source OmniSharp, który oferuje również obsługę technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-121">You can also target .NET Core with most third-party editors like Sublime, Emacs, vi, and the open-source OmniSharp project, which also provides IntelliSense support.</span></span>

<span data-ttu-id="2a1cd-122">Oprócz środowisk IDE i edytorów, można użyć narzędzi [interfejs wiersza polecenia platformy .NET Core](../../../core/tools/index.md) dla wszystkich obsługiwanych platform.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-122">In addition to the IDEs and editors, you can use the [.NET Core CLI](../../../core/tools/index.md) tools for all supported platforms.</span></span>

## <a name="using-containers-for-new-green-field-projects"></a><span data-ttu-id="2a1cd-123">Używanie kontenerów dla nowych projektów ("zielony-pole")</span><span class="sxs-lookup"><span data-stu-id="2a1cd-123">Using containers for new ("green-field") projects</span></span>

<span data-ttu-id="2a1cd-124">Kontenery są często używane w połączeniu z architekturą mikrousług, chociaż mogą być również używane do konteneryzowanie aplikacji lub usług sieci Web, które są zgodne z dowolnym wzorcem architektury.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-124">Containers are commonly used in conjunction with a microservices architecture, although they can also be used to containerize web apps or services that follow any architectural pattern.</span></span> <span data-ttu-id="2a1cd-125">.NET Framework w kontenerach systemu Windows, ale modularność i lekki charakter platformy .NET Core sprawia, że jest idealnym rozwiązaniem w przypadku kontenerów i architektur mikrousług.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-125">You can use .NET Framework on Windows Containers, but the modularity and lightweight nature of .NET Core makes it perfect for containers and microservices architectures.</span></span> <span data-ttu-id="2a1cd-126">Po utworzeniu i wdrożeniu kontenera jego obraz jest znacznie mniejszy przy użyciu platformy .NET Core niż z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-126">When you create and deploy a container, its image is far smaller with .NET Core than with .NET Framework.</span></span>

## <a name="creating-and-deploying-microservices-on-containers"></a><span data-ttu-id="2a1cd-127">Tworzenie i wdrażanie mikrousług w kontenerach</span><span class="sxs-lookup"><span data-stu-id="2a1cd-127">Creating and deploying microservices on containers</span></span>

<span data-ttu-id="2a1cd-128">Można użyć tradycyjnego .NET Framework do tworzenia aplikacji opartych na mikrousługach (bez kontenerów) za pomocą zwykłych procesów.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-128">You could use the traditional .NET Framework for building microservices-based applications (without containers) by using plain processes.</span></span> <span data-ttu-id="2a1cd-129">Dzięki temu, ponieważ .NET Framework są już zainstalowane i udostępniane między procesami, procesy są jasne i szybkie, aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-129">That way, because the .NET Framework is already installed and shared across processes, processes are light and fast to start.</span></span> <span data-ttu-id="2a1cd-130">Jeśli jednak korzystasz z kontenerów, obraz dla tradycyjnych .NET Framework jest również oparty na systemie Windows Server Core i sprawia, że jest zbyt ciężki dla podejścia mikrousługowego na kontenery.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-130">However, if you are using containers, the image for the traditional .NET Framework is also based on Windows Server Core and that makes it too heavy for a microservices-on-containers approach.</span></span>

<span data-ttu-id="2a1cd-131">W przeciwieństwie do programu .NET Core jest najlepszym kandydatem, jeśli korzystasz z systemu opartego na mikrousługach opartych na kontenerach, ponieważ .NET Core jest lekki.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-131">In contrast, .NET Core is the best candidate if you are embracing a microservices-oriented system that is based on containers, because .NET Core is lightweight.</span></span> <span data-ttu-id="2a1cd-132">Ponadto powiązane z nimi obrazy kontenerów, obraz systemu Linux lub obraz Windows nano, to oszczędne i małe tworzenie pojemników, jasne i szybkie.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-132">In addition, its related container images, either the Linux image or the Windows Nano image, are lean and small making containers light and fast to start.</span></span>

<span data-ttu-id="2a1cd-133">Mikrousługa powinna być możliwie najmniejsza, jak to możliwe, aby było jasne, aby mieć niewielki wpływ na niewielką część (sprawdzanie DDD, [Projektowanie oparte na domenie](https://en.wikipedia.org/wiki/Domain-driven_design)), aby reprezentować mały obszar wątpliwości i mieć możliwość szybkiego uruchamiania i zatrzymywania.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-133">A microservice is meant to be as small as possible: to be light when spinning up, to have a small footprint, to have a small Bounded Context (check DDD, [Domain-Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)), to represent a small area of concerns, and to be able to start and stop fast.</span></span> <span data-ttu-id="2a1cd-134">W przypadku tych wymagań należy użyć małych i szybkich obrazów kontenerów, takich jak obraz kontenera .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-134">For those requirements, you will want to use small and fast-to-instantiate container images like the .NET Core container image.</span></span>

<span data-ttu-id="2a1cd-135">Architektura mikrousług umożliwia również mieszanie technologii między granicami usług.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-135">A microservices architecture also allows you to mix technologies across a service boundary.</span></span> <span data-ttu-id="2a1cd-136">Dzięki temu można stopniowo przeprowadzić migrację do platformy .NET Core dla nowych mikrousług, które działają w połączeniu z innymi mikrousługami lub usługami opracowanymi przy użyciu technologii Node. js, Python, Java, GoLang lub innych.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-136">This enables a gradual migration to .NET Core for new microservices that work in conjunction with other microservices or with services developed with Node.js, Python, Java, GoLang, or other technologies.</span></span>

## <a name="deploying-high-density-in-scalable-systems"></a><span data-ttu-id="2a1cd-137">Wdrażanie wysokiej gęstości w skalowalnych systemach</span><span class="sxs-lookup"><span data-stu-id="2a1cd-137">Deploying high density in scalable systems</span></span>

<span data-ttu-id="2a1cd-138">Gdy system oparty na kontenerach wymaga najlepszej możliwej gęstości, szczegółowości i wydajności, program .NET Core i ASP.NET Core są najlepszymi opcjami.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-138">When your container-based system needs the best possible density, granularity, and performance, .NET Core and ASP.NET Core are your best options.</span></span> <span data-ttu-id="2a1cd-139">ASP.NET Core jest nawet dziesięć razy szybsze niż ASP.NET w tradycyjnych .NET Framework i prowadzi do innych popularnych technologii branżowych dla mikrousług, takich jak Java serwletów, go i Node. js.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-139">ASP.NET Core is up to ten times faster than ASP.NET in the traditional .NET Framework, and it leads other popular industry technologies for microservices, such as Java servlets, Go, and Node.js.</span></span>

<span data-ttu-id="2a1cd-140">Jest to szczególnie istotne w przypadku architektury mikrousług, w których można korzystać z setek mikrousług (kontenerów).</span><span class="sxs-lookup"><span data-stu-id="2a1cd-140">This is especially relevant for microservices architectures, where you could have hundreds of microservices (containers) running.</span></span> <span data-ttu-id="2a1cd-141">W przypadku obrazów ASP.NET Core (opartych na środowisku uruchomieniowym .NET Core) w systemie Linux lub Windows nano można uruchomić system z znacznie mniejszą liczbą serwerów lub maszyn wirtualnych, co ostatecznie oszczędza koszty infrastruktury i hostingu.</span><span class="sxs-lookup"><span data-stu-id="2a1cd-141">With ASP.NET Core images (based on the .NET Core runtime) on Linux or Windows Nano, you can run your system with a much lower number of servers or VMs, ultimately saving costs in infrastructure and hosting.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2a1cd-142">[Poprzedni](general-guidance.md)Następny
>[](net-framework-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="2a1cd-142">[Previous](general-guidance.md)
[Next](net-framework-container-scenarios.md)</span></span>