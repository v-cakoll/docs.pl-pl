---
title: Zachowywanie białych znaków podczas Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396405"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="2bf27-102">Zachowywanie białych znaków podczas serializowania</span><span class="sxs-lookup"><span data-stu-id="2bf27-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="2bf27-103">W tym temacie opisano, jak sterować białym znakiem podczas serializowania drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2bf27-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="2bf27-104">Typowym scenariuszem jest odczytywanie wciętych plików XML, tworzenie drzewa XML w pamięci bez jakichkolwiek białych węzłów tekstowych (to nie zachowuje białych znaków), wykonywanie niektórych operacji na pliku XML, a następnie zapisywanie kodu XML z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="2bf27-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="2bf27-105">Podczas serializacji pliku XML z formatowaniem zachowywana jest tylko znaczący biały znak w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="2bf27-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="2bf27-106">Jest to zachowanie domyślne dla programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2bf27-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="2bf27-107">Inny typowy scenariusz polega na odczytaniu i zmodyfikowaniu kodu XML, który został już celowo wcięty.</span><span class="sxs-lookup"><span data-stu-id="2bf27-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="2bf27-108">W żaden sposób nie trzeba zmieniać tego wcięcia.</span><span class="sxs-lookup"><span data-stu-id="2bf27-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="2bf27-109">W tym celu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] należy zachować biały znak podczas ładowania lub analizowania kodu XML i wyłączyć formatowanie podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="2bf27-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="2bf27-110">Zachowanie białych znaków metod, które serializować drzewa XML</span><span class="sxs-lookup"><span data-stu-id="2bf27-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="2bf27-111">Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klasy serializacji drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2bf27-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="2bf27-112">Można serializować drzewo XML do pliku, a <xref:System.IO.TextReader> lub <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="2bf27-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2bf27-113">`ToString`Metoda jest serializowana do ciągu.</span><span class="sxs-lookup"><span data-stu-id="2bf27-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="2bf27-114">XElement. ToString ()</span><span class="sxs-lookup"><span data-stu-id="2bf27-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="2bf27-115">XDocument. ToString ()</span><span class="sxs-lookup"><span data-stu-id="2bf27-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="2bf27-116">Jeśli metoda nie przyjmuje <xref:System.Xml.Linq.SaveOptions> argumentu, metoda będzie formatować (wcięcie) serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="2bf27-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="2bf27-117">W takim przypadku wszystkie nieznaczące białe znaki w drzewie XML są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="2bf27-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="2bf27-118">Jeśli metoda przyjmuje <xref:System.Xml.Linq.SaveOptions> jako argument, można określić, że metoda nie formatuje (wcięcie) serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="2bf27-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="2bf27-119">W takim przypadku wszystkie odstępy w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="2bf27-119">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf27-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bf27-120">See also</span></span>

- [<span data-ttu-id="2bf27-121">Serializowanie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bf27-121">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
