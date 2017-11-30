---
title: 'Porady: tworzenie dokumentacji XML w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [/ doc](../../../visual-basic/reference/command-line-compiler/doc.md)
