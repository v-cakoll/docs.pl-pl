---
title: Obsługa typu w ramach klas zestawu System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026890"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="372a4-102">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="372a4-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="372a4-103">W programie .NET Framework 2.0 główne klasy XML zostały rozszerzone i obejmują funkcje pomocy technicznej typu.</span><span class="sxs-lookup"><span data-stu-id="372a4-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="372a4-104"><xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, I <xref:System.Xml.XPath.XPathNavigator> klas obejmują funkcje pomocy technicznej typu, łącznie z możliwością do konwersji między typami schematu XML i typowych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="372a4-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="372a4-105">W .NET Framework w wersji 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.XPath.XPathNavigator> klasy zostały rozszerzone i obejmują funkcje pomocy technicznej typu.</span><span class="sxs-lookup"><span data-stu-id="372a4-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="372a4-106"><xref:System.Xml.XmlReader> i <xref:System.Xml.XPath.XPathNavigator> zawierają klasy każdego **może** właściwość, która zwraca informacje o schemacie dla węzła.</span><span class="sxs-lookup"><span data-stu-id="372a4-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="372a4-107">**ReadContentAs** i **ReadElementContentAs** i metod <xref:System.Xml.XmlReader> klasy odczytaj wartość tekstową i przekonwertować go na wartość CLR w pojedynczym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="372a4-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="372a4-108"><xref:System.Xml.XmlWriter.WriteValue%2A> Metody <xref:System.Xml.XmlWriter> klasy konwertuje typ CLR na typ schematu XML podczas zapisywania na poziomie XML.</span><span class="sxs-lookup"><span data-stu-id="372a4-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="372a4-109">**ValueAs** i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy może zwracać wartości węzła i przekonwertować go na wartość CLR w pojedynczym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="372a4-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="372a4-110">W .NET Framework w wersji 1.0 <xref:System.Xml.XmlConvert> klasy był niezbędny do konwersji między typami CLR i schematu XML.</span><span class="sxs-lookup"><span data-stu-id="372a4-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="372a4-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="372a4-111">In This Section</span></span>  
 [<span data-ttu-id="372a4-112">Mapowanie typów danych XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="372a4-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="372a4-113">W tym artykule opisano domyślne mapowania typów danych XML na typy CLR.</span><span class="sxs-lookup"><span data-stu-id="372a4-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="372a4-114">Obsługiwane typy XML — uwagi dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="372a4-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="372a4-115">W tym artykule omówiono, niektóre szczegóły implementacji typ pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="372a4-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="372a4-116">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="372a4-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="372a4-117">Opisuje sposób używania <xref:System.Xml.XmlConvert> klasy do konwersji między typami CLR i schematu XML.</span><span class="sxs-lookup"><span data-stu-id="372a4-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="372a4-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="372a4-118">Related Sections</span></span>  
 [<span data-ttu-id="372a4-119">Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="372a4-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
