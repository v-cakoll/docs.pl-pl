---
title: 'Instrukcje: Tworzenie literałów XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 0e74dccac0b3528fe73d091670a3368328baeaab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560597"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="aec8a-102">Instrukcje: Tworzenie literałów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec8a-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="aec8a-103">Można utworzyć dokumentu XML, fragment lub element bezpośrednio w kodzie za pomocą literał XML.</span><span class="sxs-lookup"><span data-stu-id="aec8a-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="aec8a-104">Przykłady w tym temacie pokazują, jak utworzyć element XML, który ma trzy elementy podrzędne i tworzenie dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="aec8a-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="aec8a-105">Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="aec8a-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="aec8a-106">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="aec8a-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="aec8a-107">Aby utworzyć XML element</span><span class="sxs-lookup"><span data-stu-id="aec8a-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="aec8a-108">Utwórz w tekście XML przy użyciu składni literał XML, która jest taka sama jak rzeczywista składni XML.</span><span class="sxs-lookup"><span data-stu-id="aec8a-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="aec8a-109">Uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="aec8a-109">Run the code.</span></span> <span data-ttu-id="aec8a-110">Wynik tego kodu jest:</span><span class="sxs-lookup"><span data-stu-id="aec8a-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="aec8a-111">Aby utworzyć dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="aec8a-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="aec8a-112">Utwórz w tekście dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="aec8a-112">Create the XML document inline.</span></span> <span data-ttu-id="aec8a-113">Poniższy kod tworzy dokument XML, który ma składni literału, deklaracja XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="aec8a-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="aec8a-114">Uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="aec8a-114">Run the code.</span></span> <span data-ttu-id="aec8a-115">Wynik tego kodu jest:</span><span class="sxs-lookup"><span data-stu-id="aec8a-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="aec8a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aec8a-116">See also</span></span>
- [<span data-ttu-id="aec8a-117">XML</span><span class="sxs-lookup"><span data-stu-id="aec8a-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="aec8a-118">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aec8a-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="aec8a-119">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="aec8a-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="aec8a-120">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="aec8a-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
