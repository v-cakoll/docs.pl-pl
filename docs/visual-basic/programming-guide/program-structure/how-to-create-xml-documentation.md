---
title: 'Porady: tworzenie dokumentacji XML w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 7fb56da8a28367a6dcd5e28f208b4519510d7d95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650884"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Porady: tworzenie dokumentacji XML w Visual Basic
W tym przykładzie przedstawiono sposób dodawania komentarzy dokumentacji XML w kodzie.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Aby utworzyć plik dokumentacji XML dla typu lub elementu członkowskiego  
  
1.  W **edytora kodu**, umieść kursor w wierszu powyżej typu lub elementu członkowskiego, dla którego chcesz utworzyć dokumentacji.  
  
2.  Typ `'''` (trzy znaków pojedynczego cudzysłowu).  
  
     Szkielet XML dla typu lub elementu członkowskiego został dodany w **edytora kodu**.  
  
3.  Dodaj informacje opisowe między odpowiednich tagów.  
  
    > [!NOTE]
    >  Jeśli dodasz dodatkowe wiersze w bloku dokumentacji XML, każdy wiersz musi rozpoczynać się od `'''`.  
  
4.  Dodaj dodatkowy kod, który używa typu lub elementu członkowskiego o nowe komentarze dokumentacji XML.  
  
     Funkcja IntelliSense wyświetla tekst z \<podsumowania > tag dla typu lub elementu członkowskiego.  
  
5.  Należy skompilować kod aby wygenerować plik XML zawierający komentarze dokumentacji. Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
