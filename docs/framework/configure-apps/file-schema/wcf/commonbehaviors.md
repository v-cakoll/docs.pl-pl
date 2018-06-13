---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350325"
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="36aff-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="36aff-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="36aff-103">`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="36aff-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="36aff-104">Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="36aff-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="36aff-105">Każda kolekcja definiuje elementy zachowanie odpowiednio używane przez wszystkie punkty końcowe WCF i usług na komputerze.</span><span class="sxs-lookup"><span data-stu-id="36aff-105">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="36aff-106">Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowane w `serviceBehaviors` są stosowane tylko do usług.</span><span class="sxs-lookup"><span data-stu-id="36aff-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="36aff-107">Jeśli to zachowanie jest zdefiniowany zarówno `commonBehaviors` i `behaviors` sekcje zachowanie `behaviors` sekcji jest preferowane.</span><span class="sxs-lookup"><span data-stu-id="36aff-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
