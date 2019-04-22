---
title: 'Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: cd1b0db5305c7879d89cfdfff6cd458d6dea14f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836821"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="3a5be-102">Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a5be-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="3a5be-103">W tym przykładzie pokazano, jak używać elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, które mają określoną nazwą w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="3a5be-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="3a5be-104">W szczególności używa <xref:System.Xml.Linq.XElement.Value%2A> właściwość, aby pobrać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="3a5be-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="3a5be-105">`name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy podrzędne, o nazwie `phone` w `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a5be-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="3a5be-106">W tym przykładzie również użyto `phone` właściwości osi elementu podrzędnego na dostęp do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a5be-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a5be-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a5be-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3a5be-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3a5be-108">Compiling the Code</span></span>  
 <span data-ttu-id="3a5be-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3a5be-109">This example requires:</span></span>  
  
-   <span data-ttu-id="3a5be-110">Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3a5be-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5be-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a5be-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3a5be-112">Właściwości osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="3a5be-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="3a5be-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="3a5be-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="3a5be-114">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a5be-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="3a5be-115">XML</span><span class="sxs-lookup"><span data-stu-id="3a5be-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
