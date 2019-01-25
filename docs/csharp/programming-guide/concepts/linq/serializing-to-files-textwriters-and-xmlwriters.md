---
title: Serializowanie do plików, elementów TextWriter i XmlWriters1
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 19371c0422c607171ccbea1235ea4348852d801c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498820"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="a113d-102">Serializowanie do plików, elementów TextWriter i elementów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="a113d-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="a113d-103">Może wykonywać serializację drzew XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a113d-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="a113d-104">Może wykonywać serializację dowolny składnik XML w tym <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement>, na ciąg przy użyciu `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="a113d-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="a113d-105">Jeśli chcesz pominąć formatowania podczas serializowania na ciąg, możesz użyć <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a113d-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a113d-106">Zachowanie Thedefault podczas serializacji do pliku jest formatowanie dokumentu (wcięcie) wynikowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="a113d-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="a113d-107">Możesz wciąć nieważny biały znak w drzewie XML nie zostaną zachowane.</span><span class="sxs-lookup"><span data-stu-id="a113d-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="a113d-108">Do serializacji, za pomocą formatowania, użyj jednego z przeciążeń, które z poniższych metod, które nie przyjmują <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="a113d-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a113d-109">Opcja nie twórz wcięcia i Zachowaj nieważny biały znak w drzewie XML, użyć jednego z przeciążeń z następujących metod, które przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="a113d-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a113d-110">Przykłady zobacz temat odpowiednie odwołania.</span><span class="sxs-lookup"><span data-stu-id="a113d-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a113d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a113d-111">See also</span></span>

- [<span data-ttu-id="a113d-112">Serializowanie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a113d-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
