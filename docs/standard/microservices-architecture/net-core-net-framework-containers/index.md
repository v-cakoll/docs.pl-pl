---
title: Wybór między .NET Core i .NET Framework dla kontenerów Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wybór między .NET Core i .NET Framework dla kontenerów Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b483214e7bd039a71ae642aa26e69d63222af8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="78e7f-103">Wybór między .NET Core i .NET Framework dla kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="78e7f-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="78e7f-104">Istnieją dwa implementacje obsługiwanych dla tworzenia po stronie serwera konteneryzowanych Docker aplikacji z platformą .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) i [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="78e7f-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="78e7f-105">Mają wiele składników platformy .NET Standard, a kod mogą udostępniać między nimi.</span><span class="sxs-lookup"><span data-stu-id="78e7f-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="78e7f-106">Istnieją jednak podstawowe różnice między nimi i implementacji, którego używasz będzie zależeć od co chcesz zrobić.</span><span class="sxs-lookup"><span data-stu-id="78e7f-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="78e7f-107">Ta sekcja zawiera wskazówki dotyczące sytuacji wybrać każdego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="78e7f-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="78e7f-108">[Poprzednie] (.. / container-docker-introduction/docker-containers-images-registries.md) [dalej] (Ogólne guidance.md)</span><span class="sxs-lookup"><span data-stu-id="78e7f-108">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
