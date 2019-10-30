---
title: Monitorowanie i kondycja
description: Monitorowanie i kondycja
ms.date: 09/23/2019
ms.openlocfilehash: 6274040318b5442478e9cc291c4f223bdf533110
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094510"
---
# <a name="monitoring-and-health"></a><span data-ttu-id="ee4b1-103">Monitorowanie i kondycja</span><span class="sxs-lookup"><span data-stu-id="ee4b1-103">Monitoring and health</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ee4b1-104">Mikrousługi i aplikacje natywne w chmurze są dostępne z dobrymi praktykami DevOps.</span><span class="sxs-lookup"><span data-stu-id="ee4b1-104">Microservices and cloud-native applications go hand in hand with good DevOps practices.</span></span> <span data-ttu-id="ee4b1-105">DevOps jest wiele rzeczy dla wielu osób, ale być może jedna z lepszych definicji pochodzi z ambasadorów w chmurze i DevOps propagator Donovan Brown:</span><span class="sxs-lookup"><span data-stu-id="ee4b1-105">DevOps is many things to many people but perhaps one of the better definitions comes from cloud advocate and DevOps evangelist Donovan Brown:</span></span>

<span data-ttu-id="ee4b1-106">"DevOps to związek ludzi, procesów i produktów, który umożliwia ciągłe dostarczanie wartości naszym użytkownikom końcowym".</span><span class="sxs-lookup"><span data-stu-id="ee4b1-106">"DevOps is the union of people, process, and products to enable continuous delivery of value to our end users."</span></span>

<span data-ttu-id="ee4b1-107">Niestety, dzięki definicjom zwięzła, zawsze możesz popowiedzieć więcej rzeczy.</span><span class="sxs-lookup"><span data-stu-id="ee4b1-107">Unfortunately, with terse definitions, there's always room to say more things.</span></span> <span data-ttu-id="ee4b1-108">Jednym z kluczowych składników DevOps jest zapewnienie, że aplikacje działające w środowisku produkcyjnym działają prawidłowo i wydajnie.</span><span class="sxs-lookup"><span data-stu-id="ee4b1-108">One of the key components of DevOps is ensuring that the applications running in production are functioning properly and efficiently.</span></span> <span data-ttu-id="ee4b1-109">Aby mierzyć kondycję aplikacji w środowisku produkcyjnym, należy monitorować różne dzienniki i metryki generowane z serwerów, hostów i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee4b1-109">To gauge the health of the application in production, it's necessary to monitor the various logs and metrics being produced from the servers, hosts, and the application proper.</span></span> <span data-ttu-id="ee4b1-110">Liczba różnych usług działających w ramach obsługi aplikacji natywnej w chmurze umożliwia monitorowanie kondycji poszczególnych składników i aplikacji jako całościowego wyzwania.</span><span class="sxs-lookup"><span data-stu-id="ee4b1-110">The number of different services running in support of a cloud-native application makes monitoring the health of individual components and the application as a whole a critical challenge.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ee4b1-111">[Poprzedni](resilient-communications.md)
>[Następny](observability-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="ee4b1-111">[Previous](resilient-communications.md)
[Next](observability-patterns.md)</span></span>
