---
title: Wprowadzenie do kontenerów i Docker
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e9f81c5fecc06b19ebd84cc4b2cc232686768a90
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106635"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="0b806-103">Wprowadzenie do kontenerów i Docker</span><span class="sxs-lookup"><span data-stu-id="0b806-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="0b806-104">Przechowywanie w kontenerach jest podejście do rozwoju oprogramowania, w której aplikacja lub usługi, jego zależności i jego konfiguracji (pobieranej jako pliki manifestu wdrożenia) jednym pakiecie jako obraz kontenera.</span><span class="sxs-lookup"><span data-stu-id="0b806-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="0b806-105">Następnie można przetestować aplikację konteneryzowanych jako jednostki i wdrożyć go jako kontener wystąpienie obrazu systemu operacyjnego hosta.</span><span class="sxs-lookup"><span data-stu-id="0b806-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="0b806-106">Tak samo jak w branży wysyłki używa standardowych kontenerów, aby przenieść towarów dostawy, pociągu lub ciężarówka, niezależnie od ładunku w tych kontenerach oprogramowania działają jako standardowa jednostka oprogramowania, które mogą zawierać różne kodu i zależności.</span><span class="sxs-lookup"><span data-stu-id="0b806-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="0b806-107">Wprowadzenie do oprogramowania w kontenerach umożliwia dla deweloperów i specjalistów IT do wdrożenia tych kontenerach w środowiskach z żadnych modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0b806-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="0b806-108">Kontenery również izolowania aplikacji od siebie na udostępnionych systemu operacyjnego (systemu operacyjnego).</span><span class="sxs-lookup"><span data-stu-id="0b806-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="0b806-109">Konteneryzowanych aplikacje działają hosta kontenera, który z kolei jest uruchamiany na system operacyjny (Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="0b806-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="0b806-110">W związku z tym kontenery zostały znacznie mniej miejsca niż obrazy maszyny wirtualnej (VM).</span><span class="sxs-lookup"><span data-stu-id="0b806-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="0b806-111">Każdego kontenera można uruchomić w całej aplikacji sieci web lub usługi, jak pokazano w rysunku 1-1.</span><span class="sxs-lookup"><span data-stu-id="0b806-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="0b806-112">Rysunek 1-1: wiele kontenerów uruchomiona na hoście kontenera</span><span class="sxs-lookup"><span data-stu-id="0b806-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="0b806-113">W tym przykładzie Docker Host jest hostem kontenera, i aplikacji 1, 2 aplikacji Svc 1 i Svc 2 konteneryzowanych aplikacji lub usług.</span><span class="sxs-lookup"><span data-stu-id="0b806-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="0b806-114">Kolejna korzyść związana, który może pochodzić od przechowywanie w kontenerach jest skalowalność.</span><span class="sxs-lookup"><span data-stu-id="0b806-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="0b806-115">Użytkownik może skalowalnego w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań.</span><span class="sxs-lookup"><span data-stu-id="0b806-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="0b806-116">Z punktu widzenia aplikacji *tworzenia wystąpienia obrazu* (utworzenie kontenera) jest podobny do tworzenia wystąpienia procesów, takich jak usługi lub aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="0b806-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="0b806-117">Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zwykle ma każdego kontenera (wystąpienia obrazu) do uruchomienia na serwerze innego hosta lub maszyny Wirtualnej w domenach awarii innego.</span><span class="sxs-lookup"><span data-stu-id="0b806-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="0b806-118">Krótko mówiąc kontenery oferuje zalet izolacji, przenośność elastyczności, skalowalności i kontroli dla przepływu pracy cyklu życia całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b806-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="0b806-119">Najważniejszą korzyścią jest izolacji udostępniane między deweloperów i Ops.</span><span class="sxs-lookup"><span data-stu-id="0b806-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
[<span data-ttu-id="0b806-120">Next</span><span class="sxs-lookup"><span data-stu-id="0b806-120">Next</span></span>](what-is-docker.md)
