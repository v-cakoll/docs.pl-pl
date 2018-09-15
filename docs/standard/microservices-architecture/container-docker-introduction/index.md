---
title: Wprowadzenie do kontenerów i platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Wprowadzenie do kontenerów i platformy Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: bc99bbfc3adee4cdc7008a91f42659ebcaa7a1b1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658434"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="0f63a-103">Wprowadzenie do kontenerów i platformy Docker</span><span class="sxs-lookup"><span data-stu-id="0f63a-103">Introduction to Containers and Docker</span></span>

<span data-ttu-id="0f63a-104">Konteneryzacji to podejście do tworzenia oprogramowania, w którym aplikacji lub usługi, jego zależności i jego konfiguracji (wyodrębnione pliki manifestu wdrożenia) jednym pakiecie w postaci obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="0f63a-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="0f63a-105">Konteneryzowanej aplikacji można przetestować jako jednostka i wdrażane jako wystąpienia obrazu kontenera do hosta systemu operacyjnego (OS).</span><span class="sxs-lookup"><span data-stu-id="0f63a-105">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="0f63a-106">Po prostu dopuszcza wysyła kontenery transportu statku, szkolenie lub truck niezależnie od ładunku wewnątrz towarów, kontenery oprogramowania pełnić rolę pojedynczej jednostki standard wdrożenia oprogramowania, który może zawierać inny kod i zależności.</span><span class="sxs-lookup"><span data-stu-id="0f63a-106">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software deployment that can contain different code and dependencies.</span></span> <span data-ttu-id="0f63a-107">Konteneryzowania oprogramowania w ten sposób umożliwia deweloperom i informatykom, ich wdrażania w środowiskach o niewielkich modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0f63a-107">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="0f63a-108">Kontenery także izolowania aplikacji od siebie nawzajem na udostępnionym systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0f63a-108">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="0f63a-109">Konteneryzowane aplikacje uruchamiane w systemie hosta kontenera, który z kolei jest uruchamiany w systemach operacyjnych (Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="0f63a-109">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="0f63a-110">Kontenery w związku z tym mają znacznie mniejszy wyświetlacz niż obrazy maszyn wirtualnych (VM).</span><span class="sxs-lookup"><span data-stu-id="0f63a-110">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="0f63a-111">Każdy kontener można uruchomić aplikacji całej sieci web lub usługi, jak pokazano w rysunek 2-1.</span><span class="sxs-lookup"><span data-stu-id="0f63a-111">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="0f63a-112">W tym przykładzie hosta platformy Docker jest host kontenera i serwera App1, App2, Svc 1 i Svc 2 są konteneryzowanych aplikacji lub usług.</span><span class="sxs-lookup"><span data-stu-id="0f63a-112">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![Dwie aplikacje i dwie usługi działające w ramach systemu operacyjnego na maszynie Wirtualnej lub serwera fizycznego](./media/image1.png)

<span data-ttu-id="0f63a-114">**Rysunek 2-1**.</span><span class="sxs-lookup"><span data-stu-id="0f63a-114">**Figure 2-1**.</span></span> <span data-ttu-id="0f63a-115">Wiele kontenerów, działające na hoście kontenera</span><span class="sxs-lookup"><span data-stu-id="0f63a-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="0f63a-116">Kolejną korzyścią wynikającą z konteneryzacji jest skalowalność.</span><span class="sxs-lookup"><span data-stu-id="0f63a-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="0f63a-117">Można skalować w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań.</span><span class="sxs-lookup"><span data-stu-id="0f63a-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="0f63a-118">Z punktu widzenia aplikacji wystąpienia obrazu (utworzenie kontenera) jest podobne do tworzenia wystąpienia procesu, takich jak usługi lub aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="0f63a-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="0f63a-119">Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zazwyczaj chcesz każdego kontenera (obraz wystąpienia), aby uruchomić na innym serwerze hosta lub maszyn wirtualnych w różnych domenach błędów.</span><span class="sxs-lookup"><span data-stu-id="0f63a-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="0f63a-120">Krótko mówiąc kontenery oferują korzyści z izolacji, przenośność, elastyczność, skalowalność i kontroli w całej aplikacji przepływu pracy cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="0f63a-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="0f63a-121">Najważniejsze korzyści to środowisko izolacji udostępniane między deweloperskim i operacjami.</span><span class="sxs-lookup"><span data-stu-id="0f63a-121">The most important benefit is the environment's isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0f63a-122">[Poprzednie](../index.md)
[dalej](docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="0f63a-122">[Previous](../index.md)
[Next](docker-defined.md)</span></span>
