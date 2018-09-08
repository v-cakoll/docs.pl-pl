---
title: Dynamiczna obiektów Nodelists NodeLists i NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207411"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamiczna obiektów Nodelists NodeLists i NamedNodeMaps
Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawierają zestaw węzłów, jeszcze dokument XML jest ładowany do pamięci i jest modyfikowana, World Wide Web Consortium (W3C) stwierdza, że te obiekty które zawierają zestawy węzły muszą być dynamiczne. Oznacza to jeśli zmieni się dokumentu podstawowego, następnie dane w tych dwóch obiektów należy zmieniać również. W związku z tym jeśli masz **XmlNodeList** zawierający wszystkie elementy podrzędne danego elementu (na przykład element X), a następnie dodaj element dodatkowy element Q, do dokumentu w elemencie X. **XmlNodeList** powinien również zawierać tego nowego elementu w funkcji pytania i dodać do swojej kolekcji. Dotyczy to także w odwrotnej kolejności. Jeśli węzeł zostanie dodany do **XmlNodeList**, również zostanie zaktualizowany dokumentu podstawowego.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
