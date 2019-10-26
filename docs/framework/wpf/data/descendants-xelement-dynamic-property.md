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
# <a name="descendants-xelement-dynamic-property"></a><span data-ttu-id="54e50-102">Elementy podrzędne (właściwość dynamiczna XElement)</span><span class="sxs-lookup"><span data-stu-id="54e50-102">Descendants (XElement dynamic property)</span></span>

<span data-ttu-id="54e50-103">Pobiera indeksator używany do pobierania wszystkich elementów podrzędnych bieżącego elementu, który jest zgodny z określoną rozwiniętą nazwą.</span><span class="sxs-lookup"><span data-stu-id="54e50-103">Gets an indexer used to retrieve all the descendant elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="54e50-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54e50-104">Syntax</span></span>

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="54e50-105">Wartość właściwości/zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="54e50-105">Property value/return value</span></span>

<span data-ttu-id="54e50-106">Indeksator typu `IEnumerable<XElement> Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="54e50-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="54e50-107">Ten indeksator przyjmuje rozwiniętą nazwę określonych elementów potomnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="54e50-107">This indexer takes the expanded name of the specified descendant elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="54e50-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54e50-108">Remarks</span></span>

<span data-ttu-id="54e50-109">Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> klasy <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="54e50-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="54e50-110">Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu źródłowego XML.</span><span class="sxs-lookup"><span data-stu-id="54e50-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="54e50-111">Ta właściwość używa wykonania odroczonego.</span><span class="sxs-lookup"><span data-stu-id="54e50-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="54e50-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54e50-112">See also</span></span>

- [<span data-ttu-id="54e50-113">Właściwości dynamiczne klasy XElement</span><span class="sxs-lookup"><span data-stu-id="54e50-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="54e50-114">Elements</span><span class="sxs-lookup"><span data-stu-id="54e50-114">Elements</span></span>](elements-xelement-dynamic-property.md)
