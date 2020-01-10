---
title: Edytowanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
ms.openlocfilehash: 3b9225f1efcca0f4874a98f2b83d1964aacef735
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710963"
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="967e5-102">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="967e5-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="967e5-103">Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia metody umożliwiające Wstawianie, modyfikowanie i usuwanie węzłów oraz wartości z dokumentu XML zawartego w obiekcie <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="967e5-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="967e5-104">Aby można było użyć dowolnej z tych metod do wstawiania, modyfikowania i usuwania węzłów i wartości, obiekt <xref:System.Xml.XPath.XPathNavigator> musi być edytowalny, oznacza to, że jego właściwość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musi mieć wartość true.</span><span class="sxs-lookup"><span data-stu-id="967e5-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="967e5-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="967e5-105">In This Section</span></span>  
 [<span data-ttu-id="967e5-106">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="967e5-106">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="967e5-107">Opisuje sposób wstawiania elementów równorzędnych, podrzędnych, węzłów atrybutów i wartości w do obiektu <xref:System.Xml.XmlDocument> przy użyciu klasy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="967e5-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="967e5-108">Modyfikowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="967e5-108">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="967e5-109">Opisuje sposób modyfikowania węzłów i wartości w obiekcie <xref:System.Xml.XmlDocument> przy użyciu klasy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="967e5-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="967e5-110">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="967e5-110">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="967e5-111">Opisuje sposób usuwania węzłów i wartości z obiektu <xref:System.Xml.XmlDocument> przy użyciu klasy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="967e5-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967e5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="967e5-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="967e5-113">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="967e5-113">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="967e5-114">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="967e5-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="967e5-115">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="967e5-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="967e5-116">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="967e5-116">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="967e5-117">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="967e5-117">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
