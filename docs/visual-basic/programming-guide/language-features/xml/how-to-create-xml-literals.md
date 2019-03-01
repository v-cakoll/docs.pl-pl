---
title: 'Instrukcje: Tworzenie literałów XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: c79b607f9ce5c779539b7700feafb7d4e3d67d24
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974253"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="2a757-102">Instrukcje: Tworzenie literałów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a757-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="2a757-103">Można utworzyć dokumentu XML, fragment lub element bezpośrednio w kodzie za pomocą literał XML.</span><span class="sxs-lookup"><span data-stu-id="2a757-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="2a757-104">Przykłady w tym temacie pokazują, jak utworzyć element XML, który ma trzy elementy podrzędne i tworzenie dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2a757-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="2a757-105">Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="2a757-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="2a757-106">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2a757-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="2a757-107">Aby utworzyć XML element</span><span class="sxs-lookup"><span data-stu-id="2a757-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="2a757-108">Utwórz w tekście XML przy użyciu składni literał XML, która jest taka sama jak rzeczywista składni XML.</span><span class="sxs-lookup"><span data-stu-id="2a757-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="2a757-109">Uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="2a757-109">Run the code.</span></span> <span data-ttu-id="2a757-110">Wynik tego kodu jest:</span><span class="sxs-lookup"><span data-stu-id="2a757-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="2a757-111">Aby utworzyć dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2a757-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="2a757-112">Utwórz w tekście dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2a757-112">Create the XML document inline.</span></span> <span data-ttu-id="2a757-113">Poniższy kod tworzy dokument XML, który ma składni literału, deklaracja XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="2a757-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="2a757-114">Uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="2a757-114">Run the code.</span></span> <span data-ttu-id="2a757-115">Wynik tego kodu jest:</span><span class="sxs-lookup"><span data-stu-id="2a757-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="2a757-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a757-116">See also</span></span>
- [<span data-ttu-id="2a757-117">XML</span><span class="sxs-lookup"><span data-stu-id="2a757-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="2a757-118">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a757-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2a757-119">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="2a757-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="2a757-120">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2a757-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
