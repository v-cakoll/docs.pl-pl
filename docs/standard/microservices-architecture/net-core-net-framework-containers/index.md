---
title: "Wybór między .NET Core i .NET Framework dla kontenerów Docker"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wybór między .NET Core i .NET Framework dla kontenerów Docker"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f7a5fee26f4d138ae22f3551a25a674b22a2f6d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="e9290-104">Wybór między .NET Core i .NET Framework dla kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="e9290-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="e9290-105">Istnieją dwa implementacje obsługiwanych dla tworzenia po stronie serwera konteneryzowanych Docker aplikacji z platformą .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) i [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="e9290-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="e9290-106">Mają wiele składników platformy .NET Standard, a kod mogą udostępniać między nimi.</span><span class="sxs-lookup"><span data-stu-id="e9290-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="e9290-107">Istnieją jednak podstawowe różnice między nimi i implementacji, którego używasz będzie zależeć od co chcesz zrobić.</span><span class="sxs-lookup"><span data-stu-id="e9290-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="e9290-108">Ta sekcja zawiera wskazówki dotyczące sytuacji wybrać każdego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e9290-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e9290-109">[Poprzednie] (.. / container-docker-introduction/docker-containers-images-registries.md) [dalej] (Ogólne guidance.md)</span><span class="sxs-lookup"><span data-stu-id="e9290-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
