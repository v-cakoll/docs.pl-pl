---
title: Elementy podrzędne (właściwość dynamiczna XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 8d14b0a94d1a2028a56f649a574f157264ba50fa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920889"
---
# <a name="descendants-xelement-dynamic-property"></a>Elementy podrzędne (właściwość dynamiczna XElement)

Pobiera indeksator używany do pobierania wszystkich elementów podrzędnych bieżącego elementu, który jest zgodny z określoną rozwiniętą nazwą.

## <a name="syntax"></a>Składnia

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę określonych elementów potomnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> klasy <xref:System.Xml.Linq.XContainer>.

Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu źródłowego XML.

Ta właściwość używa wykonania odroczonego.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](attribute-xelement-dynamic-property.md)
- [Elements](elements-xelement-dynamic-property.md)
