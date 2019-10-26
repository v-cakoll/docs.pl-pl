---
title: Atrybut (właściwość dynamiczna XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 2b645575a5b6876ffbb52a999c4e05a2de037493
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920917"
---
# <a name="attribute-xelement-dynamic-property"></a>Atrybut (właściwość dynamiczna XElement)

Pobiera indeksator używany do pobierania wystąpienia atrybutu, który odpowiada określonej rozwiniętej nazwie.

## <a name="syntax"></a>Składnia

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

Indeksator typu `XAttribute Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę określonego atrybutu i zwraca odpowiednie <xref:System.Xml.Linq.XAttribute> lub `null`, jeśli nie ma atrybutu o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XElement.Attribute%2A> klasy <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](attribute-xelement-dynamic-property.md)
- [Wartość](value-xattribute-dynamic-property.md)
