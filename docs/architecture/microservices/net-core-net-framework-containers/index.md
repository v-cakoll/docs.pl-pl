---
title: Wybieranie między programami .NET Core i .NET Framework dla kontenerów platformy Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Wybieranie między programami .NET Core i .NET Framework dla kontenerów platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849273"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="32659-103">Wybieranie między programami .NET Core i .NET Framework dla kontenerów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="32659-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="32659-104">Istnieją dwie obsługiwane struktury do kompilowania aplikacji platformy Docker po stronie serwera z platformą .NET: [.NET Framework i .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="32659-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="32659-105">Współużytkują one wiele składników platformy .NET i można udostępniać kod w obu tych składnikach.</span><span class="sxs-lookup"><span data-stu-id="32659-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="32659-106">Istnieją jednak podstawowe różnice między nimi i używane struktury zależą od tego, co chcesz osiągnąć.</span><span class="sxs-lookup"><span data-stu-id="32659-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="32659-107">Ta sekcja zawiera wskazówki dotyczące sytuacji, w których należy wybrać poszczególne struktury.</span><span class="sxs-lookup"><span data-stu-id="32659-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="32659-108">[Poprzedni](../container-docker-introduction/docker-containers-images-registries.md)Następny
>[](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="32659-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
