---
title: "Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)
Ten temat zawiera [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zasady nazewnictwa elementów XML oraz atrybuty w literałach XML.  W literał XML można określić nazwę lokalną lub kwalifikowanej nazwy. Kwalifikowana nazwa składa się z prefiksu przestrzeni nazw XML, dwukropek i nazwa lokalna. Aby uzyskać więcej informacji na temat prefiksy przestrzeni nazw XML, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Reguły  
 Lokalna nazwa elementu lub atrybutu w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] muszą być zgodne z następującymi zasadami.  
  
-   Może ona rozpoczynać przestrzeni nazw. Musi zaczynać się od litery lub znaku podkreślenia (`_`).  
  
-   Musi zawierać tylko znaki alfabetyczne, cyfry dziesiętne, znaki podkreślenia, kropki (.) i łączniki (-).  
  
-   Nie może być więcej niż 1024 znaków.  
  
-   Dwukropki, które pojawiają się w nazwach wskazują odgraniczenie przestrzeni nazw. W związku z tym umożliwia dwukropki tylko określić przestrzeń nazw XML dla określonej nazwy.  
  
 Ponadto należy przestrzegać następujących wytycznych.  
  
-   Specyfikacja XML 1.0 zastrzega sobie wszystkie nazwy zaczynającym się od ciągu "xml" jakiekolwiek zmiany wielkości liter. W związku z tym nie należy używać tych nazw dla danego elementu i nazwach atrybutów.  
  
### <a name="name-length-guidelines"></a>Wskazówki dotyczące długość nazwy  
 Jak to w praktyce nazwa powinna być możliwie krótki podczas nadal jednoznacznie identyfikujący rodzaj elementu. To poprawia czytelność kodu i zmniejsza rozmiar linii długość i pliku źródłowego.  
  
 Nazwa nie należy jednak tak krótki, że nie można ją było właściwie opisano element lub kodu używaniu go. Jest to ważne w przypadku czytelność kodu. Jeśli ktoś próbuje go zrozumieć, lub jeśli chcesz samodzielnie go przez długi czas, po jego zapisano, nazwy odpowiednich elementów zaoszczędzić czas.  
  
## <a name="case-sensitivity-in-names"></a>Uwzględniana wielkość liter w nazwach  
 Nazwy elementów XML jest uwzględniana wielkość liter. Oznacza to, że w przypadku [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora porównuje dwie nazwy, które różnią się alfabetycznej tylko wielkością liter, jego interpretuje je jako różne nazwy. Na przykład interpretuje `ABC` i `abc` jako odnoszące się do oddzielania elementów.  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Podczas tworzenia literał elementu XML, można określić prefiks przestrzeni nazw XML dla nazwy elementu. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
