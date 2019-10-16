---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321174"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Wyjątek komentarza XML musi mieć atrybut „cref”

Tag \<exception > umożliwia dokumentowanie wyjątków, które mogą być zgłaszane przez metodę. Wymagany atrybut `cref` Określa nazwę elementu członkowskiego, który jest sprawdzany przez generator dokumentacji. Jeśli element członkowski istnieje, jest tłumaczony na nazwę elementu kanonicznego w pliku dokumentacji.

**Identyfikator błędu:** BC42319

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Dodaj atrybut `cref` do wyjątku w następujący sposób:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Zobacz także

- [@no__t — 1exception >](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Instrukcje: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
