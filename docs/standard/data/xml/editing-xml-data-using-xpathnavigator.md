---
title: Edytowanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
ms.openlocfilehash: 11395c52e399068e5242a1e041ebd9ed94bc2881
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292075"
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="88d2d-102">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="88d2d-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="88d2d-103"><xref:System.Xml.XPath.XPathNavigator>Klasa zawiera metody umożliwiające Wstawianie, modyfikowanie i usuwanie węzłów oraz wartości z dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="88d2d-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="88d2d-104">Aby można było użyć którejkolwiek z tych metod do wstawiania, modyfikowania i usuwania węzłów i wartości, <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, oznacza to, że jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Właściwość musi mieć wartość true.</span><span class="sxs-lookup"><span data-stu-id="88d2d-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88d2d-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="88d2d-105">In This Section</span></span>  
 [<span data-ttu-id="88d2d-106">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="88d2d-106">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="88d2d-107">Opisuje sposób wstawiania elementów równorzędnych, podrzędnych, węzłów atrybutów i wartości w <xref:System.Xml.XmlDocument> obiekcie do obiektu za pomocą <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="88d2d-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="88d2d-108">Modyfikowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="88d2d-108">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="88d2d-109">Opisuje sposób modyfikowania węzłów i wartości w <xref:System.Xml.XmlDocument> obiekcie przy użyciu <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="88d2d-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="88d2d-110">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="88d2d-110">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="88d2d-111">Opisuje sposób usuwania węzłów i wartości z <xref:System.Xml.XmlDocument> obiektu przy użyciu <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="88d2d-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88d2d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88d2d-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="88d2d-113">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="88d2d-113">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="88d2d-114">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="88d2d-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="88d2d-115">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="88d2d-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="88d2d-116">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="88d2d-116">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="88d2d-117">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="88d2d-117">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
