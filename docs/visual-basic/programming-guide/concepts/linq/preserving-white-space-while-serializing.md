---
title: Zachowywanie białych znaków podczas Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: a08d69a817c3e493e571d1b3b98f6f2a144ad995
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254519"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="3ded8-102">Zachowywanie białych znaków podczas serializowania</span><span class="sxs-lookup"><span data-stu-id="3ded8-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="3ded8-103">W tym temacie opisano sposób kontrolowania biały znak podczas serializowania drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3ded8-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="3ded8-104">Typowym scenariuszem jest Odczytaj dane XML z wcięciami, utworzyć drzewa XML w pamięci bez wszystkie węzły tekstowe białe miejsca (to znaczy nie zachowania biały), wykonywanie operacji na pliku XML, a następnie zapisz plik XML, z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="3ded8-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="3ded8-105">Po użytkownik serializacji XML za pomocą formatowania, tylko istotne biały znak w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="3ded8-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="3ded8-106">Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ded8-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="3ded8-107">Inny typowy scenariusz polega na odczytywanie i modyfikację XML, który już został celowo z wcięciami.</span><span class="sxs-lookup"><span data-stu-id="3ded8-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="3ded8-108">Nie można zmienić to wcięcie w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="3ded8-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="3ded8-109">Aby to zrobić w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], gdy obciążenia lub nemohla analyzovat kód XML i Wyłącz formatowanie podczas serializacji XML jest zachowany biały znak.</span><span class="sxs-lookup"><span data-stu-id="3ded8-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="3ded8-110">Biały metod, które serializowanie drzew XML</span><span class="sxs-lookup"><span data-stu-id="3ded8-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="3ded8-111">Następujące metody w klasie <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klasy serializacji drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3ded8-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="3ded8-112">Może wykonywać serializację drzewa XML w pliku <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3ded8-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3ded8-113">`ToString` Metoda serializuje do ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ded8-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3ded8-114">Jeśli metoda nie przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie metoda sformatuje (wcięcie) serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="3ded8-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="3ded8-115">W takim przypadku wszystkie nieważny biały znak w drzewie XML jest odrzucany.</span><span class="sxs-lookup"><span data-stu-id="3ded8-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="3ded8-116">Jeśli metoda <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie można określić metody nie formatu (wcięcie) serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="3ded8-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="3ded8-117">W takim przypadku wszystkie biały znak w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="3ded8-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ded8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ded8-118">See Also</span></span>  
 [<span data-ttu-id="3ded8-119">Serializowanie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ded8-119">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
