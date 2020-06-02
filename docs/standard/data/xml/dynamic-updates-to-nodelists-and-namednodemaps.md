---
title: Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 0199f24e9ef8dd28f91976edd50f78399dc893ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292088"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps
Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawierają zestaw węzłów, a dokument XML jest ładowany do pamięci i jest modyfikowany, organizacja World Wide Web Consortium (W3C) stwierdza, że te obiekty, które zawierają zestawy węzłów, muszą być dynamiczne. Oznacza to, że jeśli dokument źródłowy ulegnie zmianie, dane w tych dwóch obiektach powinny być również zmienione. W związku z tym, jeśli masz element **XmlNodeList** , który zawiera wszystkie elementy podrzędne określonego elementu (na przykład element x), następnie Dodaj dodatkowy element, element Q do dokumentu w obszarze element x. **XmlNodeList** powinien również mieć dodany nowy element Q do swojej kolekcji. Ta sama wartość dotyczy odwrócenia. Jeśli węzeł zostanie dodany do **XmlNodeList**, dokument źródłowy również zostanie zaktualizowany.  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
