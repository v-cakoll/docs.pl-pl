---
title: Serializowanie do plików, elementów TextWriter i elementów XmlWriter
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868855"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="5f198-102">Serializowanie do plików, elementów TextWriter i elementów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="5f198-102">Serializing to Files, TextWriters, and XmlWriters</span></span>

<span data-ttu-id="5f198-103">Drzewa XML można serializować <xref:System.IO.File>na <xref:System.IO.TextWriter>, a <xref:System.Xml.XmlWriter>, lub .</span><span class="sxs-lookup"><span data-stu-id="5f198-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="5f198-104">Za pomocą <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` tej metody można serializować dowolny składnik XML, w tym i , ciąg.</span><span class="sxs-lookup"><span data-stu-id="5f198-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="5f198-105">Jeśli chcesz pominąć formatowanie podczas serializacji do ciągu, <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> można użyć tej metody.</span><span class="sxs-lookup"><span data-stu-id="5f198-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5f198-106">Domyślnym zachowaniem podczas serializacji do pliku jest sformatowanie (wcięcia) wynikowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5f198-106">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="5f198-107">Po wcięciu nieznaczne odstępy w drzewie XML nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="5f198-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="5f198-108">Aby serializować za pomocą formatowania, należy użyć jednej z przeciążeń <xref:System.Xml.Linq.SaveOptions> następujących metod, które nie są przyjmowane jako argument:</span><span class="sxs-lookup"><span data-stu-id="5f198-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="5f198-109">Jeśli opcja nie wcinać i zachować nieznaczne odstępy w drzewie XML, należy użyć jednej <xref:System.Xml.Linq.SaveOptions> z przeciążeń następujących metod, które przyjmuje jako argument:</span><span class="sxs-lookup"><span data-stu-id="5f198-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="5f198-110">Na przykład zobacz odpowiedni temat odwołania.</span><span class="sxs-lookup"><span data-stu-id="5f198-110">For examples, see the appropriate reference topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f198-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f198-111">See also</span></span>

- [<span data-ttu-id="5f198-112">Serializujące drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5f198-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
