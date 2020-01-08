---
title: 'Porady: dostęp do elementów podrzędnych XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 32bdb1ba476a954bdad1f23c3ecc6129c90ccaac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347177"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="b07c4-102">Porady: dostęp do elementów podrzędnych XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b07c4-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="b07c4-103">Ten przykład pokazuje, jak używać właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych XML, które mają określoną nazwę w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="b07c4-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="b07c4-104">W szczególności używa właściwości <xref:System.Xml.Linq.XElement.Value%2A>, aby pobrać wartość pierwszego elementu w kolekcji, która zwraca `name` właściwości osi podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="b07c4-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="b07c4-105">Właściwość osi elementu podrzędnego `name` pobiera wszystkie elementy podrzędne o nazwie `phone` w obiekcie `contact`.</span><span class="sxs-lookup"><span data-stu-id="b07c4-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="b07c4-106">W tym przykładzie użyta jest również właściwość `phone` osi podrzędnej, aby uzyskać dostęp do wszystkich elementów podrzędnych o nazwach `phone` zawartych w obiekcie `contact`.</span><span class="sxs-lookup"><span data-stu-id="b07c4-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b07c4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b07c4-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="b07c4-108">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="b07c4-108">Compile the code</span></span>  
 <span data-ttu-id="b07c4-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b07c4-109">This example requires:</span></span>  
  
- <span data-ttu-id="b07c4-110">Odwołanie do przestrzeni nazw <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="b07c4-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07c4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b07c4-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b07c4-112">Właściwości osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="b07c4-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="b07c4-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="b07c4-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="b07c4-114">Uzyskiwanie dostępu do pliku XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b07c4-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="b07c4-115">XML</span><span class="sxs-lookup"><span data-stu-id="b07c4-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
