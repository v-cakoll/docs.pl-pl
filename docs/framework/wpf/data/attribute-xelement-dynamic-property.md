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
# <a name="attribute-xelement-dynamic-property"></a><span data-ttu-id="9cad2-102">Atrybut (właściwość dynamiczna XElement)</span><span class="sxs-lookup"><span data-stu-id="9cad2-102">Attribute (XElement dynamic property)</span></span>

<span data-ttu-id="9cad2-103">Pobiera indeksator używany do pobierania wystąpienia atrybutu, który odpowiada określonej rozwiniętej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9cad2-103">Gets an indexer used to retrieve the attribute instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="9cad2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cad2-104">Syntax</span></span>

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="9cad2-105">Wartość właściwości/zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="9cad2-105">Property value/return value</span></span>

<span data-ttu-id="9cad2-106">Indeksator typu `XAttribute Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="9cad2-106">An indexer of the type `XAttribute Item(String expandedName)`.</span></span> <span data-ttu-id="9cad2-107">Ten indeksator przyjmuje rozwiniętą nazwę określonego atrybutu i zwraca odpowiednie <xref:System.Xml.Linq.XAttribute> lub `null`, jeśli nie ma atrybutu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9cad2-107">This indexer takes the expanded name of the specified attribute and returns the corresponding <xref:System.Xml.Linq.XAttribute>, or `null` if there is no attribute with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="9cad2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cad2-108">Remarks</span></span>

<span data-ttu-id="9cad2-109">Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XElement.Attribute%2A> klasy <xref:System.Xml.Linq.XElement?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="9cad2-109">This property is equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9cad2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cad2-110">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [<span data-ttu-id="9cad2-111">Właściwości dynamiczne klasy XElement</span><span class="sxs-lookup"><span data-stu-id="9cad2-111">XElement Class Dynamic Properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="9cad2-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="9cad2-112">Value</span></span>](value-xattribute-dynamic-property.md)
