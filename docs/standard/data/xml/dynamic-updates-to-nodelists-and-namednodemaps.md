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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a7abbb7344530ca993b8d07b774da17e6d0349b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamiczne aktualizacje NodeLists i NamedNodeMaps
Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawiera zestaw węzłów jeszcze dokumentu XML jest ładowany do pamięci i jest modyfikowana, sieci World Wide Web konsorcjum W3C stwierdza, że te obiekty które zawierają zestawy węzły muszą być dynamiczne. Oznacza to jeśli zmieni się dokumentu podstawowego, następnie dane w tych dwóch obiektów należy także zmienić. W związku z tym jeśli masz **XmlNodeList** zawierający wszystkie elementy podrzędne danego elementu (na przykład element X), a następnie dodaj element dodatkowy element Q, do dokumentu w elemencie X. **XmlNodeList** powinien również zawierać ten nowy element Q dodane do pobrania. To samo dotyczy odwrotnie. Jeśli węzeł zostanie dodany do **XmlNodeList**, również zostanie zaktualizowany dokumentu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
