---
title: '&lt;commonBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b39942cc438201ceaecf1fee62ce3fefdc27b68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="bb25e-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="bb25e-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="bb25e-103">`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="bb25e-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="bb25e-104">Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="bb25e-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="bb25e-105">Każda kolekcja definiuje używane przez wszystkie elementy zachowanie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] punktów końcowych i usług na komputerze odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="bb25e-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="bb25e-106">Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowane w `serviceBehaviors` są stosowane tylko do usług.</span><span class="sxs-lookup"><span data-stu-id="bb25e-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="bb25e-107">Jeśli to zachowanie jest zdefiniowany zarówno `commonBehaviors` i `behaviors` sekcje zachowanie `behaviors` sekcji jest preferowane.</span><span class="sxs-lookup"><span data-stu-id="bb25e-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
