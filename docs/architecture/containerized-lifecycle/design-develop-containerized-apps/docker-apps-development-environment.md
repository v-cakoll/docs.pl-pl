---
title: Środowisko deweloperskie dla aplikacji platformy Docker
description: Poznaj najważniejsze opcje narzędzia deweloperskiego, które obsługują cykl życia platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214302"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="ae10f-103">Środowisko deweloperskie dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ae10f-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="ae10f-104">Opcje narzędzi programistycznych: IDE lub Edytor</span><span class="sxs-lookup"><span data-stu-id="ae10f-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="ae10f-105">Niezależnie od tego, czy wolisz pełną i wydajną platformę IDE, czy też Edytor uproszczony i Agile, firma Microsoft połączyła się z tworzeniem aplikacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ae10f-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="ae10f-106">Visual Studio Code i interfejs wiersza polecenia platformy Docker (narzędzia dla wielu platform dla systemów Mac, Linux i Windows)</span><span class="sxs-lookup"><span data-stu-id="ae10f-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="ae10f-107">Jeśli wolisz lekki Edytor Międzyplatformowy obsługujący dowolny język programowania, możesz użyć Visual Studio Code i interfejsu wiersza polecenia platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ae10f-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="ae10f-108">Te produkty zapewniają proste, a jeszcze niezawodne środowisko, które ma kluczowe znaczenie dla usprawnienia przepływu pracy dewelopera.</span><span class="sxs-lookup"><span data-stu-id="ae10f-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="ae10f-109">Instalując "Docker for Mac" lub "Docker for Windows" (środowisko programistyczne), deweloperzy platformy Docker mogą używać jednego interfejsu wiersza polecenia platformy Docker do kompilowania aplikacji dla systemu Windows lub Linux (środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="ae10f-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="ae10f-110">Dodatkowo Visual Studio Code obsługuje rozszerzenia dla platformy Docker z technologią IntelliSense dla wieloetapowe dockerfile oraz zadania skrótów do uruchamiania poleceń platformy Docker z edytora.</span><span class="sxs-lookup"><span data-stu-id="ae10f-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="ae10f-111">Aby pobrać Visual Studio Code, przejdź do <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="ae10f-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="ae10f-112">Aby pobrać platformę Docker dla komputerów Mac i Windows, przejdź do <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="ae10f-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="ae10f-113">Visual Studio z narzędziami platformy Docker (komputer deweloperski systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="ae10f-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="ae10f-114">Zalecamy używanie programu Visual Studio 2017 (lub nowszego) z włączonymi wbudowanymi narzędziami platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ae10f-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="ae10f-115">Za pomocą programu Visual Studio można opracowywać, uruchamiać i weryfikować aplikacje bezpośrednio w wybranym środowisku platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ae10f-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="ae10f-116">Naciśnij klawisz F5, aby debugować aplikację (pojedynczy kontener lub wiele kontenerów) bezpośrednio na hoście platformy Docker lub naciśnij klawisze CTRL + F5, aby edytować i odświeżyć aplikację bez konieczności ponownego kompilowania kontenera.</span><span class="sxs-lookup"><span data-stu-id="ae10f-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="ae10f-117">Jest to najprostszy i najbardziej zaawansowany wybór dla deweloperów systemu Windows do tworzenia kontenerów platformy Docker dla systemu Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="ae10f-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="ae10f-118">Visual Studio dla komputerów Mac (komputer deweloperski dla komputerów Mac)</span><span class="sxs-lookup"><span data-stu-id="ae10f-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="ae10f-119">Podczas tworzenia aplikacji opartych na platformie Docker można użyć [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) .</span><span class="sxs-lookup"><span data-stu-id="ae10f-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="ae10f-120">Visual Studio dla komputerów Mac oferuje bogatsze środowisko IDE w porównaniu do Visual Studio Code dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="ae10f-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="ae10f-121">Wybór języka i struktury</span><span class="sxs-lookup"><span data-stu-id="ae10f-121">Language and framework choices</span></span>

<span data-ttu-id="ae10f-122">Aplikacje platformy Docker można opracowywać przy użyciu narzędzi firmy Microsoft z większością nowoczesnych języków.</span><span class="sxs-lookup"><span data-stu-id="ae10f-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="ae10f-123">Poniżej znajduje się lista wstępna, ale nie jest ograniczona do niej:</span><span class="sxs-lookup"><span data-stu-id="ae10f-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="ae10f-124">.NET Core i ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae10f-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="ae10f-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="ae10f-125">Node.js</span></span>
- <span data-ttu-id="ae10f-126">Z rzeczywistym użyciem</span><span class="sxs-lookup"><span data-stu-id="ae10f-126">Go</span></span>
- <span data-ttu-id="ae10f-127">Java</span><span class="sxs-lookup"><span data-stu-id="ae10f-127">Java</span></span>
- <span data-ttu-id="ae10f-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="ae10f-128">Ruby</span></span>
- <span data-ttu-id="ae10f-129">Python</span><span class="sxs-lookup"><span data-stu-id="ae10f-129">Python</span></span>

<span data-ttu-id="ae10f-130">W zasadzie można użyć dowolnego nowoczesnego języka obsługiwanego przez platformę Docker w systemie Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="ae10f-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ae10f-131">[Poprzedni](deploy-azure-kubernetes-service.md)
>[Następny](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ae10f-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
