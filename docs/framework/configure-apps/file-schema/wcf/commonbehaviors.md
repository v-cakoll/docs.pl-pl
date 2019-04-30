---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704365"
---
# <a name="commonbehaviors"></a><span data-ttu-id="9f9ec-101">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="9f9ec-101">\<commonBehaviors></span></span>
<span data-ttu-id="9f9ec-102">`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="9f9ec-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="9f9ec-103">Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="9f9ec-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="9f9ec-104">Każdej kolekcji definiuje zachowanie elementy używane przez wszystkie punkty końcowe WCF i usługi na maszynie, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9f9ec-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="9f9ec-105">Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowanego w `serviceBehaviors` są stosowane tylko do usług.</span><span class="sxs-lookup"><span data-stu-id="9f9ec-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="9f9ec-106">Jeśli to zachowanie jest zdefiniowany w obu `commonBehaviors` i `behaviors` sekcje zachowanie w `behaviors` sekcji otrzymuje preferencji.</span><span class="sxs-lookup"><span data-stu-id="9f9ec-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
