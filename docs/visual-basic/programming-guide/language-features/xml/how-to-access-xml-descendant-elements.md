---
title: 'Instrukcje: Dostęp do elementów podrzędnych XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: bfbf849bd296f639f03580346e4a9c52ce000abd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832219"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="dacb3-102">Instrukcje: Dostęp do elementów podrzędnych XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dacb3-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="dacb3-103">W tym przykładzie pokazano, jak dostęp do wszystkich elementów XML, które mają określoną nazwą i znajdujących się w obszarze elementu XML przy użyciu właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="dacb3-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="dacb3-104">W szczególności używa `Value` właściwość, aby pobrać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="dacb3-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="dacb3-105">`name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy o nazwie `name` są zawarte w `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="dacb3-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="dacb3-106">W tym przykładzie również użyto `phone` właściwości osi elementu podrzędnego do dostępu do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contacts` obiektu.</span><span class="sxs-lookup"><span data-stu-id="dacb3-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dacb3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="dacb3-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dacb3-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="dacb3-108">Compiling the Code</span></span>  
 <span data-ttu-id="dacb3-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="dacb3-109">This example requires:</span></span>  
  
-   <span data-ttu-id="dacb3-110">Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dacb3-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dacb3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dacb3-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dacb3-112">Właściwości osi obiektu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="dacb3-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="dacb3-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="dacb3-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="dacb3-114">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dacb3-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="dacb3-115">XML</span><span class="sxs-lookup"><span data-stu-id="dacb3-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
