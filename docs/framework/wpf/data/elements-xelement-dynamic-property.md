---
title: Elementy (właściwość dynamiczna XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.openlocfilehash: 812adabd3bfb01fd9313ce3f35e6cb0a5e23344e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920854"
---
# <a name="elements-xelement-dynamic-property"></a><span data-ttu-id="43ffc-102">Elementy (właściwość dynamiczna XElement)</span><span class="sxs-lookup"><span data-stu-id="43ffc-102">Elements (XElement dynamic property)</span></span>

<span data-ttu-id="43ffc-103">Pobiera indeksator używany do pobierania elementów podrzędnych bieżącego elementu, który jest zgodny z określoną rozwiniętą nazwą.</span><span class="sxs-lookup"><span data-stu-id="43ffc-103">Gets an indexer used to retrieve the child elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="43ffc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43ffc-104">Syntax</span></span>

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="43ffc-105">Wartość właściwości/zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="43ffc-105">Property value/return value</span></span>

<span data-ttu-id="43ffc-106">Indeksator typu `IEnumerable<XElement> Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="43ffc-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="43ffc-107">Ten indeksator przyjmuje rozwiniętą nazwę żądanych elementów podrzędnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="43ffc-107">This indexer takes the expanded name of the desired child elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="43ffc-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43ffc-108">Remarks</span></span>

<span data-ttu-id="43ffc-109">Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> klasy <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="43ffc-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="43ffc-110">Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu źródłowego XML.</span><span class="sxs-lookup"><span data-stu-id="43ffc-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="43ffc-111">Ta właściwość używa wykonania odroczonego.</span><span class="sxs-lookup"><span data-stu-id="43ffc-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="43ffc-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43ffc-112">See also</span></span>

- [<span data-ttu-id="43ffc-113">Właściwości dynamiczne klasy XElement</span><span class="sxs-lookup"><span data-stu-id="43ffc-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="43ffc-114">Element</span><span class="sxs-lookup"><span data-stu-id="43ffc-114">Element</span></span>](element-xelement-dynamic-property.md)
- [<span data-ttu-id="43ffc-115">Elementy potomne</span><span class="sxs-lookup"><span data-stu-id="43ffc-115">Descendants</span></span>](descendants-xelement-dynamic-property.md)
