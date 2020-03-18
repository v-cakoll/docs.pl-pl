---
title: Środowisko deweloperskie dla aplikacji platformy Docker
description: Poznaj najważniejsze opcje narzędzi programistycznych, które obsługują cykl życia rozwoju platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71214302"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="147d9-103">Środowisko deweloperskie dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="147d9-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="147d9-104">Opcje narzędzi programistycznych: IDE lub edytor</span><span class="sxs-lookup"><span data-stu-id="147d9-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="147d9-105">Bez względu na to, czy wolisz pełny i wydajny IDE lub lekki i zwinny edytor, Microsoft ma Cię w około prawie, jeśli chodzi o tworzenie aplikacji Docker.</span><span class="sxs-lookup"><span data-stu-id="147d9-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="147d9-106">Visual Studio Code i Docker CLI (narzędzia międzyplatformowe dla komputerów Mac, Linux i Windows)</span><span class="sxs-lookup"><span data-stu-id="147d9-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="147d9-107">Jeśli wolisz lekki edytor między platformami obsługujący dowolny język deweloperski, możesz użyć kodu programu Visual Studio i identyfikatora docker CLI.</span><span class="sxs-lookup"><span data-stu-id="147d9-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="147d9-108">Produkty te zapewniają proste, ale niezawodne środowisko, które ma kluczowe znaczenie dla usprawnienia przepływu pracy dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="147d9-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="147d9-109">Instalując "Docker for Mac" lub "Docker for Windows" (środowisko programistyczne), deweloperzy platformy Docker mogą używać jednego środowiska cli platformy Docker do tworzenia aplikacji dla systemu Windows lub Linux (środowisko środowiska uruchomieniowego).</span><span class="sxs-lookup"><span data-stu-id="147d9-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="147d9-110">Ponadto program Visual Studio Code obsługuje rozszerzenia platformy Docker z intelliSense dla plików dockerfiles i zadania skrótów do uruchamiania poleceń platformy Docker z edytora.</span><span class="sxs-lookup"><span data-stu-id="147d9-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="147d9-111">Aby pobrać kod programu <https://code.visualstudio.com/download>Visual Studio, przejdź do .</span><span class="sxs-lookup"><span data-stu-id="147d9-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="147d9-112">Aby pobrać platformę Docker dla <https://www.docker.com/products/docker>komputerów Mac i system Windows, przejdź do witryny .</span><span class="sxs-lookup"><span data-stu-id="147d9-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="147d9-113">Visual Studio z narzędziami platformy Docker (komputer deweloperskie systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="147d9-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="147d9-114">Zaleca się używanie programu Visual Studio 2017 (lub nowszego) z włączonymi wbudowanymi narzędziami platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="147d9-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="147d9-115">Za pomocą programu Visual Studio można tworzyć, uruchamiać i weryfikować aplikacje bezpośrednio w wybranym środowisku platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="147d9-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="147d9-116">Naciśnij klawisz F5, aby debugować aplikację (pojedynczy kontener lub wiele kontenerów) bezpośrednio na hoście platformy Docker, lub naciśnij klawisze Ctrl+F5, aby edytować i odświeżać aplikację bez konieczności odbudowywania kontenera.</span><span class="sxs-lookup"><span data-stu-id="147d9-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="147d9-117">Jest to najprostszy i najpotężniejszy wybór dla deweloperów systemu Windows do tworzenia kontenerów Platformy Docker dla systemu Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="147d9-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="147d9-118">Visual Studio dla komputerów Mac (mac deweloper)</span><span class="sxs-lookup"><span data-stu-id="147d9-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="147d9-119">[Program Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) można używać podczas tworzenia aplikacji opartych na platformie Docker.</span><span class="sxs-lookup"><span data-stu-id="147d9-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="147d9-120">Visual Studio dla komputerów Mac oferuje bogatsze IDE w porównaniu do programu Visual Studio Code for Mac.</span><span class="sxs-lookup"><span data-stu-id="147d9-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="147d9-121">Wybór języka i struktury</span><span class="sxs-lookup"><span data-stu-id="147d9-121">Language and framework choices</span></span>

<span data-ttu-id="147d9-122">Aplikacje dokowania można tworzyć przy użyciu narzędzi firmy Microsoft w większości nowoczesnych języków.</span><span class="sxs-lookup"><span data-stu-id="147d9-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="147d9-123">Poniżej znajduje się wstępna lista, ale nie ograniczasz się do niej:</span><span class="sxs-lookup"><span data-stu-id="147d9-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="147d9-124">.NET Core i ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="147d9-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="147d9-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="147d9-125">Node.js</span></span>
- <span data-ttu-id="147d9-126">Przejdź</span><span class="sxs-lookup"><span data-stu-id="147d9-126">Go</span></span>
- <span data-ttu-id="147d9-127">Java</span><span class="sxs-lookup"><span data-stu-id="147d9-127">Java</span></span>
- <span data-ttu-id="147d9-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="147d9-128">Ruby</span></span>
- <span data-ttu-id="147d9-129">Python</span><span class="sxs-lookup"><span data-stu-id="147d9-129">Python</span></span>

<span data-ttu-id="147d9-130">Zasadniczo można użyć dowolnego nowoczesnego języka obsługiwanego przez platformę Docker w systemie Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="147d9-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="147d9-131">[Poprzedni](deploy-azure-kubernetes-service.md)
>[następny](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="147d9-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
