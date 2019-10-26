---
title: Element (właściwość dynamiczna XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.openlocfilehash: fc0277d0dc38574696f01e6915e5382744345771
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920896"
---
# <a name="element-xelement-dynamic-property"></a>Element (właściwość dynamiczna XElement)

Pobiera indeksator używany do pobrania wystąpienia elementu podrzędnego, który odnosi się do określonej rozwiniętej nazwy.

## <a name="syntax"></a>Składnia

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

Indeksator typu `XElement Item(String expandedName)`. Ten indeksator przyjmuje rozszerzony parametr name i zwraca odpowiednie <xref:System.Xml.Linq.XElement> lub `null`, jeśli nie ma elementu o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Element%2A> metodzie klasy <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](attribute-xelement-dynamic-property.md)
- [Elements](elements-xelement-dynamic-property.md)
