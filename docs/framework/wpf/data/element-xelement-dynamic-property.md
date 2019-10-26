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
# <a name="element-xelement-dynamic-property"></a><span data-ttu-id="4bc58-102">Element (właściwość dynamiczna XElement)</span><span class="sxs-lookup"><span data-stu-id="4bc58-102">Element (XElement dynamic property)</span></span>

<span data-ttu-id="4bc58-103">Pobiera indeksator używany do pobrania wystąpienia elementu podrzędnego, który odnosi się do określonej rozwiniętej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4bc58-103">Gets an indexer used to retrieve the child element instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bc58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bc58-104">Syntax</span></span>

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="4bc58-105">Wartość właściwości/zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="4bc58-105">Property value/return value</span></span>

<span data-ttu-id="4bc58-106">Indeksator typu `XElement Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="4bc58-106">An indexer of the type `XElement Item(String expandedName)`.</span></span> <span data-ttu-id="4bc58-107">Ten indeksator przyjmuje rozszerzony parametr name i zwraca odpowiednie <xref:System.Xml.Linq.XElement> lub `null`, jeśli nie ma elementu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4bc58-107">This indexer takes an expanded name parameter and returns the corresponding <xref:System.Xml.Linq.XElement>, or `null` if there is no element with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bc58-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bc58-108">Remarks</span></span>

<span data-ttu-id="4bc58-109">Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Element%2A> metodzie klasy <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="4bc58-109">This property is equivalent to <xref:System.Xml.Linq.XContainer.Element%2A> method of the <xref:System.Xml.Linq.XContainer?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bc58-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bc58-110">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [<span data-ttu-id="4bc58-111">Właściwości dynamiczne klasy XElement</span><span class="sxs-lookup"><span data-stu-id="4bc58-111">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="4bc58-112">Elements</span><span class="sxs-lookup"><span data-stu-id="4bc58-112">Elements</span></span>](elements-xelement-dynamic-property.md)
