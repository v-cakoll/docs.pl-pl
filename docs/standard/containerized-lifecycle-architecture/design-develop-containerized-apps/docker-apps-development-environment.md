---
title: Środowisko projektowe dla aplikacji Docker
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c164b94572a8fde58124acaa14d47da574a19383
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="00bc1-103">Środowisko projektowe dla aplikacji Docker</span><span class="sxs-lookup"><span data-stu-id="00bc1-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="00bc1-104">Opcje narzędzi programistycznych: IDE lub edytora</span><span class="sxs-lookup"><span data-stu-id="00bc1-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="00bc1-105">Niezależnie Jeśli wolisz pełne i wydajne środowiska IDE lub edytora nieskomplikowane i elastyczne, firma Microsoft ma będzie po przejściu tworzenia aplikacji Docker.</span><span class="sxs-lookup"><span data-stu-id="00bc1-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="00bc1-106">Visual Studio Code i Docker interfejsu wiersza polecenia (narzędzia wieloplatformowe dla komputerów Mac, Linux i Windows)</span><span class="sxs-lookup"><span data-stu-id="00bc1-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="00bc1-107">Jeśli wolisz edytorze niewielka, między platformami obsługi żadnego języka programowania, można użyć programu Visual Studio Code i interfejsu wiersza polecenia Docker.</span><span class="sxs-lookup"><span data-stu-id="00bc1-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="00bc1-108">Te produkty zapewniają proste, ale niezawodne środowisko, co jest szczególnie ważne dla usprawnienie przepływu pracy deweloperów.</span><span class="sxs-lookup"><span data-stu-id="00bc1-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="00bc1-109">Instalując "Docker dla komputerów Mac" lub "Docker dla systemu Windows" (development environment), Docker deweloperzy mogą używać jednego interfejsu wiersza polecenia Docker, aby tworzyć aplikacje systemu Windows lub Linux (środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="00bc1-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="00bc1-110">Ponadto w Visual Studio Code obsługuje rozszerzenia dla Docker z technologii IntelliSense dla Dockerfiles oraz skrót zadania Docker poleceń w edytorze.</span><span class="sxs-lookup"><span data-stu-id="00bc1-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="00bc1-111">Aby pobrać program Visual Studio Code, przejdź do <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="00bc1-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="00bc1-112">Aby pobrać Docker dla systemów Mac i systemu Windows, przejdź do <http://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="00bc1-112">To download Docker for Mac and Windows, go to <http://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="00bc1-113">Program Visual Studio z narzędziami Docker</span><span class="sxs-lookup"><span data-stu-id="00bc1-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="00bc1-114">Podczas korzystania z programu Visual Studio 2015 można zainstalować dodatkowe narzędzia "Docker Tools for Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="00bc1-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="00bc1-115">Dla programu Visual Studio 2017 r narzędzia Docker są wbudowane już.</span><span class="sxs-lookup"><span data-stu-id="00bc1-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="00bc1-116">W obu przypadkach można rozwijać, uruchamiania i sprawdzanie poprawności aplikacji bezpośrednio w wybranym środowisku Docker.</span><span class="sxs-lookup"><span data-stu-id="00bc1-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="00bc1-117">F5 aplikacji (jeden kontener lub wielu kontenerów) bezpośrednio do Docker hosta z debugowaniem, lub naciśnij klawisze Ctrl + F5, edytowanie i odświeżanie aplikacji bez konieczności odbudować kontenera.</span><span class="sxs-lookup"><span data-stu-id="00bc1-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="00bc1-118">Jest to najprostsza i bardziej wydajne wybór dla deweloperów systemu Windows, tworzenie kontenerów Docker dla systemu Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="00bc1-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="00bc1-119">Aby pobrać narzędzia Docker dla programu Visual Studio, przejdź do <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="00bc1-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="00bc1-120">Opcje języka i framework</span><span class="sxs-lookup"><span data-stu-id="00bc1-120">Language and framework choices</span></span>

<span data-ttu-id="00bc1-121">Można programować aplikacje Docker i narzędzi firmy Microsoft z większość nowoczesnych języków.</span><span class="sxs-lookup"><span data-stu-id="00bc1-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="00bc1-122">Poniżej przedstawiono listę początkowej, ale nie są ograniczone do niej:</span><span class="sxs-lookup"><span data-stu-id="00bc1-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="00bc1-123">Oprogramowanie .NET core i ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="00bc1-123">.NET Core and ASP.NET Core</span></span>

-   <span data-ttu-id="00bc1-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="00bc1-124">Node.js</span></span>

-   <span data-ttu-id="00bc1-125">Golang</span><span class="sxs-lookup"><span data-stu-id="00bc1-125">Golang</span></span>

-   <span data-ttu-id="00bc1-126">Java</span><span class="sxs-lookup"><span data-stu-id="00bc1-126">Java</span></span>

-   <span data-ttu-id="00bc1-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="00bc1-127">Ruby</span></span>

-   <span data-ttu-id="00bc1-128">Python</span><span class="sxs-lookup"><span data-stu-id="00bc1-128">Python</span></span>

<span data-ttu-id="00bc1-129">Zasadniczo można użyć dowolnego nowoczesnych języków obsługiwanych przez Docker w systemie Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="00bc1-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="00bc1-130">[Poprzednie] (organizowania wysoki skalowalność availability.md) [dalej] (docker aplikacje — wewnętrzny pętli workflow.md)</span><span class="sxs-lookup"><span data-stu-id="00bc1-130">[Previous] (orchestrate-high-scalability-availability.md) [Next] (docker-apps-inner-loop-workflow.md)</span></span>
