---
title: 'Porady: dostęp do elementów podrzędnych XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347157"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="2632f-102">Porady: dostęp do elementów podrzędnych XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2632f-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="2632f-103">Ten przykład pokazuje, jak używać właściwości osi elementu podrzędnego w celu uzyskania dostępu do wszystkich elementów XML, które mają określoną nazwę i które są zawarte w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="2632f-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="2632f-104">W szczególności używa właściwości `Value`, aby pobrać wartość pierwszego elementu w kolekcji, która zwraca `name` Właściwość osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2632f-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="2632f-105">Właściwość osi elementu podrzędnego `name` pobiera wszystkie elementy o nazwie `name`, które są zawarte w obiekcie `contacts`.</span><span class="sxs-lookup"><span data-stu-id="2632f-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="2632f-106">W tym przykładzie używane jest również `phone` Właściwość osi elementu podrzędnego, aby uzyskać dostęp do wszystkich elementów podrzędnych o nazwach `phone` zawartych w obiekcie `contacts`.</span><span class="sxs-lookup"><span data-stu-id="2632f-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2632f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2632f-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="2632f-108">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="2632f-108">Compile the code</span></span>  
 <span data-ttu-id="2632f-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2632f-109">This example requires:</span></span>  
  
- <span data-ttu-id="2632f-110">Odwołanie do przestrzeni nazw <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="2632f-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2632f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2632f-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2632f-112">Właściwości osi obiektu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="2632f-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="2632f-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="2632f-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="2632f-114">Uzyskiwanie dostępu do pliku XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2632f-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="2632f-115">XML</span><span class="sxs-lookup"><span data-stu-id="2632f-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
