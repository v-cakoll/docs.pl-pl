---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268763"
---
# <a name="commonbehaviors"></a>\<commonBehaviors>
`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config. Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każdej kolekcji definiuje zachowanie elementy używane przez wszystkie punkty końcowe WCF i usługi na maszynie, odpowiednio. Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowanego w `serviceBehaviors` są stosowane tylko do usług. Jeśli to zachowanie jest zdefiniowany w obu `commonBehaviors` i `behaviors` sekcje zachowanie w `behaviors` sekcji otrzymuje preferencji.
