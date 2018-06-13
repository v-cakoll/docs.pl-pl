---
title: Obsługa Namespace w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e91ce2b36462780925dcaef701583a966c5f59b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569454"
---
# <a name="namespace-support-in-the-dom"></a>Obsługa Namespace w modelu DOM
XML modelu DOM (Document Object) jest całkowicie przestrzeni nazw aware. Obsługiwane są tylko dokumenty obsługujących przestrzeń nazw XML. Sieci World Wide Web konsorcjum W3C Określa, czy aplikacje modelu DOM, które implementują poziomu 1 może być nie rozpoznający — przestrzeń nazw i funkcje DOM poziomu 2 rozpoznają przestrzeni nazw. Jednak są wszystkie funkcje w modelu DOM XML obsługujących przestrzeń nazw, niezależnie od tego, czy metoda jest z poziomu 1 lub poziom 2 DOM zalecenie.  
  
 Na przykład w środowisku nie rozpoznający — przestrzeń nazw wywoływania `setAttribute("A:b", "123")`, jak określono w modelu DOM poziomu 1 zalecenie, nie powoduje atrybutu z prefiksem `A` i nazwę lokalną `b`. Spowoduje to atrybut o wartości `A:b`.  
  
 W środowisku obsługujących przestrzeń nazw wywołanie DOM poziomu 2 `setAttribute("A:b", "123")` powoduje atrybutu z prefiksem `A` i nazwę lokalną `b`. Jest to, jak działa system Microsoft .NET Framework w modelu DOM.  
  
 W związku z tym dla wszystkich metod, które przyjmują parametr name, te metody także zająć prefiks nazwy. Parametr name, takich jak `A:b` w **setAttribute** metodę modelu DOM poziomu 1 jest analizowana w następujący sposób:  
  
-   Jeśli występują znaki nie dwukropka (:), a następnie ustawiono nazwę lokalną `name` parametru i prefiks i NamespaceURI są puste ciągi.  
  
-   Jeśli zostanie znaleziony dwukropek, nazwa jest podzielony na dwie części na podstawie położenia pierwszym znakiem dwukropka. Prefiks jest ustawiona na ciąg znaleziono przed dwukropkiem, a nazwa lokalna jest ustawiona na ciąg po dwukropkiem. Dla metod, które nie przyjmują wartości NamespaceURI, jego identyfikator NamespaceURI nie został rozwiązany i pozostanie ustawiony na pusty ciąg. W przeciwnym razie jego identyfikator NamespaceURI ma ustawioną wartość ciągu przekazany do metody. Jeśli zdefiniowano prefiksu, a następnie **zapisać** — metoda i **InnerXml** i **OuterXml** właściwości kończyć się niepowodzeniem.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
