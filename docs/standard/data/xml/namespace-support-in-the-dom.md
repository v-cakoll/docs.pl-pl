---
title: Obsługa przestrzeni nazw w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a468d1a2b15d1f92726d8d429fbc5ddece96e6d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647866"
---
# <a name="namespace-support-in-the-dom"></a>Obsługa przestrzeni nazw w modelu DOM
XML Document Object Model (DOM) jest całkowicie przestrzeni nazw aware. Obsługiwane są tylko pamiętać nazw dokumentów XML. World Wide Web Consortium (W3C) określa, że aplikacje w modelu DOM, które implementują poziomu 1 może być przestrzeni nazw nieobsługującą i funkcje na poziomie 2 modelu DOM są obsługujących przestrzeń nazw. Jednak wszystkie funkcje w modelu DOM języka XML są obsługujących przestrzeń nazw, niezależnie od tego, jeśli metoda jest z poziomu 1 lub na poziomie 2 modelu DOM zalecenia.  
  
 Na przykład w przestrzeni nazw nieobsługującą ustawienie wywoływania `setAttribute("A:b", "123")`, jak to określono w modelu DOM na poziomie 1 zalecenia, nie powoduje atrybutu z prefiksem `A` i lokalna nazwa elementu `b`. Spowoduje to atrybutu o wartości `A:b`.  
  
 W środowisku obsługujących przestrzeń nazw wywołania na poziomie 2 modelu DOM `setAttribute("A:b", "123")` skutkuje atrybutu z prefiksem `A` i lokalna nazwa elementu `b`. Jest to, jak działa program Microsoft .NET Framework w modelu DOM.  
  
 W związku z tym dla wszystkich metod, które przyjmują parametr name, te metody także przyjmują Zakwalifikuj nazwę przez określenie prefiksu. Parametr name, takich jak `A:b` w **setAttribute** metodę modelu DOM poziomu 1 jest analizowana w następujący sposób:  
  
- Jeśli występują znaki nie dwukropka (:), a następnie nazwę lokalnego jest równa `name` parametru i prefiksu i jego identyfikator NamespaceURI to puste ciągi.  
  
- Jeśli zostanie znaleziony dwukropek, nazwę zostanie podzielona na dwie części na podstawie pozycji pierwszy znak dwukropka. Prefiks jest ustawiona na ciąg znaków znalezionych przed dwukropkiem i lokalna nazwa jest równa string znaleźć po dwukropku. Dla metody, które nie przyjmują wartości jego identyfikator NamespaceURI, jego identyfikator NamespaceURI nie został rozwiązany i pozostanie ustawiony na pusty ciąg. W przeciwnym razie jego identyfikator NamespaceURI ustawiono ciąg przekazywany do metody. Jeśli prefiks jest niezdefiniowana, a następnie **Zapisz** metody i **InnerXml** i **OuterXml** właściwości kończyć się niepowodzeniem.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
