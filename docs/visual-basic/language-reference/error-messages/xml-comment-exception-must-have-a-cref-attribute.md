---
title: Wyjątek komentarza XML musi mieć &#39;cref&#39; atrybutu
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: ee91513ef94e2abbe01d3ac09796b7fdf8e129ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597386"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Wyjątek komentarza XML musi mieć &#39;cref&#39; atrybutu
\<Wyjątku > tagu umożliwia dokumentu wyjątki, które może zostać zgłoszony przez metodę. Wymagane `cref` atrybut określa nazwę elementu członkowskiego, który jest sprawdzana przez generator dokumentacji. Jeśli istnieje element członkowski, są tłumaczone na nazwę kanoniczną elementu w pliku dokumentacji.  
  
 **Identyfikator błędu:** BC42319  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj `cref` atrybutu wyjątek w następujący sposób:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [\<wyjątku >](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Instrukcje: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
