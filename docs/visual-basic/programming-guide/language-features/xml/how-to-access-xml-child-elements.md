---
title: 'Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 874c7490e451d64bf50e25934ea43a9b928ddab9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980558"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="2f455-102">Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f455-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="2f455-103">W tym przykładzie pokazano, jak używać elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, które mają określoną nazwą w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="2f455-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="2f455-104">W szczególności używa <xref:System.Xml.Linq.XElement.Value%2A> właściwość, aby pobrać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2f455-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="2f455-105">`name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy podrzędne, o nazwie `phone` w `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2f455-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="2f455-106">W tym przykładzie również użyto `phone` właściwości osi elementu podrzędnego na dostęp do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2f455-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f455-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f455-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f455-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2f455-108">Compiling the Code</span></span>  
 <span data-ttu-id="2f455-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2f455-109">This example requires:</span></span>  
  
-   <span data-ttu-id="2f455-110">Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2f455-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f455-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f455-111">See also</span></span>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2f455-112">Właściwości osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="2f455-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="2f455-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="2f455-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="2f455-114">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f455-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="2f455-115">XML</span><span class="sxs-lookup"><span data-stu-id="2f455-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
