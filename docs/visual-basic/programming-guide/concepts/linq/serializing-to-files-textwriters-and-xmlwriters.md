---
title: Serializowanie do plików, elementów TextWriter i XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: 63577d955da89fde0a2320b4cf84414ccbb69c84
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675306"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="571f0-102">Serializowanie do plików, elementów TextWriter i elementów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="571f0-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="571f0-103">Może wykonywać serializację drzew XML do <xref:System.IO.File>, <xref:System.IO.TextWriter>, lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="571f0-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="571f0-104">Może wykonywać serializację dowolny składnik XML w tym <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement>, na ciąg przy użyciu `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="571f0-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="571f0-105">Jeśli chcesz pominąć formatowania podczas serializowania na ciąg, możesz użyć <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="571f0-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="571f0-106">Domyślnym zachowaniem podczas serializacji do pliku jest formatowanie dokumentu (wcięcie) wynikowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="571f0-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="571f0-107">Możesz wciąć nieważny biały znak w drzewie XML nie zostaną zachowane.</span><span class="sxs-lookup"><span data-stu-id="571f0-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="571f0-108">Do serializacji, za pomocą formatowania, użyj jednego z przeciążeń, które z poniższych metod, które nie przyjmują <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="571f0-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="571f0-109">Opcja nie twórz wcięcia i Zachowaj nieważny biały znak w drzewie XML, użyć jednego z przeciążeń z następujących metod, które przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="571f0-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="571f0-110">Przykłady zobacz temat odpowiednie odwołania.</span><span class="sxs-lookup"><span data-stu-id="571f0-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="571f0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="571f0-111">See also</span></span>

- [<span data-ttu-id="571f0-112">Serializowanie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="571f0-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
