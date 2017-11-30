---
title: "Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 572e34b1cd4813fad35e6afaf2ec3d0d9dac470a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="a8393-102">Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8393-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="a8393-103">Można utworzyć [literałów XML](../../../../visual-basic/language-reference/xml-literals/index.md) i wypełnić je przy użyciu zawartości ze źródła zewnętrznego, takich jak pliku, ciągu lub strumienia za pomocą kilku metod.</span><span class="sxs-lookup"><span data-stu-id="a8393-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="a8393-104">W poniższych przykładach przedstawiono tych metod.</span><span class="sxs-lookup"><span data-stu-id="a8393-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="a8393-105">Aby załadować z pliku XML</span><span class="sxs-lookup"><span data-stu-id="a8393-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="a8393-106">Aby wypełnić literału, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z pliku, użyj `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="a8393-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="a8393-107">Ta metoda może zająć ścieżka do pliku, strumienia tekstu lub strumień XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a8393-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="a8393-108">W poniższym przykładzie pokazano sposób użycia <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu XML z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="a8393-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="a8393-109">Ładowanie XML z ciągu</span><span class="sxs-lookup"><span data-stu-id="a8393-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="a8393-110">Aby wypełnić literału, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z ciągu, można użyć `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="a8393-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="a8393-111">W poniższym przykładzie pokazano sposób użycia <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="a8393-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="a8393-112">Aby załadować XML ze strumienia</span><span class="sxs-lookup"><span data-stu-id="a8393-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="a8393-113">Aby wypełnić literału, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu strumienia, można użyć `Load` — metoda lub <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> — metoda.</span><span class="sxs-lookup"><span data-stu-id="a8393-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a8393-114">W poniższym przykładzie pokazano sposób użycia <xref:System.Xml.Linq.XNode.ReadFrom%2A> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu XML ze strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="a8393-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a8393-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8393-115">See Also</span></span>  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a8393-116">Literały XML</span><span class="sxs-lookup"><span data-stu-id="a8393-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="a8393-117">XML</span><span class="sxs-lookup"><span data-stu-id="a8393-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="a8393-118">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8393-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
