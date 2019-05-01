---
title: Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934475"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps
Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawierają zestaw węzłów, jeszcze dokument XML jest ładowany do pamięci i jest modyfikowana, World Wide Web Consortium (W3C) stwierdza, że te obiekty które zawierają zestawy węzły muszą być dynamiczne. Oznacza to jeśli zmieni się dokumentu podstawowego, następnie dane w tych dwóch obiektów należy zmieniać również. W związku z tym jeśli masz **XmlNodeList** zawierający wszystkie elementy podrzędne danego elementu (na przykład element X), a następnie dodaj element dodatkowy element Q, do dokumentu w elemencie X. **XmlNodeList** powinien również zawierać tego nowego elementu w funkcji pytania i dodać do swojej kolekcji. Dotyczy to także w odwrotnej kolejności. Jeśli węzeł zostanie dodany do **XmlNodeList**, również zostanie zaktualizowany dokumentu podstawowego.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
