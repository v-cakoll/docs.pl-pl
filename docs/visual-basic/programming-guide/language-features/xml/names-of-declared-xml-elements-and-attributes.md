---
title: Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2221f2677183cf360fa82a4d73a679a8b68927d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761705"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)
Ten temat zawiera wskazówki dotyczące języka Visual Basic nazewnictwa elementów XML oraz atrybuty w literałach XML.  W literał XML można określić nazwę lokalnego lub nazwą kwalifikowaną. Kwalifikowana nazwa składa się z prefiksu przestrzeni nazw XML, dwukropek i lokalna nazwa. Aby uzyskać więcej informacji na temat prefiksy przestrzeni nazw XML, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>reguły  
 Lokalna nazwa elementu lub atrybutu w języku Visual Basic muszą spełniać następujące reguły.  
  
- Można zaczyna się ona z przestrzenią nazw. Musi zaczynać się od znaku alfabetycznego lub znaku podkreślenia (`_`).  
  
- Musi zawierać tylko litery, cyfry dziesiętne, znaki podkreślenia, kropki (.) i łączniki (-).  
  
- Nie może być więcej niż 1024 znaków.  
  
- Dwukropki, które pojawiają się w nazwach wskazują odgraniczenie przestrzeni nazw. W związku z tym można użyć dwukropki tylko do określenia obszaru nazw XML dla określonej nazwy.  
  
 Ponadto należy przestrzegać następujących wytycznych.  
  
- Specyfikacja XML 1.0 zastrzega sobie wszystkie nazwy rozpoczynające się od ciągu "xml" jakiekolwiek zmiany wielkości liter. W związku z tym nie należy używać tych nazw w odniesieniu do danego elementu i nazwach atrybutów.  
  
### <a name="name-length-guidelines"></a>Wytyczne dotyczące długość nazwy  
 Jak to w praktyce nazwa powinna być możliwie krótkie podczas identyfikacji nadal wyraźnie rodzaj elementu. To zwiększa czytelność kodu i zmniejsza rozmiar wiersza długości i pliku źródłowego.  
  
 Jednak Twoja nazwa nie powinna być zbyt krótki, że nie odpowiednio opisano element lub kodzie używaniu go. Jest to ważne dla czytelności kodu. Jeśli ktoś inny spróbuje go zrozumieć lub samodzielnie przeglądasz go przez długi czas, po jego autorem, nazwy elementów odpowiednie zaoszczędzić czas.  
  
## <a name="case-sensitivity-in-names"></a>Rozróżnianie wielkości liter w nazwach  
 Nazwy elementów XML jest uwzględniana wielkość liter. Oznacza to, że gdy kompilator języka Visual Basic porównuje dwie nazwy, które różnią się alfabetycznej tylko wielkością liter, interpretuje je jako różne nazwy. Na przykład interpretuje `ABC` i `abc` jako odnoszące się do oddzielania elementów.  
  
## <a name="xml-namespaces"></a>Obszary nazw XML  
 Podczas tworzenia elementu XML literału, można określić prefiks przestrzeni nazw XML dla nazwy elementu. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
