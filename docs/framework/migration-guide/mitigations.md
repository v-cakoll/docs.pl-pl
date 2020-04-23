---
title: Ograniczanie nowych zachowań w ramach platformy .NET Framework
ms.date: 04/21/2020
ms.openlocfilehash: bd0843ea21a0ff68c6f02b1351f66544dbb200bf
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103542"
---
# <a name="mitigate-new-behaviors-in-net-framework-46-and-later"></a><span data-ttu-id="4ef40-102">Ograniczanie nowych zachowań w programach .NET Framework 4.6 i nowszych</span><span class="sxs-lookup"><span data-stu-id="4ef40-102">Mitigate new behaviors in .NET Framework 4.6 and later</span></span>

<span data-ttu-id="4ef40-103">Ta sekcja zawiera artykuły, które opisują środki zaradcze dla zachowań, które zostały wprowadzone w .NET Framework 4.6 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="4ef40-103">This section contains articles that describe mitigations for behaviors that were introduced in .NET Framework 4.6 and later.</span></span>

<span data-ttu-id="4ef40-104">Należy rozważyć złagodzenie nowego zachowania, jeśli powoduje problemy dla aplikacji lub jest w inny sposób niepożądane.</span><span class="sxs-lookup"><span data-stu-id="4ef40-104">Consider mitigating a new behavior if it causes problems for your app or is otherwise undesirable.</span></span> <span data-ttu-id="4ef40-105">W niektórych przypadkach można również *włączyć* nowe zachowanie w aplikacjach, które są przeznaczone dla starszej wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.6 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="4ef40-105">In some cases, you can also *enable* a new behavior on apps that target an older version of .NET Framework but are running on .NET Framework 4.6 or later.</span></span>
