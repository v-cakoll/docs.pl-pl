---
title: Obsługa typu w ramach klas zestawu System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710105"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="05a23-102">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="05a23-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="05a23-103">W .NET Framework w wersji 2,0 podstawowe klasy XML zostały ulepszone w celu uwzględnienia funkcji obsługi typu.</span><span class="sxs-lookup"><span data-stu-id="05a23-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="05a23-104">Klasy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>i <xref:System.Xml.XPath.XPathNavigator> zawierają funkcje obsługi typu, w tym możliwość konwersji między typami schematu XML i typami środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="05a23-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="05a23-105">W .NET Framework w wersji 2,0, klasy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>i <xref:System.Xml.XPath.XPathNavigator> zostały ulepszone w celu uwzględnienia funkcji obsługi typu.</span><span class="sxs-lookup"><span data-stu-id="05a23-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="05a23-106">Klasy <xref:System.Xml.XmlReader> i <xref:System.Xml.XPath.XPathNavigator> zawierają Właściwość **SchemaInfo** , która zwraca informacje o schemacie w węźle.</span><span class="sxs-lookup"><span data-stu-id="05a23-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="05a23-107">**ReadContentAs** i **ReadElementContentAs** i metody <xref:System.Xml.XmlReader> klasy odczytają wartość tekstową i konwertują ją na wartość CLR w wywołaniu pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="05a23-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="05a23-108"><xref:System.Xml.XmlWriter.WriteValue%2A> Metoda w <xref:System.Xml.XmlWriter> klasie konwertuje typ CLR na typ schematu XML podczas pisania kodu XML.</span><span class="sxs-lookup"><span data-stu-id="05a23-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="05a23-109">**ValueAs** i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy zwracają wartość węzła i konwertują ją na wartość CLR w pojedynczym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="05a23-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05a23-110">W .NET Framework w wersji 1,0 <xref:System.Xml.XmlConvert> Klasa była wymagana do konwersji między schematem XML i typami CLR.</span><span class="sxs-lookup"><span data-stu-id="05a23-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05a23-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="05a23-111">In This Section</span></span>  
 [<span data-ttu-id="05a23-112">Mapowanie typów danych XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="05a23-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="05a23-113">Opisuje domyślne mapowania typów danych XML na typy CLR.</span><span class="sxs-lookup"><span data-stu-id="05a23-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="05a23-114">Obsługiwane typy XML — uwagi dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="05a23-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="05a23-115">W tym artykule omówiono niektóre typy szczegółów implementacji.</span><span class="sxs-lookup"><span data-stu-id="05a23-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="05a23-116">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="05a23-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="05a23-117">Opisuje sposób użycia <xref:System.Xml.XmlConvert> klasy do konwersji między schematem XML i typami CLR.</span><span class="sxs-lookup"><span data-stu-id="05a23-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05a23-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="05a23-118">Related Sections</span></span>  
 [<span data-ttu-id="05a23-119">Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="05a23-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
