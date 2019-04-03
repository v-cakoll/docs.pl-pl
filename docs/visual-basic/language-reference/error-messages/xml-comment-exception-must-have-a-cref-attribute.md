---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a974df5d2305b88946981d0d258a8088b23d3fc3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813291"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Wyjątek komentarza XML musi mieć atrybut „cref”
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
