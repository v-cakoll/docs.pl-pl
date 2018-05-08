---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config. Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każda kolekcja definiuje elementy zachowanie odpowiednio używane przez wszystkie punkty końcowe WCF i usług na komputerze. Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowane w `serviceBehaviors` są stosowane tylko do usług. Jeśli to zachowanie jest zdefiniowany zarówno `commonBehaviors` i `behaviors` sekcje zachowanie `behaviors` sekcji jest preferowane.
