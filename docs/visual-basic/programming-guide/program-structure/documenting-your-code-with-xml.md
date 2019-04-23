---
title: Dokumentowanie kodu za pomocą XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 6b9fe9994b7bdf2259dcdb1ecef906e0f9955c8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480628"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Dokumentowanie kodu za pomocą XML (Visual Basic)

W języku Visual Basic można udokumentować kod za pomocą języka XML

## <a name="xml-documentation-comments"></a>Komentarze dokumentacji XML

Zapewnia prosty sposób automatycznego tworzenia dokumentacji XML dla projektów w Visual Basic. Automatycznie Generuj szkielet XML dla typów i elementów członkowskich i następnie podaj podsumowania, dokumentacja opisową dla każdego parametru i inne uwagi. W przypadku odpowiedniej konfiguracji dokumentacji XML są automatycznie emitowane do pliku XML z taką samą nazwę jak projekt i rozszerzenie .xml. Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).

Plik XML można używane lub w przeciwnym razie modyfikowane jako XML. Ten plik znajduje się w tym samym katalogu co plik .exe lub .dll danych wyjściowych projektu.

Dokumentacja XML, który rozpoczyna się od `'''`. Przetwarzanie te komentarze mają pewne ograniczenia:

- Dokumentacja musi być poprawnie sformułowany XML. Jeśli plik XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji zawiera komentarz informujący o tym, że wystąpił błąd podczas.

- Deweloperzy są bezpłatne tworzenie własnych zestawów tagów. Jest zalecany zestaw znaczników (patrz "Sekcje pokrewne" w tym temacie). Niektóre zalecane tagi mają specjalne znaczenie:

  - \<Param > tag jest używany do opisania parametrów. Jeśli używane, kompilator sprawdzi, czy parametr istnieje i czy wszystkie parametry są opisane w dokumentacji. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.

  - `cref` Atrybutu mogą być dołączane do każdego znacznika, aby zapewnić odwołanie do elementu kodu. Kompilator sprawdza, czy ten element kodu istnieje. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie. Kompilator również stosuje się do dowolnej `Imports` instrukcji podczas wyszukiwania dla typu z opisem w temacie `cref` atrybutu.

  - \<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać szczegółowe informacje na temat tworzenia pliku XML z komentarzami dokumentacji zobacz następujące tematy:

- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

- [Przetwarzanie pliku XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Instrukcje: Tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Narzędzia XML w Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji za pomocą języka Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
