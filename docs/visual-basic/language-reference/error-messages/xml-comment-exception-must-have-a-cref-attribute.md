---
title: Wyjątek komentarza XML musi mieć &#39;cref&#39; atrybutu
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 0f276781165e80b2d869da2518dbe34b33085d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649950"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Wyjątek komentarza XML musi mieć &#39;cref&#39; atrybutu
\<Wyjątku > tag umożliwia dokumentowanie wyjątki, które mogą być generowane przez metodę. Wymagane `cref` atrybut określa nazwę elementu członkowskiego, która jest sprawdzana przez generator dokumentacji. Jeśli istnieje elementu członkowskiego, jest tłumaczony nazwy kanonicznej elementu w pliku dokumentacji.  
  
 **Identyfikator błędu:** BC42319  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj `cref` atrybutu wyjątku w następujący sposób:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [\<wyjątku >](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Instrukcje: Tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
