---
title: Wybieranie między programami .NET Core i .NET Framework dla kontenerów platformy Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Wybieranie między programami .NET Core i .NET Framework dla kontenerów platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 771d23cf4610e5778f0a144386754ce10d6ae144
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296520"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="e6c04-103">Wybieranie między programami .NET Core i .NET Framework dla kontenerów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="e6c04-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="e6c04-104">Istnieją dwie obsługiwane struktury do kompilowania aplikacji platformy Docker po stronie serwera z platformą .NET: [.NET Framework i .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="e6c04-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="e6c04-105">Współużytkują one wiele składników platformy .NET i można udostępniać kod w obu tych składnikach.</span><span class="sxs-lookup"><span data-stu-id="e6c04-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="e6c04-106">Istnieją jednak podstawowe różnice między nimi i używane struktury zależą od tego, co chcesz osiągnąć.</span><span class="sxs-lookup"><span data-stu-id="e6c04-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="e6c04-107">Ta sekcja zawiera wskazówki dotyczące sytuacji, w których należy wybrać poszczególne struktury.</span><span class="sxs-lookup"><span data-stu-id="e6c04-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e6c04-108">[Poprzedni](../container-docker-introduction/docker-containers-images-registries.md)Następny
>[](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="e6c04-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
