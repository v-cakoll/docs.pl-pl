---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: aaf89f73b6de250aaa572b8fef31e5a1ebd5482b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="26526-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="26526-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="26526-103">`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="26526-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="26526-104">Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="26526-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="26526-105">Każda kolekcja definiuje używane przez wszystkie elementy zachowanie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] punktów końcowych i usług na komputerze odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="26526-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="26526-106">Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowane w `serviceBehaviors` są stosowane tylko do usług.</span><span class="sxs-lookup"><span data-stu-id="26526-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="26526-107">Jeśli to zachowanie jest zdefiniowany zarówno `commonBehaviors` i `behaviors` sekcje zachowanie `behaviors` sekcji jest preferowane.</span><span class="sxs-lookup"><span data-stu-id="26526-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
