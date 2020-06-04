---
title: 'Porady: tworzenie dokumentacji XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 1421cc85beba42b3cf3656c34b1d02347fbaf164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403242"
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
    > Jeśli dodasz dodatkowe linie w bloku dokumentacji XML, każdy wiersz musi rozpoczynać się od `'''` .

4. Dodaj dodatkowy kod, który używa typu lub elementu członkowskiego z nowymi komentarzami dokumentacji XML.

    IntelliSense wyświetla tekst ze \<summary> znacznika dla typu lub elementu członkowskiego.

5. Skompiluj kod w celu wygenerowania pliku XML zawierającego Komentarze do dokumentacji. Aby uzyskać więcej informacji, zobacz [-doc](../../reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentowanie kodu za pomocą XML](documenting-your-code-with-xml.md)
- [Tagi komentarza XML](../../language-reference/xmldoc/index.md)
- [-doc](../../reference/command-line-compiler/doc.md)
