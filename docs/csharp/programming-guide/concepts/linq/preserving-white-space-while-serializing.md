---
title: Zachowywanie odstępu podczas serializacji3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d357d40c13a66a152b3c8bb5f61e3a3374c4055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484076"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="f6549-102">Zachowywanie białych znaków podczas serializowania</span><span class="sxs-lookup"><span data-stu-id="f6549-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="f6549-103">W tym temacie opisano sposób kontrolowania odstępu podczas serializacji drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f6549-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="f6549-104">Typowym scenariuszem jest odczyt wciętego kodu XML, utworzenie drzewa XML w pamięci bez żadnych węzłów tekstu odstępu (czyli nie zachowanie odstępu), wykonanie niektórych operacji w pliku XML, a następnie zapisanie kodu XML z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="f6549-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="f6549-105">Podczas serializacji XML z formatowaniem zachowano tylko znaczące odstępy w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="f6549-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="f6549-106">Jest to domyślne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zachowanie dla .</span><span class="sxs-lookup"><span data-stu-id="f6549-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="f6549-107">Innym typowym scenariuszem jest odczytywanie i modyfikowanie języka XML, który został już celowo wcięty.</span><span class="sxs-lookup"><span data-stu-id="f6549-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="f6549-108">W jakikolwiek sposób możesz nie chcieć zmienić tego wcięcia.</span><span class="sxs-lookup"><span data-stu-id="f6549-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="f6549-109">Aby to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zrobić w , należy zachować biały znak podczas ładowania lub analizowania XML i wyłączyć formatowanie podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="f6549-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="f6549-110">Zachowanie odstępu metod serializowania drzew XML</span><span class="sxs-lookup"><span data-stu-id="f6549-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="f6549-111">Następujące metody w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klas serializować drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f6549-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="f6549-112">Drzewo XML można serializować do pliku, <xref:System.IO.TextReader>pliku <xref:System.Xml.XmlReader>lub pliku .</span><span class="sxs-lookup"><span data-stu-id="f6549-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="f6549-113">Metoda `ToString` serializuje do ciągu.</span><span class="sxs-lookup"><span data-stu-id="f6549-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="f6549-114">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="f6549-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="f6549-115">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="f6549-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="f6549-116">Jeśli metoda nie <xref:System.Xml.Linq.SaveOptions> bierze jako argument, a następnie metoda będzie format (wcięcie) serializowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="f6549-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="f6549-117">W takim przypadku wszystkie nieistotne odstępy w drzewie XML są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="f6549-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="f6549-118">Jeśli metoda ma <xref:System.Xml.Linq.SaveOptions> jako argument, a następnie można określić, że metoda nie format (wcięcie) serializowany chyląc XML.</span><span class="sxs-lookup"><span data-stu-id="f6549-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="f6549-119">W takim przypadku wszystkie odstępy w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="f6549-119">In this case, all white space in the XML tree is preserved.</span></span>  
