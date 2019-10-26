---
title: Wartość (właściwość dynamiczna XAttribute)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.openlocfilehash: 32c15a89a976b5f9af12f040c43e724a25357ead
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920651"
---
# <a name="value-xattribute-dynamic-property"></a>Wartość (właściwość dynamiczna XAttribute)

Pobiera lub ustawia wartość atrybutu XML.

## <a name="syntax"></a>Składnia

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

<xref:System.String> zawierający wartość tego atrybutu.

## <a name="exceptions"></a>Wyjątki

|Typ wyjątku|Warunek|
| - |---------------|
|<xref:System.ArgumentNullException>|Ustawienie `value` jest `null`.|

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna z właściwością <xref:System.Xml.Linq.XAttribute.Value%2A> klasy <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ale ta właściwość dynamiczna obsługuje również powiadomienia o zmianach.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XAttribute](value-xattribute-dynamic-property.md)
- [Atrybut](attribute-xelement-dynamic-property.md)
