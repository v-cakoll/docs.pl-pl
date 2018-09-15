---
title: Wybieranie między .NET Core i .NET Framework dla kontenerów Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Wybieranie między .NET Core i .NET Framework dla kontenerów Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 9abff2614e4022408a069be25440196111db19ab
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638863"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="ceb5c-103">Wybieranie między .NET Core i .NET Framework dla kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="ceb5c-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="ceb5c-104">Dostępne są dwie obsługiwane platformy dla tworzenia po stronie serwera aplikacji platformy Docker z platformą .NET kontenerowych nimi: [.NET Framework i .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="ceb5c-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="ceb5c-105">Współużytkują one wiele składników platformy .NET i mogą współużytkować kod między nimi.</span><span class="sxs-lookup"><span data-stu-id="ceb5c-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="ceb5c-106">Istnieją jednak podstawowe różnice między nimi i framework, której użyjesz zależy od co chcesz osiągnąć.</span><span class="sxs-lookup"><span data-stu-id="ceb5c-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="ceb5c-107">Ta sekcja zawiera wskazówki dotyczące kiedy należy wybrać każdego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ceb5c-107">This section provides guidance on when to choose each framework.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ceb5c-108">[Poprzednie](../container-docker-introduction/docker-containers-images-registries.md)
[dalej](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="ceb5c-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
