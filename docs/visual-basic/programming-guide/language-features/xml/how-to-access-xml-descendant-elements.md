---
title: 'Porady: dostęp do elementów podrzędnych XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 03c403aa3c187b0b9d2006104eccaa1f9cd8aec5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392639"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="693e2-102">Porady: dostęp do elementów podrzędnych XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="693e2-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="693e2-103">Ten przykład pokazuje, jak używać właściwości osi elementu podrzędnego w celu uzyskania dostępu do wszystkich elementów XML, które mają określoną nazwę i które są zawarte w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="693e2-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="693e2-104">W szczególności używa `Value` właściwości, aby pobrać wartość pierwszego elementu w kolekcji, która `name` zwraca właściwość osi elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="693e2-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="693e2-105">`name`Właściwość osi elementu podrzędnego pobiera wszystkie elementy o nazwie `name` , które są zawarte w `contacts` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="693e2-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="693e2-106">W tym przykładzie jest również stosowana `phone` Właściwość osi elementu podrzędnego, aby uzyskać dostęp do wszystkich elementów podrzędnych o nazwie `phone` , które są zawarte w `contacts` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="693e2-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="693e2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="693e2-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="693e2-108">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="693e2-108">Compile the code</span></span>  
 <span data-ttu-id="693e2-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="693e2-109">This example requires:</span></span>  
  
- <span data-ttu-id="693e2-110">Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="693e2-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693e2-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="693e2-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="693e2-112">Właściwości osi obiektu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="693e2-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="693e2-113">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="693e2-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="693e2-114">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="693e2-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="693e2-115">XML</span><span class="sxs-lookup"><span data-stu-id="693e2-115">XML</span></span>](index.md)
