---
title: Skalowanie aplikacji natywnych w chmurze
description: Skalowanie aplikacji natywnych w chmurze za pomocą usługi Azure Kubernetes i Azure Functions, aby zaspokoić zapotrzebowanie użytkowników w ekonomiczny sposób.
ms.date: 05/13/2020
ms.openlocfilehash: d425976eed248461a9c2e4fe03596f9f6dfd2eba
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613736"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="5247a-103">Skalowanie aplikacji natywnych w chmurze</span><span class="sxs-lookup"><span data-stu-id="5247a-103">Scaling cloud-native applications</span></span>

<span data-ttu-id="5247a-104">Jedną z najczęściej zachwalana korzyści związanych z przechodzeniem do środowiska hostingu w chmurze jest skalowalność.</span><span class="sxs-lookup"><span data-stu-id="5247a-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="5247a-105">Skalowalność lub możliwość akceptowania przez aplikację dodatkowego obciążenia użytkownika bez kompromisu wydajności dla każdego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5247a-105">Scalability, or the ability for an application to accept additional user load without compromising performance for each user.</span></span> <span data-ttu-id="5247a-106">Jest to najczęściej realizowane przez rozdzielenie aplikacji na małe fragmenty, które mogą być dostarczone przez zasoby, których wymagają.</span><span class="sxs-lookup"><span data-stu-id="5247a-106">It's most often achieved by breaking up an application into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="5247a-107">Dostawcy chmury umożliwiają ogromne skalowanie w dowolnym czasie i dowolnym miejscu na świecie.</span><span class="sxs-lookup"><span data-stu-id="5247a-107">Cloud vendors enable massive scalability anytime and anywhere in the world.</span></span>

 <span data-ttu-id="5247a-108">W tym rozdziale omówiono technologie umożliwiające skalowanie aplikacji natywnych w chmurze w celu spełnienia wymagań użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5247a-108">In this chapter, we discuss technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="5247a-109">Do tych technologii należą:</span><span class="sxs-lookup"><span data-stu-id="5247a-109">These technologies include:</span></span>

- <span data-ttu-id="5247a-110">Containers</span><span class="sxs-lookup"><span data-stu-id="5247a-110">Containers</span></span>
- <span data-ttu-id="5247a-111">Koordynatorzy</span><span class="sxs-lookup"><span data-stu-id="5247a-111">Orchestrators</span></span>
- <span data-ttu-id="5247a-112">Przetwarzanie bezserwerowe</span><span class="sxs-lookup"><span data-stu-id="5247a-112">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5247a-113">[Poprzedni](centralized-configuration.md) 
> [Dalej](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="5247a-113">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
