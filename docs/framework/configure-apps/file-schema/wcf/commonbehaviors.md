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
ms.openlocfilehash: 06d09763b0281eb7edafadbbd59ff924b751d73e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` Sekcji można zdefiniować tylko w pliku machine.config. Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każda kolekcja definiuje używane przez wszystkie elementy zachowanie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] punktów końcowych i usług na komputerze odpowiednio. Zachowania zdefiniowane w `endpointBehaviors` są stosowane tylko do klientów i zachowania zdefiniowane w `serviceBehaviors` są stosowane tylko do usług. Jeśli to zachowanie jest zdefiniowany zarówno `commonBehaviors` i `behaviors` sekcje zachowanie `behaviors` sekcji jest preferowane.
