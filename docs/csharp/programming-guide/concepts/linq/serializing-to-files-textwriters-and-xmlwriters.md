---
title: Serializacja do plików, TextWriters i XmlWriters1
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 903e6f5b6a8cd88c140e6759136301a6305cee2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330213"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="a3514-102">Serializacja do plików, TextWriters i XmlWriters</span><span class="sxs-lookup"><span data-stu-id="a3514-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="a3514-103">Może wykonywać serializację drzew XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a3514-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="a3514-104">Może wykonywać serializację jakiegokolwiek składnika XML w tym <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement>, ciąg przy użyciu `ToString` — metoda.</span><span class="sxs-lookup"><span data-stu-id="a3514-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="a3514-105">Jeśli chcesz pominąć formatowania podczas serializowania na ciąg, możesz użyć <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a3514-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a3514-106">Thedefault zachowanie podczas serializowania do pliku ma format dokumentu (wcięcie) wynikowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="a3514-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="a3514-107">Gdy wcięcie, nieważny biały znak w drzewie XML nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="a3514-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="a3514-108">Do serializacji z formatowaniem, użyj jednej z przeciążeń następujących metod, które nie przyjmują <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="a3514-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a3514-109">Opcja nie wcięcie i Zachowaj nieważny biały znak w drzewie XML, użyć jednego z przeciążeń z następujących metod, które przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="a3514-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a3514-110">Przykłady zobacz temat odpowiednie informacje.</span><span class="sxs-lookup"><span data-stu-id="a3514-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3514-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3514-111">See Also</span></span>  
 [<span data-ttu-id="a3514-112">Serializacja XML drzew (C#)</span><span class="sxs-lookup"><span data-stu-id="a3514-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
