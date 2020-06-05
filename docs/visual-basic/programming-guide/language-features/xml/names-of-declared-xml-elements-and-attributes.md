---
title: Nazwy deklarowanych elementów XML oraz atrybuty
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 043243eeee7c24d8c63105047fa3e7e0ed58c7b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374671"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)
Ten temat zawiera Visual Basic wskazówki dotyczące nazewnictwa elementów i atrybutów XML w literałach XML.  W literale XML można określić nazwę lokalną lub kwalifikowaną nazwę. Kwalifikowana nazwa składa się z prefiksu przestrzeni nazw XML, dwukropka i nazwy lokalnej. Aby uzyskać więcej informacji na temat prefiksów przestrzeni nazw XML, zobacz [literał elementu XML](../../../language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Reguły  
 Lokalna nazwa elementu lub atrybutu w Visual Basic musi być zgodna z poniższymi regułami.  
  
- Może zaczynać się od przestrzeni nazw. Musi zaczynać się od litery lub znaku podkreślenia ( `_` ).  
  
- Musi zawierać tylko litery alfabetu, cyfry dziesiętne, podkreślenia, kropki (.) i łączniki (-).  
  
- Nie może być dłuższa niż 1 024 znaków.  
  
- Dwukropek, które pojawiają się w nazwach, wskazują na rozgraniczenie przestrzeni nazw. W związku z tym, można użyć dwukropka, aby określić przestrzeń nazw XML dla określonej nazwy.  
  
 Ponadto należy przestrzegać następujących wytycznych.  
  
- Specyfikacja XML 1,0 rezerwuje wszystkie nazwy zaczynające się od ciągu "XML" dowolnej zmiany wielkości liter. W związku z tym nie należy używać tych nazw dla nazw elementów i atrybutów.  
  
### <a name="name-length-guidelines"></a>Wskazówki dotyczące długości nazwy  
 Jako praktyczna nazwa powinna być tak krótka, jak to możliwe, podczas gdy nadal jednoznacznie identyfikuje charakter elementu. Poprawia to czytelność kodu i zmniejsza długość wiersza i rozmiar pliku źródłowego.  
  
 Jednak Twoja nazwa nie powinna być tak krótka, aby nie była odpowiednio opisywana elementu lub jak kod używa go. Jest to ważne dla czytelności kodu. Jeśli ktoś inny próbuje zrozumieć ten element, lub jeśli ty zobaczysz swoją godzinę po jej zapisaniu, odpowiednie nazwy elementów mogą zaoszczędzić czas.  
  
## <a name="case-sensitivity-in-names"></a>Rozróżnianie wielkości liter w nazwach  
 W nazwach elementów XML jest rozróżniana wielkość liter. Oznacza to, że kiedy kompilator Visual Basic porównuje dwie nazwy, które różnią się tylko wielkością liter, interpretuje je jako różne nazwy. Na przykład interpretuje i w odniesieniu `ABC` `abc` do oddzielnych elementów.  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Podczas tworzenia literału elementu XML, można określić prefiks przestrzeni nazw XML dla nazwy elementu. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie XML w Visual Basic](creating-xml.md)
- [Literał elementu XML](../../../language-reference/xml-literals/xml-element-literal.md)
