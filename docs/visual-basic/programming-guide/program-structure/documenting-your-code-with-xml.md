---
title: Dokumentowanie kodu za pomocą XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347442"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Dokumentowanie kodu za pomocą XML (Visual Basic)

W Visual Basic można udokumentować kod za pomocą XML

## <a name="xml-documentation-comments"></a>Komentarze dokumentacji XML

Visual Basic zapewnia łatwy sposób automatycznego tworzenia dokumentacji XML dla projektów. Można automatycznie wygenerować szkielet XML dla typów i składowych, a następnie podać podsumowania, opisową dokumentację dla każdego parametru oraz inne uwagi. Po wybraniu odpowiedniej konfiguracji dokumentacja XML jest automatycznie emitowana do pliku XML o takiej samej nazwie jak nazwa projektu i rozszerzenie. XML. Aby uzyskać więcej informacji, zobacz [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

Plik XML można wykorzystać lub w inny sposób manipulować jako XML. Ten plik znajduje się w tym samym katalogu, w którym znajduje się plik Output. exe lub. dll projektu.

Dokumentacja XML rozpoczyna się od `'''`. Przetwarzanie tych komentarzy ma pewne ograniczenia:

- Dokumentacja musi być poprawnie sformułowanym plikiem XML. Jeśli kod XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji zawiera komentarz informujący o wystąpieniu błędu.

- Deweloperzy mogą bezpłatnie tworzyć własne zestawy tagów. Istnieje zalecany zestaw tagów (zobacz sekcję "sekcje pokrewne" w tym temacie). Niektóre z zalecanych tagów mają specjalne znaczenie:

  - Tag \<param > służy do opisywania parametrów. Jeśli jest używany, kompilator sprawdzi, czy parametr istnieje i że wszystkie parametry zostały opisane w dokumentacji. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.

  - Atrybut `cref` może być dołączany do dowolnego tagu w celu udostępnienia odwołania do elementu kodu. Kompilator sprawdza, czy ten element kodu istnieje. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie. Kompilator uwzględnia również wszystkie instrukcje `Imports` podczas wyszukiwania typu opisanego w atrybucie `cref`.

  - Tag \<Summary > jest używany przez funkcję IntelliSense w programie Visual Studio do wyświetlania dodatkowych informacji na temat typu lub elementu członkowskiego.

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać szczegółowe informacje na temat tworzenia pliku XML z komentarzami dokumentacji, zobacz następujące tematy:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

- [Przetwarzanie pliku XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Instrukcje: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Narzędzia XML w Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji za pomocą Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Przewodnik programowania Visual Basic](../../../visual-basic/programming-guide/index.md)
