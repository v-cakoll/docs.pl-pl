---
title: Dynamiczne aktualizacje NodeLists i NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1de133d0208f1b86ad3240cdc00d8016af0a160c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamiczne aktualizacje NodeLists i NamedNodeMaps
Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawiera zestaw węzłów jeszcze dokumentu XML jest ładowany do pamięci i jest modyfikowana, sieci World Wide Web konsorcjum W3C stwierdza, że te obiekty które zawierają zestawy węzły muszą być dynamiczne. Oznacza to jeśli zmieni się dokumentu podstawowego, następnie dane w tych dwóch obiektów należy także zmienić. W związku z tym jeśli masz **XmlNodeList** zawierający wszystkie elementy podrzędne danego elementu (na przykład element X), a następnie dodaj element dodatkowy element Q, do dokumentu w elemencie X. **XmlNodeList** powinien również zawierać ten nowy element Q dodane do pobrania. To samo dotyczy odwrotnie. Jeśli węzeł zostanie dodany do **XmlNodeList**, również zostanie zaktualizowany dokumentu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
