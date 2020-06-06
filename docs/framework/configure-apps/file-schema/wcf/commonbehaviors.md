---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704365"
---
# \<commonBehaviors>
<span data-ttu-id="6a126-101">`commonBehaviors`Sekcję można zdefiniować tylko w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="6a126-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="6a126-102">Definiuje dwie kolekcje podrzędne o nazwach `endpointBehaviors` i `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="6a126-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="6a126-103">Każda kolekcja definiuje elementy zachowań używane przez wszystkie punkty końcowe i usługi WCF odpowiednio na maszynie.</span><span class="sxs-lookup"><span data-stu-id="6a126-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="6a126-104">Zachowania zdefiniowane w programie `endpointBehaviors` są stosowane tylko do klientów, a zachowania zdefiniowane w programie `serviceBehaviors` są stosowane tylko do usług.</span><span class="sxs-lookup"><span data-stu-id="6a126-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="6a126-105">Jeśli zachowanie jest zdefiniowane w obu `commonBehaviors` `behaviors` sekcjach, zachowanie w `behaviors` sekcji ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="6a126-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
