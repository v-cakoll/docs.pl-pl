---
title: Serializowanie do plików, elementów TextWriter i elementów XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868855"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="16f8d-102">Serializowanie do plików, elementów TextWriter i elementów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="16f8d-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="16f8d-103">Można serializować drzewa XML do <xref:System.IO.File>, a <xref:System.IO.TextWriter>lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="16f8d-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="16f8d-104">Można serializować dowolny składnik XML, w tym <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement>, do ciągu przy użyciu `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="16f8d-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="16f8d-105">Jeśli chcesz pominąć formatowanie podczas serializacji do ciągu, możesz użyć <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="16f8d-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="16f8d-106">Zachowanie domyślne podczas serializowania do pliku ma format (wcięcie) otrzymany dokument XML.</span><span class="sxs-lookup"><span data-stu-id="16f8d-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="16f8d-107">W przypadku wcięcia nie jest zachowywany znaczący biały znak w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="16f8d-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="16f8d-108">Aby serializować z formatowaniem, użyj jednego z przeciążeń następujących metod, które nie przyjmują <xref:System.Xml.Linq.SaveOptions> argumentu:</span><span class="sxs-lookup"><span data-stu-id="16f8d-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="16f8d-109">Jeśli chcesz, aby opcja nie była wcięty i aby zachować nieznaczący biały znak w drzewie XML, użyj jednego z przeciążeń następujących metod, które przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument:</span><span class="sxs-lookup"><span data-stu-id="16f8d-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="16f8d-110">Przykłady znajdują się w odpowiednim temacie.</span><span class="sxs-lookup"><span data-stu-id="16f8d-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="16f8d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16f8d-111">See also</span></span>

- [<span data-ttu-id="16f8d-112">Serializowanie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="16f8d-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
