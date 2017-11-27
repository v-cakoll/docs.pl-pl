---
title: "Zachowywanie biały znak podczas Serializing3"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: df0ee9bedd4123ac47c06d1c64f305fcf0b0825a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="61f74-102">Zachowywanie białe miejsce podczas serializowania</span><span class="sxs-lookup"><span data-stu-id="61f74-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="61f74-103">W tym temacie opisano, jak sterowania biały znak w przypadku serializacji drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="61f74-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="61f74-104">Typowy scenariusz jest Odczytaj dane XML z wcięciami, utwórz drzewo XML w pamięci bez żadnych białe węzły tekstowe (to znaczy nie zachowania biały znak), operacji na pliku XML, a następnie zapisz plik XML z wcięcia.</span><span class="sxs-lookup"><span data-stu-id="61f74-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="61f74-105">Podczas formatowania kodu XML, tylko znaczący biały znak w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="61f74-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="61f74-106">Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61f74-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="61f74-107">Inny typowy scenariusz polega może odczytywać i modyfikować XML, który już został celowo wcięcia.</span><span class="sxs-lookup"><span data-stu-id="61f74-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="61f74-108">Nie można zmienić tej wcięcia w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="61f74-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="61f74-109">Aby to zrobić w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można zachować biały znak w przypadku obciążenia lub analizy kodu XML i wyłączyć formatowania podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="61f74-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="61f74-110">Zachowanie biały znak metod, które zserializować drzew XML</span><span class="sxs-lookup"><span data-stu-id="61f74-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="61f74-111">Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klasy serializować drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="61f74-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="61f74-112">Może wykonywać serializację drzewo XML w pliku <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="61f74-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="61f74-113">`ToString` Metody serializuje do ciągu.</span><span class="sxs-lookup"><span data-stu-id="61f74-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="61f74-114">Jeśli metoda nie przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie metoda sformatuje (wcięcie) serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="61f74-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="61f74-115">W takim przypadku wszystkie nieważny biały znak w drzewie XML zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="61f74-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="61f74-116">Jeżeli metoda <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie można określić metody nie format serializacji XML (wcięcie).</span><span class="sxs-lookup"><span data-stu-id="61f74-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="61f74-117">W takim przypadku wszystkie biały znak w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="61f74-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f74-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61f74-118">See Also</span></span>  
 [<span data-ttu-id="61f74-119">Serializacja XML drzew (C#)</span><span class="sxs-lookup"><span data-stu-id="61f74-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
