---
title: 'Porady: dostęp do elementów podrzędnych XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392821"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="e4b41-102">Porady: dostęp do elementów podrzędnych XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4b41-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="e4b41-103">Ten przykład pokazuje, jak używać właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych XML, które mają określoną nazwę w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="e4b41-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="e4b41-104">W szczególności używa <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać wartość pierwszego elementu w kolekcji, która `name` zwraca właściwość osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e4b41-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="e4b41-105">`name`Właściwość oś podrzędna pobiera wszystkie elementy podrzędne o nazwie `phone` w `contact` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e4b41-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="e4b41-106">Ten przykład używa również `phone` Właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych o nazwie `phone` , które są zawarte w `contact` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e4b41-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4b41-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4b41-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="e4b41-108">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="e4b41-108">Compile the code</span></span>  
 <span data-ttu-id="e4b41-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e4b41-109">This example requires:</span></span>  
  
- <span data-ttu-id="e4b41-110">Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e4b41-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b41-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4b41-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e4b41-112">Właściwości osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="e4b41-112">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="e4b41-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="e4b41-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="e4b41-114">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4b41-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="e4b41-115">XML</span><span class="sxs-lookup"><span data-stu-id="e4b41-115">XML</span></span>](index.md)
