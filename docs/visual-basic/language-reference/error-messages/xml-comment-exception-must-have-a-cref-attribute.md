---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406511"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Wyjątek komentarza XML musi mieć atrybut „cref”

\<exception>Tag umożliwia dokumentowanie wyjątków, które mogą być zgłaszane przez metodę. Wymagany `cref` atrybut określa nazwę elementu członkowskiego, który jest sprawdzany przez generator dokumentacji. Jeśli element członkowski istnieje, jest tłumaczony na nazwę elementu kanonicznego w pliku dokumentacji.

**Identyfikator błędu:** BC42319

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Dodaj `cref` atrybut do wyjątku w następujący sposób:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Zobacz też

- [\<exception>](../xmldoc/exception.md)
- [Instrukcje: tworzenie dokumentacji XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Tagi komentarza XML](../xmldoc/index.md)
