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
`commonBehaviors`Sekcję można zdefiniować tylko w pliku Machine. config. Definiuje dwie kolekcje podrzędne o nazwach `endpointBehaviors` i `serviceBehaviors` .  Każda kolekcja definiuje elementy zachowań używane przez wszystkie punkty końcowe i usługi WCF odpowiednio na maszynie. Zachowania zdefiniowane w programie `endpointBehaviors` są stosowane tylko do klientów, a zachowania zdefiniowane w programie `serviceBehaviors` są stosowane tylko do usług. Jeśli zachowanie jest zdefiniowane w obu `commonBehaviors` `behaviors` sekcjach, zachowanie w `behaviors` sekcji ma pierwszeństwo.
