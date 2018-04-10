---
title: Wprowadzenie do kontenerów i Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wprowadzenie do kontenerów i Docker
keywords: Docker, Mikrousług, ASP.NET, kontenera
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8809ae41609ff0e2d2fc969d412cb5edc8939653
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="07098-104">Wprowadzenie do kontenerów i Docker</span><span class="sxs-lookup"><span data-stu-id="07098-104">Introduction to Containers and Docker</span></span>

<span data-ttu-id="07098-105">Przechowywanie w kontenerach jest podejście do rozwoju oprogramowania, w której aplikacja lub usługi, jego zależności i jego konfiguracji (pobieranej jako pliki manifestu wdrożenia) jednym pakiecie jako obraz kontenera.</span><span class="sxs-lookup"><span data-stu-id="07098-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="07098-106">Konteneryzowanych aplikacji można przetestować jako jednostki i wdrażać jako kontener wystąpienie obrazu systemu operacyjnego hosta (systemu operacyjnego).</span><span class="sxs-lookup"><span data-stu-id="07098-106">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="07098-107">Tak samo, jak kontenery wysyłki umożliwiają transportu dostawy, pociągu lub ciężarówka niezależnie od ładunku wewnątrz towarów, kontenery oprogramowania działają jako standardowa jednostka oprogramowania, które mogą zawierać różne kodu i zależności.</span><span class="sxs-lookup"><span data-stu-id="07098-107">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="07098-108">Containerizing oprogramowania w ten sposób umożliwia deweloperom i informatykom je wdrożyć w środowiskach z żadnych modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="07098-108">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="07098-109">Kontenery również izolowania aplikacji od siebie na udostępnionych systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="07098-109">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="07098-110">Konteneryzowanych aplikacje są uruchamiane na górze kontenera hosta, który z kolei jest uruchamiany na system operacyjny (Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="07098-110">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="07098-111">Kontenery więc znacznie mniej miejsca niż obrazy maszyny wirtualnej (VM).</span><span class="sxs-lookup"><span data-stu-id="07098-111">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="07098-112">Każdego kontenera można uruchomić aplikacji sieci web całego lub usługi, jak pokazano w rysunku 2-1.</span><span class="sxs-lookup"><span data-stu-id="07098-112">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="07098-113">W tym przykładzie Docker host jest hostem kontenera, i App1, App2 Svc 1 i Svc 2 konteneryzowanych aplikacji lub usług.</span><span class="sxs-lookup"><span data-stu-id="07098-113">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![](./media/image1.png)

<span data-ttu-id="07098-114">**Rysunek 2-1**.</span><span class="sxs-lookup"><span data-stu-id="07098-114">**Figure 2-1**.</span></span> <span data-ttu-id="07098-115">Wiele kontenerów uruchomiona na hoście kontenera</span><span class="sxs-lookup"><span data-stu-id="07098-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="07098-116">Inną zaletą przechowywanie w kontenerach jest skalowalność.</span><span class="sxs-lookup"><span data-stu-id="07098-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="07098-117">Możesz skalować w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań.</span><span class="sxs-lookup"><span data-stu-id="07098-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="07098-118">Z punktu widzenia aplikacji tworzenie wystąpień obrazu (utworzenie kontenera) jest podobny do tworzenia wystąpienia procesów, takich jak usługi lub aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="07098-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="07098-119">Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zwykle ma każdego kontenera (wystąpienia obrazu) do uruchomienia na serwerze innego hosta lub maszyny Wirtualnej w domenach awarii innego.</span><span class="sxs-lookup"><span data-stu-id="07098-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="07098-120">Krótko mówiąc kontenery oferuje zalet izolacji, przenośność elastyczności, skalowalności i kontroli dla przepływu pracy z cyklem życia całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07098-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="07098-121">Najważniejszą korzyścią jest izolacji udostępniane między deweloperów i Ops.</span><span class="sxs-lookup"><span data-stu-id="07098-121">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="07098-122">[Poprzednie] (.. / index.md) [dalej] (docker defined.md)</span><span class="sxs-lookup"><span data-stu-id="07098-122">[Previous] (../index.md) [Next] (docker-defined.md)</span></span>
