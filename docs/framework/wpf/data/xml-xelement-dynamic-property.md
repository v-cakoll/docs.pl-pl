---
title: Xml (właściwość dynamiczna XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Xml
ms.openlocfilehash: 9bac9797f397a0bea1dda36bf864f88293061893
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920721"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (właściwość dynamiczna XElement)

Pobiera niesformatowaną zawartość XML elementu.

## <a name="syntax"></a>Składnia

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

<xref:System.String>, która reprezentuje niesformatowaną zawartość XML elementu.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna metodzie <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> klasy <xref:System.Xml.Linq.XNode?displayProperty=fullName> z parametrem `SaveOptions` ustawionym na <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](attribute-xelement-dynamic-property.md)
- [Wartość](value-xelement-dynamic-property.md)
