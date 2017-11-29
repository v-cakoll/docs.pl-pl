---
title: Dynamiczne aktualizacje NodeLists i NamedNodeMaps
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamiczne aktualizacje NodeLists i NamedNodeMaps
Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawiera zestaw węzłów jeszcze dokumentu XML jest ładowany do pamięci i jest modyfikowana, sieci World Wide Web konsorcjum W3C stwierdza, że te obiekty które zawierają zestawy węzły muszą być dynamiczne. Oznacza to jeśli zmieni się dokumentu podstawowego, następnie dane w tych dwóch obiektów należy także zmienić. W związku z tym jeśli masz **XmlNodeList** zawierający wszystkie elementy podrzędne danego elementu (na przykład element X), a następnie dodaj element dodatkowy element Q, do dokumentu w elemencie X. **XmlNodeList** powinien również zawierać ten nowy element Q dodane do pobrania. To samo dotyczy odwrotnie. Jeśli węzeł zostanie dodany do **XmlNodeList**, również zostanie zaktualizowany dokumentu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
