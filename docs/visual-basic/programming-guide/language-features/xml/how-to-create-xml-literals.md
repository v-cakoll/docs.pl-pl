---
title: 'Porady: tworzenie literałów XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 61b138c0851c747ed30eedc10cb882cc3b03c4d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392613"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="e250c-102">Porady: tworzenie literałów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e250c-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="e250c-103">Można utworzyć dokument XML, fragment lub element bezpośrednio w kodzie przy użyciu literału XML.</span><span class="sxs-lookup"><span data-stu-id="e250c-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="e250c-104">W przykładach w tym temacie pokazano, jak utworzyć element XML z trzema elementami podrzędnymi i jak utworzyć dokument XML.</span><span class="sxs-lookup"><span data-stu-id="e250c-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="e250c-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Do tworzenia obiektów można także używać interfejsów API [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e250c-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="e250c-106">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e250c-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="e250c-107">Aby utworzyć element XML</span><span class="sxs-lookup"><span data-stu-id="e250c-107">To create an XML element</span></span>  
  
- <span data-ttu-id="e250c-108">Utwórz kod XML w tekście przy użyciu składni literału XML, która jest taka sama jak rzeczywista składnia XML.</span><span class="sxs-lookup"><span data-stu-id="e250c-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="e250c-109">Uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="e250c-109">Run the code.</span></span> <span data-ttu-id="e250c-110">Dane wyjściowe tego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="e250c-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="e250c-111">Aby utworzyć dokument XML</span><span class="sxs-lookup"><span data-stu-id="e250c-111">To create an XML document</span></span>  
  
- <span data-ttu-id="e250c-112">Utwórz wiersz dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e250c-112">Create the XML document inline.</span></span> <span data-ttu-id="e250c-113">Poniższy kod tworzy dokument XML, który ma składnię literału, deklarację XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.</span><span class="sxs-lookup"><span data-stu-id="e250c-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="e250c-114">Uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="e250c-114">Run the code.</span></span> <span data-ttu-id="e250c-115">Dane wyjściowe tego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="e250c-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="e250c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e250c-116">See also</span></span>

- [<span data-ttu-id="e250c-117">XML</span><span class="sxs-lookup"><span data-stu-id="e250c-117">XML</span></span>](index.md)
- [<span data-ttu-id="e250c-118">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e250c-118">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="e250c-119">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="e250c-119">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="e250c-120">Literał dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="e250c-120">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
