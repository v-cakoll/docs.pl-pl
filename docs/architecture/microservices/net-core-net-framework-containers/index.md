---
title: Wybieranie między .NET Core i .NET Framework dla kontenerów platformy Docker
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Wybieranie między .NET Core i .NET Framework dla kontenerów platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70849273"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="f8502-103">Wybieranie między .NET Core i .NET Framework dla kontenerów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="f8502-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="f8502-104">Istnieją dwie obsługiwane struktury do tworzenia konteneryzowanych aplikacji dodocker po stronie serwera za pomocą .NET: [.NET Framework i .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="f8502-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="f8502-105">Współużytkują one wiele składników platformy .NET i można udostępniać kod między nimi.</span><span class="sxs-lookup"><span data-stu-id="f8502-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="f8502-106">Istnieją jednak podstawowe różnice między nimi, a które struktury, których używasz, będą zależeć od tego, co chcesz osiągnąć.</span><span class="sxs-lookup"><span data-stu-id="f8502-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="f8502-107">Ta sekcja zawiera wskazówki dotyczące wyboru każdej struktury.</span><span class="sxs-lookup"><span data-stu-id="f8502-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f8502-108">[Poprzedni](../container-docker-introduction/docker-containers-images-registries.md)
>[następny](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="f8502-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
