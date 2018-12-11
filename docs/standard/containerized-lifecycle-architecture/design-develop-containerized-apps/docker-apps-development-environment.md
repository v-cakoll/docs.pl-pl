---
title: Środowisko programistyczne dla aplikacji platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 471b52fd577e5560bd93e6da50f2032d63eb2e6f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152419"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="877b8-103">Środowisko programistyczne dla aplikacji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="877b8-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="877b8-104">Opcje narzędzia do opracowywania: Środowiskiem IDE lub edytorem</span><span class="sxs-lookup"><span data-stu-id="877b8-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="877b8-105">Niezależnie od tego Jeśli wolisz, pełne i zaawansowanego środowiska IDE lub edytora lekkie i elastyczne, firma Microsoft ma potrzebne, jeśli chodzi o tworzenie aplikacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="877b8-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="877b8-106">Visual Studio Code i interfejsu wiersza polecenia Docker (narzędzi dla wielu platform dla systemów Mac, Linux i Windows)</span><span class="sxs-lookup"><span data-stu-id="877b8-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="877b8-107">Jeśli wolisz lekkie Międzyplatformowe Edytor Obsługa dowolnego języka programowania, można użyć programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="877b8-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="877b8-108">Te produkty zapewniają proste, ale niezawodne środowisko, co ma kluczowe znaczenie dla usprawnienie przepływu pracy dewelopera.</span><span class="sxs-lookup"><span data-stu-id="877b8-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="877b8-109">Instalując "Docker for Mac" lub "Docker for Windows" (środowisko programistyczne), deweloperzy platformy Docker można użyć pojedynczego interfejsu wiersza polecenia platformy Docker do tworzenia aplikacji Windows lub Linux (środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="877b8-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="877b8-110">Ponadto w Visual Studio Code obsługuje rozszerzenia dla platformy Docker za pomocą funkcji IntelliSense dla plików Dockerfile i skrót zadania to uruchamianie poleceń Docker z poziomu edytora.</span><span class="sxs-lookup"><span data-stu-id="877b8-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="877b8-111">Aby pobrać program Visual Studio Code, przejdź do <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="877b8-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="877b8-112">Aby pobrać platformy Docker dla systemów Mac i Windows, przejdź do <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="877b8-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="877b8-113">Visual Studio z narzędziami Docker</span><span class="sxs-lookup"><span data-stu-id="877b8-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="877b8-114">Podczas korzystania z programu Visual Studio 2015 można zainstalować dodatkowe narzędzia "Narzędzia platformy Docker dla programu Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="877b8-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="877b8-115">Dla programu Visual Studio 2017 narzędzia platformy Docker są wbudowane już.</span><span class="sxs-lookup"><span data-stu-id="877b8-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="877b8-116">W obu przypadkach można rozwijać, uruchamianie i Weryfikuj aplikacje bezpośrednio w wybranym środowisku platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="877b8-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="877b8-117">F5 aplikacji (jeden kontener lub wiele kontenerów) bezpośrednio do platformy Docker hosta debugowania lub naciśnij klawisze Ctrl + F5, aby edytować i odświeżać aplikację bez konieczności ponownego kompilowania kontenera.</span><span class="sxs-lookup"><span data-stu-id="877b8-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="877b8-118">Jest to najprostsza i bardziej wydajne wyborem dla deweloperów Windows tworzenie kontenerów platformy Docker dla systemu Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="877b8-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="877b8-119">Aby pobrać narzędzia aparatu Docker dla programu Visual Studio, przejdź do <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="877b8-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="877b8-120">Opcje języka i struktury</span><span class="sxs-lookup"><span data-stu-id="877b8-120">Language and framework choices</span></span>

<span data-ttu-id="877b8-121">Możesz opracowywać aplikacje platformy Docker i narzędzi firmy Microsoft przy użyciu najbardziej nowoczesnych języków.</span><span class="sxs-lookup"><span data-stu-id="877b8-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="877b8-122">Poniżej przedstawiono listę początkowej, ale nie są ograniczone do niego:</span><span class="sxs-lookup"><span data-stu-id="877b8-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="877b8-123">.NET Core i ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="877b8-123">.NET Core and ASP.NET Core</span></span>
-   <span data-ttu-id="877b8-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="877b8-124">Node.js</span></span>
-   <span data-ttu-id="877b8-125">Golang</span><span class="sxs-lookup"><span data-stu-id="877b8-125">Golang</span></span>
-   <span data-ttu-id="877b8-126">Java</span><span class="sxs-lookup"><span data-stu-id="877b8-126">Java</span></span>
-   <span data-ttu-id="877b8-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="877b8-127">Ruby</span></span>
-   <span data-ttu-id="877b8-128">Python</span><span class="sxs-lookup"><span data-stu-id="877b8-128">Python</span></span>

<span data-ttu-id="877b8-129">Zasadniczo można używać dowolnego języka modern, obsługiwane przez platformę Docker w systemie Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="877b8-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="877b8-130">[Poprzednie](orchestrate-high-scalability-availability.md)
>[dalej](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="877b8-130">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>