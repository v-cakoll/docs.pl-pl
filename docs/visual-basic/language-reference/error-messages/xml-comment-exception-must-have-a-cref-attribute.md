---
title: "Wyjątek komentarza XML musi mieć &#39; cref &#39; atrybut"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Wyjątek komentarza XML musi mieć &#39; cref &#39; atrybut
\<Wyjątku > tagu umożliwia dokumentu wyjątki, które może zostać zgłoszony przez metodę. Wymagane `cref` atrybut określa nazwę elementu członkowskiego, który jest sprawdzana przez generator dokumentacji. Jeśli istnieje element członkowski, są tłumaczone na nazwę kanoniczną elementu w pliku dokumentacji.  
  
 **Identyfikator błędu:** BC42319  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj `cref` atrybutu wyjątek w następujący sposób:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [\<wyjątku >](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Porady: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
