---
title: 'Porady: Przekształcanie fragmentu węzła'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd35e469a16dc2fdb3a7f4afd89d04f67185cd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568566"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="ca72f-102">Porady: Przekształcanie fragmentu węzła</span><span class="sxs-lookup"><span data-stu-id="ca72f-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="ca72f-103">Gdy przekształcenie danych zawartych w <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> obiektów przekształceń XSLT stosowane do całego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ca72f-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="ca72f-104">Innymi słowy w przypadku przekazania w węźle innym niż węzeł główny dokumentu, to nie zapobiega proces przekształcania podczas uzyskiwania dostępu do wszystkich węzłów w załadowanego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ca72f-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="ca72f-105">Aby przekształcić fragmentu węzła, należy utworzyć oddzielny obiekt zawierający tylko fragmentu węzeł i przekazać do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ca72f-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ca72f-106">Procedury</span><span class="sxs-lookup"><span data-stu-id="ca72f-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="ca72f-107">Aby przekształcić fragmentu węzła</span><span class="sxs-lookup"><span data-stu-id="ca72f-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="ca72f-108">Utwórz obiekt zawierający dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="ca72f-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="ca72f-109">Zlokalizuj fragmentu węzła, który ma zostać transformacji.</span><span class="sxs-lookup"><span data-stu-id="ca72f-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="ca72f-110">Należy utworzyć oddzielny obiekt z właśnie fragmentu węzła.</span><span class="sxs-lookup"><span data-stu-id="ca72f-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="ca72f-111">Fragment węzła do przekazania <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ca72f-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca72f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca72f-112">Example</span></span>  
 <span data-ttu-id="ca72f-113">W poniższym przykładzie przekształca fragmentu węzła i umieszcza wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="ca72f-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="ca72f-114">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="ca72f-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="ca72f-115">Books.XML</span><span class="sxs-lookup"><span data-stu-id="ca72f-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="ca72f-116">Single.xsl</span><span class="sxs-lookup"><span data-stu-id="ca72f-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="ca72f-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ca72f-117">Output</span></span>  
 <span data-ttu-id="ca72f-118">Tytuł książki jest Man. zaufania</span><span class="sxs-lookup"><span data-stu-id="ca72f-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca72f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca72f-119">See Also</span></span>  
 [<span data-ttu-id="ca72f-120">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="ca72f-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
