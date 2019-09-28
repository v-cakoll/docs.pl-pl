---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592041"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Wyjątek komentarza XML musi mieć atrybut „cref”
Tag \<exception > umożliwia dokumentowanie wyjątków, które mogą być zgłaszane przez metodę. Wymagany atrybut `cref` Określa nazwę elementu członkowskiego, który jest sprawdzany przez generator dokumentacji. Jeśli element członkowski istnieje, jest tłumaczony na nazwę elementu kanonicznego w pliku dokumentacji.  
  
 **Identyfikator błędu:** BC42319  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj atrybut `cref` do wyjątku w następujący sposób:  
  
    xml  
    <exception cref="member">Opis</exception> "" "  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
