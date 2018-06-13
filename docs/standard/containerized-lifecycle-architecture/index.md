---
title: Wprowadzenie do kontenerów i Docker
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 8d1062aaea85cf810fa07b36252974eceb227c43
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768284"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="a1618-103">Wprowadzenie do kontenerów i Docker</span><span class="sxs-lookup"><span data-stu-id="a1618-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="a1618-104">Przechowywanie w kontenerach jest podejście do rozwoju oprogramowania, w której aplikacja lub usługi, jego zależności i jego konfiguracji (pobieranej jako pliki manifestu wdrożenia) jednym pakiecie jako obraz kontenera.</span><span class="sxs-lookup"><span data-stu-id="a1618-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="a1618-105">Następnie można przetestować aplikację konteneryzowanych jako jednostki i wdrożyć go jako kontener wystąpienie obrazu systemu operacyjnego hosta.</span><span class="sxs-lookup"><span data-stu-id="a1618-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="a1618-106">Tak samo jak w branży wysyłki używa standardowych kontenerów, aby przenieść towarów dostawy, pociągu lub ciężarówka, niezależnie od ładunku w tych kontenerach oprogramowania działają jako standardowa jednostka oprogramowania, które mogą zawierać różne kodu i zależności.</span><span class="sxs-lookup"><span data-stu-id="a1618-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="a1618-107">Wprowadzenie do oprogramowania w kontenerach umożliwia dla deweloperów i specjalistów IT do wdrożenia tych kontenerach w środowiskach z żadnych modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="a1618-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="a1618-108">Kontenery również izolowania aplikacji od siebie na udostępnionych systemu operacyjnego (systemu operacyjnego).</span><span class="sxs-lookup"><span data-stu-id="a1618-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="a1618-109">Konteneryzowanych aplikacje działają hosta kontenera, który z kolei jest uruchamiany na system operacyjny (Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="a1618-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="a1618-110">W związku z tym kontenery zostały znacznie mniej miejsca niż obrazy maszyny wirtualnej (VM).</span><span class="sxs-lookup"><span data-stu-id="a1618-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="a1618-111">Każdego kontenera można uruchomić w całej aplikacji sieci web lub usługi, jak pokazano w rysunku 1-1.</span><span class="sxs-lookup"><span data-stu-id="a1618-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="a1618-112">Rysunek 1-1: wiele kontenerów uruchomiona na hoście kontenera</span><span class="sxs-lookup"><span data-stu-id="a1618-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="a1618-113">W tym przykładzie Docker Host jest hostem kontenera, i aplikacji 1, 2 aplikacji Svc 1 i Svc 2 konteneryzowanych aplikacji lub usług.</span><span class="sxs-lookup"><span data-stu-id="a1618-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="a1618-114">Kolejna korzyść związana, który może pochodzić od przechowywanie w kontenerach jest skalowalność.</span><span class="sxs-lookup"><span data-stu-id="a1618-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="a1618-115">Użytkownik może skalowalnego w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań.</span><span class="sxs-lookup"><span data-stu-id="a1618-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="a1618-116">Z punktu widzenia aplikacji *tworzenia wystąpienia obrazu* (utworzenie kontenera) jest podobny do tworzenia wystąpienia procesów, takich jak usługi lub aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="a1618-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="a1618-117">Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zwykle ma każdego kontenera (wystąpienia obrazu) do uruchomienia na serwerze innego hosta lub maszyny Wirtualnej w domenach awarii innego.</span><span class="sxs-lookup"><span data-stu-id="a1618-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="a1618-118">Krótko mówiąc kontenery oferuje zalet izolacji, przenośność elastyczności, skalowalności i kontroli dla przepływu pracy cyklu życia całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1618-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="a1618-119">Najważniejszą korzyścią jest izolacji udostępniane między deweloperów i Ops.</span><span class="sxs-lookup"><span data-stu-id="a1618-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a1618-120">[Next] (co to docker.md)</span><span class="sxs-lookup"><span data-stu-id="a1618-120">[Next] (what-is-docker.md)</span></span>
