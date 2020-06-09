---
title: Dokumentowanie kodu za pomocą XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590932"
---
# <a name="document-your-code-with-xml-visual-basic"></a>Dokumentowanie kodu za pomocą XML (Visual Basic)

W Visual Basic można udokumentować kod przy użyciu XML.

## <a name="xml-documentation-comments"></a>Komentarze dokumentacji XML

Visual Basic zapewnia łatwy sposób automatycznego tworzenia dokumentacji XML dla projektów. Można automatycznie wygenerować szkielet XML dla typów i składowych, a następnie podać podsumowania, opisową dokumentację dla każdego parametru oraz inne uwagi. Przy użyciu odpowiedniej konfiguracji dokumentacja XML jest automatycznie emitowana do pliku XML o tej samej nazwie pliku głównego co projekt. Aby uzyskać więcej informacji, zobacz [-doc](../../reference/command-line-compiler/doc.md).

Plik XML można wykorzystać lub w inny sposób manipulować jako XML. Ten plik znajduje się w tym samym katalogu, w którym znajduje się plik Output. exe lub. dll projektu.

Dokumentacja XML zaczyna się od `'''` . Przetwarzanie tych komentarzy ma pewne ograniczenia:

- Dokumentacja musi być poprawnie sformułowanym plikiem XML. Jeśli kod XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji zawiera komentarz informujący o wystąpieniu błędu.

- Deweloperzy mogą bezpłatnie tworzyć własne zestawy tagów. Istnieje zalecany zestaw tagów (zobacz [Tagi komentarza XML](../../language-reference/xmldoc/index.md)). Niektóre z zalecanych tagów mają specjalne znaczenie:

  - \<param>Tag jest używany do opisywania parametrów. Jeśli jest używany, kompilator sprawdzi, czy parametr istnieje i że wszystkie parametry zostały opisane w dokumentacji. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.

  - Ten `cref` atrybut może być dołączany do dowolnego tagu w celu zapewnienia odwołania do elementu kodu. Kompilator sprawdza, czy ten element kodu istnieje. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie. Kompilator uwzględnia również wszelkie `Imports` instrukcje podczas wyszukiwania typu opisanego w `cref` atrybucie.

  - \<summary>Tag jest używany przez funkcję IntelliSense w programie Visual Studio do wyświetlania dodatkowych informacji na temat typu lub elementu członkowskiego.

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać szczegółowe informacje na temat tworzenia pliku XML z komentarzami dokumentacji, zobacz następujące tematy:

- [-doc](../../reference/command-line-compiler/doc.md)

- [Tagi komentarza XML](../../language-reference/xmldoc/index.md)

- [Przetwarzanie pliku XML](processing-the-xml-file.md)

- [Instrukcje: tworzenie dokumentacji XML](how-to-create-xml-documentation.md)

- [Narzędzia XML w programie Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Zobacz też

- [Tworzenie aplikacji za pomocą Visual Basic](../../developing-apps/index.md)
- [Przewodnik programowania w Visual Basic](../index.md)
