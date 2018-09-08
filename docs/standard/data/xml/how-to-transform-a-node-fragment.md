---
title: 'Instrukcje: Przekształcanie fragmentu węzła'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb258b61664e1fdbf6604afdf69074c48cf5bda4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135003"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="8296d-102">Instrukcje: Przekształcanie fragmentu węzła</span><span class="sxs-lookup"><span data-stu-id="8296d-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="8296d-103">Kiedy przekształcasz dane zawarte w <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> obiektu przekształcenia XSLT dotyczą dokumentu jako całości.</span><span class="sxs-lookup"><span data-stu-id="8296d-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="8296d-104">Innymi słowy Jeśli przekażesz w węźle innym niż węzeł główny dokument, to nie uniemożliwia proces przekształcania uzyskiwania dostępu do wszystkich węzłów w dokumencie załadowane.</span><span class="sxs-lookup"><span data-stu-id="8296d-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="8296d-105">Aby Przekształcanie fragmentu węzła, należy utworzyć oddzielny obiekt zawierający tylko fragmentu węzła i przekazać ten obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8296d-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8296d-106">Procedury</span><span class="sxs-lookup"><span data-stu-id="8296d-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="8296d-107">Aby Przekształcanie fragmentu węzła</span><span class="sxs-lookup"><span data-stu-id="8296d-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="8296d-108">Utwórz obiekt zawierający dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="8296d-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="8296d-109">Znajdź fragment węzeł, który chcesz przekształcić.</span><span class="sxs-lookup"><span data-stu-id="8296d-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="8296d-110">Utwórz oddzielne obiekty z tylko fragmentu węzła.</span><span class="sxs-lookup"><span data-stu-id="8296d-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="8296d-111">Przekazywanie fragmentu węzła do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8296d-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8296d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8296d-112">Example</span></span>  
 <span data-ttu-id="8296d-113">W poniższym przykładzie przekształca fragmentu węzła i generuje wyjściowe wyniki do konsoli.</span><span class="sxs-lookup"><span data-stu-id="8296d-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="8296d-114">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="8296d-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="8296d-115">Books.XML</span><span class="sxs-lookup"><span data-stu-id="8296d-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="8296d-116">Single.xsl</span><span class="sxs-lookup"><span data-stu-id="8296d-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="8296d-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8296d-117">Output</span></span>  
 <span data-ttu-id="8296d-118">Tytuł książki jest Man. ufności</span><span class="sxs-lookup"><span data-stu-id="8296d-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8296d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8296d-119">See also</span></span>

- [<span data-ttu-id="8296d-120">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="8296d-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
