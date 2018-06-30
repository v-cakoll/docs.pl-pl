---
title: Aplikacje oparte na proces Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Aplikacje oparte na proces Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 61bc9ca6fed8f5249dcb125619aa1b07f290ba7e
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106882"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="a0054-103">Proces tworzenia aplikacji opartych na Docker</span><span class="sxs-lookup"><span data-stu-id="a0054-103">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="a0054-104">*Opracowywanie konteneryzowanych aplikacji .NET lubisz, IDE fokus z programu Visual Studio i narzędzi Visual Studio tools for Docker lub interfejsu wiersza polecenia/Edytor fokus z interfejsu wiersza polecenia Docker i Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="a0054-104">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="a0054-105">Środowisko projektowe dla aplikacji Docker</span><span class="sxs-lookup"><span data-stu-id="a0054-105">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="a0054-106">Opcje narzędzia opracowywania: IDE lub edytora</span><span class="sxs-lookup"><span data-stu-id="a0054-106">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="a0054-107">Czy wolisz pełne i wydajne środowiska IDE lub edytora nieskomplikowane i elastyczne, firma Microsoft udostępnia narzędzia, które służą do tworzenia aplikacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a0054-107">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="a0054-108">**Visual Studio (dla systemu Windows)**.</span><span class="sxs-lookup"><span data-stu-id="a0054-108">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="a0054-109">Do tworzenia aplikacji opartych na Docker, użyj programu Visual Studio 2017 lub nowsze wersje, które jest dostarczany z tools for Docker już wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="a0054-109">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="a0054-110">Tools for Docker umożliwiają tworzenie, uruchamianie i sprawdzanie poprawności aplikacji bezpośrednio w środowisku docelowym Docker.</span><span class="sxs-lookup"><span data-stu-id="a0054-110">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="a0054-111">Naciśnij klawisz F5, aby uruchomić i debugowania aplikacji (jeden kontener lub wielu kontenerów) bezpośrednio do hostów Docker lub naciśnij klawisze CTRL + F5, edytowanie i odświeżanie aplikacji bez konieczności odbudować kontenera.</span><span class="sxs-lookup"><span data-stu-id="a0054-111">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="a0054-112">Jest to najbardziej zaawansowanych wybór programowanie dla aplikacji opartych na Docker.</span><span class="sxs-lookup"><span data-stu-id="a0054-112">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="a0054-113">**Visual Studio for Mac**.</span><span class="sxs-lookup"><span data-stu-id="a0054-113">**Visual Studio for Mac**.</span></span> <span data-ttu-id="a0054-114">Jest IDE ewolucja platformy Xamarin Studio uruchomionym w macOS i obsługuje tworzenie aplikacji opartej na Docker.</span><span class="sxs-lookup"><span data-stu-id="a0054-114">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="a0054-115">Powinno to być preferowany wybór dla deweloperów pracujących w komputerach Mac, również chcą korzystać z zaawansowanych IDE.</span><span class="sxs-lookup"><span data-stu-id="a0054-115">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="a0054-116">**Visual Studio Code i Docker CLI**.</span><span class="sxs-lookup"><span data-stu-id="a0054-116">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="a0054-117">Jeśli wolisz nieskomplikowane i Międzyplatformowe edytorze, który obsługuje dowolnego języka programowania, można użyć programu Microsoft Visual Studio (kod VS) i interfejsu wiersza polecenia Docker.</span><span class="sxs-lookup"><span data-stu-id="a0054-117">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="a0054-118">To podejście wiele platform dla komputerów Mac, Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="a0054-118">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="a0054-119">Instalując [Docker Community Edition (CE)](https://www.docker.com/community-edition) narzędzi, można użyć jednego interfejsu wiersza polecenia Docker umożliwia tworzenie aplikacji dla systemu Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="a0054-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="a0054-120">Ponadto program Visual Studio Code obsługuje rozszerzenia Docker, takie jak IntelliSense dla zadań Dockerfiles i skrót do uruchamiania polecenia Docker w edytorze.</span><span class="sxs-lookup"><span data-stu-id="a0054-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a0054-121">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="a0054-121">Additional resources</span></span>

-   <span data-ttu-id="a0054-122">**Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="a0054-122">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="a0054-123">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="a0054-123">**Visual Studio Code**.</span></span> <span data-ttu-id="a0054-124">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="a0054-124">Official site.</span></span>
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   <span data-ttu-id="a0054-125">**Docker Community Edition (CE) dla systemów Mac i systemu Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="a0054-125">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="a0054-126">.NET języków i struktur dla kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="a0054-126">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="a0054-127">Jak wspomniano we wcześniejszych sekcjach tego przewodnika, można użyć .NET Framework .NET Core i Mono projekt open source podczas opracowywania Docker konteneryzowanych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="a0054-127">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="a0054-128">Można tworzyć w języku C\#, F\#, lub Visual Basic, jeśli Linux lub kontenery systemu Windows, w zależności od tego, które .NET framework jest używana.</span><span class="sxs-lookup"><span data-stu-id="a0054-128">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="a0054-129">W przypadku języków about.NET więcej szczegółów, zobacz wpis w blogu [strategii języka .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="a0054-129">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a0054-130">[Poprzednie](../architect-microservice-container-applications/using-azure-service-fabric.md)
[dalej](docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a0054-130">[Previous](../architect-microservice-container-applications/using-azure-service-fabric.md)
[Next](docker-app-development-workflow.md)</span></span>
