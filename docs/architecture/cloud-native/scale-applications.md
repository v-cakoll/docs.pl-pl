---
title: Skalowanie aplikacji natywnych w chmurze
description: Skalowanie aplikacji natywnych w chmurze za pomocą usługi Azure Kubernetes i Azure Functions, aby zaspokoić zapotrzebowanie użytkowników w ekonomiczny sposób.
ms.date: 09/23/2019
ms.openlocfilehash: 5f4aac5804c5498c331787083c943a6ea1b69748
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184828"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="3b781-103">Skalowanie aplikacji natywnych w chmurze</span><span class="sxs-lookup"><span data-stu-id="3b781-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3b781-104">Jedną z najczęściej zachwalana korzyści związanych z przechodzeniem do środowiska hostingu w chmurze jest skalowalność.</span><span class="sxs-lookup"><span data-stu-id="3b781-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="3b781-105">Skalowalność lub możliwość zaakceptowania przez aplikację dodatkowych obciążeń użytkowników bez nieuzasadnionego obniżenia wydajności dla każdego użytkownika, jest najczęściej realizowana przez rozdzielenie aplikacji na małe fragmenty, które mogą zostać przekazane do zasobów, których wymagają.</span><span class="sxs-lookup"><span data-stu-id="3b781-105">Scalability, or the ability for an application to accept additional user load without unduly degrading performance for each user, is most often achieved by breaking up applications into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="3b781-106">W tym rozdziale wprowadzimy technologie umożliwiające skalowanie aplikacji natywnych w chmurze w celu spełnienia wymagań użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3b781-106">In this chapter, we introduce the technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="3b781-107">Te technologie obejmują:</span><span class="sxs-lookup"><span data-stu-id="3b781-107">These technologies include:</span></span>

- <span data-ttu-id="3b781-108">Kontenery</span><span class="sxs-lookup"><span data-stu-id="3b781-108">Containers</span></span>
- <span data-ttu-id="3b781-109">Koordynatorów</span><span class="sxs-lookup"><span data-stu-id="3b781-109">Orchestrators</span></span>
- <span data-ttu-id="3b781-110">Obliczanie bezserwerowe</span><span class="sxs-lookup"><span data-stu-id="3b781-110">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3b781-111">[Poprzedni](centralized-configuration.md)
>[Następny](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="3b781-111">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
