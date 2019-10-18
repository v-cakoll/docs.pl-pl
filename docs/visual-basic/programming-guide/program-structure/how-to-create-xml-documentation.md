---
title: 'Porady: tworzenie dokumentacji XML w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 5b317706e3e8e0c5958f5a3d0fd859d68600bc7a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524489"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Porady: tworzenie dokumentacji XML w Visual Basic

Ten przykład pokazuje, jak dodać komentarze dokumentacji XML do kodu.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Aby utworzyć dokumentację XML dla typu lub elementu członkowskiego

1. W **edytorze kodu**Umieść kursor w wierszu powyżej typu lub elementu członkowskiego, dla którego chcesz utworzyć dokumentację.

2. Wpisz `'''` (trzy znaki pojedynczego cudzysłowu).

    Szkielet XML dla typu lub elementu członkowskiego jest dodawany w **edytorze kodu**.

3. Dodaj opisowe informacje między odpowiednimi tagami.

    > [!NOTE]
    > Jeśli dodasz dodatkowe linie w bloku dokumentacji XML, każdy wiersz musi rozpoczynać się od `'''`.

4. Dodaj dodatkowy kod, który używa typu lub elementu członkowskiego z nowymi komentarzami dokumentacji XML.

    Funkcja IntelliSense wyświetla tekst ze znacznika > \<summary dla typu lub elementu członkowskiego.

5. Skompiluj kod w celu wygenerowania pliku XML zawierającego Komentarze do dokumentacji. Aby uzyskać więcej informacji, zobacz [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
