---
title: Środowisko deweloperskie dla aplikacji platformy Docker
description: Ustal, jakimi najważniejszych opcjach narzędzia do programowania, które obsługują programowanie platformy Docker w cyklu życia.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3a2fcbe3b9380083622b6ce72cea4bab17d7c2ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799323"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="7f1a0-103">Środowisko deweloperskie dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="7f1a0-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="7f1a0-104">Opcje narzędzia do opracowywania: Środowiskiem IDE lub edytorem</span><span class="sxs-lookup"><span data-stu-id="7f1a0-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="7f1a0-105">Niezależnie od tego Jeśli wolisz, pełne i zaawansowanego środowiska IDE lub edytora lekkie i elastyczne, firma Microsoft ma potrzebne, jeśli chodzi o tworzenie aplikacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="7f1a0-106">Visual Studio Code i interfejsu wiersza polecenia Docker (narzędzi dla wielu platform dla systemów Mac, Linux i Windows)</span><span class="sxs-lookup"><span data-stu-id="7f1a0-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="7f1a0-107">Jeśli wolisz lekkie Międzyplatformowe Edytor Obsługa dowolnego języka programowania, można użyć programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="7f1a0-108">Te produkty zapewniają proste, ale niezawodne środowisko, co ma kluczowe znaczenie dla usprawnienie przepływu pracy dewelopera.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="7f1a0-109">Instalując "Docker for Mac" lub "Docker for Windows" (środowisko programistyczne), deweloperzy platformy Docker można użyć pojedynczego interfejsu wiersza polecenia platformy Docker do tworzenia aplikacji Windows lub Linux (środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="7f1a0-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="7f1a0-110">Ponadto w Visual Studio Code obsługuje rozszerzenia dla platformy Docker za pomocą funkcji IntelliSense dla plików Dockerfile i skrót zadania to uruchamianie poleceń Docker z poziomu edytora.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
>
> <span data-ttu-id="7f1a0-111">Aby pobrać program Visual Studio Code, przejdź do <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="7f1a0-112">Aby pobrać platformy Docker dla systemów Mac i Windows, przejdź do <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="7f1a0-113">Visual Studio z narzędziami Docker (komputerze deweloperskim Windows)</span><span class="sxs-lookup"><span data-stu-id="7f1a0-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="7f1a0-114">Zalecane jest użycie programu Visual Studio 2017 (lub późniejszy) za pomocą wbudowanych narzędzi platformy Docker, włączone.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="7f1a0-115">Za pomocą programu Visual Studio mogą tworzyć, uruchamianie i Weryfikuj aplikacje bezpośrednio w wybranym środowisku platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="7f1a0-116">Naciśnij klawisz F5, aby debugować aplikację (jeden kontener lub wiele kontenerów) bezpośrednio w hosta platformy Docker lub naciśnij klawisze Ctrl + F5, aby edytować i odświeżać aplikację bez konieczności ponownego kompilowania kontenera.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="7f1a0-117">Jest to najprostszy i najbardziej wydajnymi procesorami wybór dla deweloperów Windows do tworzenia kontenerów platformy Docker dla systemu Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="7f1a0-118">Program Visual Studio for Mac (komputerze deweloperskim Mac)</span><span class="sxs-lookup"><span data-stu-id="7f1a0-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="7f1a0-119">Możesz użyć [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) podczas tworzenia aplikacji opartych na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="7f1a0-120">Program Visual Studio for Mac oferuje rozbudowane środowisko IDE, w porównaniu do programu Visual Studio Code dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="7f1a0-121">Opcje języka i struktury</span><span class="sxs-lookup"><span data-stu-id="7f1a0-121">Language and framework choices</span></span>

<span data-ttu-id="7f1a0-122">Można tworzyć aplikacje platformy Docker przy użyciu narzędzia Microsoft większość nowoczesnych języków.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="7f1a0-123">Poniżej przedstawiono listę początkowej, ale nie trzeba się ograniczać do niego:</span><span class="sxs-lookup"><span data-stu-id="7f1a0-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="7f1a0-124">.NET Core i ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7f1a0-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="7f1a0-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="7f1a0-125">Node.js</span></span>
- <span data-ttu-id="7f1a0-126">Z rzeczywistym użyciem</span><span class="sxs-lookup"><span data-stu-id="7f1a0-126">Go</span></span>
- <span data-ttu-id="7f1a0-127">Java</span><span class="sxs-lookup"><span data-stu-id="7f1a0-127">Java</span></span>
- <span data-ttu-id="7f1a0-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="7f1a0-128">Ruby</span></span>
- <span data-ttu-id="7f1a0-129">Python</span><span class="sxs-lookup"><span data-stu-id="7f1a0-129">Python</span></span>

<span data-ttu-id="7f1a0-130">Zasadniczo można używać dowolnego języka modern, obsługiwane przez platformę Docker w systemie Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="7f1a0-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7f1a0-131">[Poprzednie](deploy-azure-kubernetes-service.md)
>[dalej](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7f1a0-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
