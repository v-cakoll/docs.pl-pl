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
# <a name="commonbehaviors"></a>\<commonBehaviors>
`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config. Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każdej kolekcji definiuje zachowanie elementy używane przez wszystkie punkty końcowe WCF i usługi na maszynie, odpowiednio. Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowanego w `serviceBehaviors` są stosowane tylko do usług. Jeśli to zachowanie jest zdefiniowany w obu `commonBehaviors` i `behaviors` sekcje zachowanie w `behaviors` sekcji otrzymuje preferencji.
