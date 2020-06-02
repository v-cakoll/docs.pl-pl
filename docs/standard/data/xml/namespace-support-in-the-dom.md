---
title: Obsługa przestrzeni nazw w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
ms.openlocfilehash: 6fefce961c2ff91530a9110f5563fd921a7838a3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288800"
---
# <a name="namespace-support-in-the-dom"></a>Obsługa przestrzeni nazw w modelu DOM
Document Object Model XML (DOM) jest całkowicie oparty na przestrzeni nazw. Obsługiwane są tylko dokumenty XML obsługujące przestrzeń nazw. Organizacja World Wide Web Consortium (W3C) określa, że aplikacje DOM, które implementują poziom 1 mogą być niezgodne z przestrzenią nazw, a funkcje poziomu DOM 2 są oparte na przestrzeni nazw. Jednak wszystkie funkcje w modelu XML DOM są oparte na przestrzeni nazw, niezależnie od tego, czy metoda pochodzi z rekomendacji DOM poziomu 1 lub 2.  
  
 Na przykład w przypadku ustawienia typu "niezależne od przestrzeni nazw" wywoływanie `setAttribute("A:b", "123")` , zgodnie z zaleceniami poziomu dom 1 nie powoduje, że atrybut z prefiksem `A` i nazwą lokalną `b` . Spowodowałoby to powstanie atrybutu z wartością `A:b` .  
  
 W środowisku obsługującym przestrzeń nazw wywołanie do poziomu DOM 2 `setAttribute("A:b", "123")` powoduje wystąpienie atrybutu z prefiksem `A` i nazwą lokalną `b` . Jest to sposób działania Microsoft .NET Framework w modelu DOM.  
  
 W związku z tym w przypadku wszystkich metod przyjmujących parametr name te metody również przyjmują prefiks, aby zakwalifikować nazwę. Parametr name, taki jak `A:b` w metodzie **SetAttribute** dom Level 1, jest analizowany w następujący sposób:  
  
- Jeśli nie ma dwukropka (:) znaki, a następnie nazwa lokalna jest ustawiana na `name` parametr, a prefiks i NamespaceURI są pustymi ciągami.  
  
- Jeśli zostanie znaleziony dwukropek, nazwa zostanie podzielona na dwie części na podstawie pozycji pierwszego dwukropka. Prefiks jest ustawiany na ciąg znaleziony przed dwukropkiem, a lokalna nazwa jest ustawiona na ciąg znaleziony po dwukropku. Dla metod, które nie przyjmują wartości NamespaceURI, NamespaceURI nie jest rozpoznawane i pozostaje ustawiony jako pusty ciąg. W przeciwnym razie NamespaceURI jest ustawiony na ciąg przesłany do metody. Jeśli prefiks jest niezdefiniowany, wówczas właściwości **Save** i **InnerXml** oraz **OuterXml** będą kończyć się niepowodzeniem.  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
