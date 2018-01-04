---
title: "Obsługa typu do zestawów System.Xml klas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 38aa6462fc7a0a1eb80c767777da4f2343983296
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="4f87c-102">Obsługa typu do zestawów System.Xml klas</span><span class="sxs-lookup"><span data-stu-id="4f87c-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="4f87c-103">W programie .NET Framework w wersji 2.0 podstawowe klasy XML zostały rozszerzone i obejmują funkcje obsługi typu.</span><span class="sxs-lookup"><span data-stu-id="4f87c-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="4f87c-104"><xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, I <xref:System.Xml.XPath.XPathNavigator> klasy zawierają funkcje obsługi typu, łącznie z możliwością konwersji między typami schematu XML i typowych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="4f87c-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="4f87c-105">W programie .NET Framework w wersji 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.XPath.XPathNavigator> klasy zostały rozszerzone i obejmują funkcje obsługi typu.</span><span class="sxs-lookup"><span data-stu-id="4f87c-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
-   <span data-ttu-id="4f87c-106"><xref:System.Xml.XmlReader> i <xref:System.Xml.XPath.XPathNavigator> obejmują klasy każdego **SchemaInfo** właściwości zwracające informacje o schemacie na węźle.</span><span class="sxs-lookup"><span data-stu-id="4f87c-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
-   <span data-ttu-id="4f87c-107">**ReadContentAs** i **ReadElementContentAs** i metody <xref:System.Xml.XmlReader> klasy odczytu wartość tekstową i przekonwertować go na wartość CLR w wywołaniu pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="4f87c-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
-   <span data-ttu-id="4f87c-108"><xref:System.Xml.XmlWriter.WriteValue%2A> Metoda <xref:System.Xml.XmlWriter> klasy konwertuje typu CLR na typ schematu XML podczas zapisywania XML.</span><span class="sxs-lookup"><span data-stu-id="4f87c-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
-   <span data-ttu-id="4f87c-109">**ValueAs** i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy może zwracać wartości węzła i przekonwertować go na wartość CLR w wywołaniu pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="4f87c-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f87c-110">W programie .NET Framework w wersji 1.0 <xref:System.Xml.XmlConvert> klasy było wymagane do konwersji między typami CLR i schematu XML.</span><span class="sxs-lookup"><span data-stu-id="4f87c-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f87c-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4f87c-111">In This Section</span></span>  
 [<span data-ttu-id="4f87c-112">Mapowanie typów danych XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="4f87c-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="4f87c-113">W tym artykule opisano domyślne mapowania typów danych XML do typów CLR.</span><span class="sxs-lookup"><span data-stu-id="4f87c-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="4f87c-114">Obsługiwane typy XML — uwagi dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="4f87c-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="4f87c-115">Omówiono niektóre szczegóły implementacji typu pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="4f87c-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="4f87c-116">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="4f87c-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="4f87c-117">Informacje dotyczące używania <xref:System.Xml.XmlConvert> klasy do konwersji między typami CLR i schematu XML.</span><span class="sxs-lookup"><span data-stu-id="4f87c-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4f87c-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4f87c-118">Related Sections</span></span>  
 [<span data-ttu-id="4f87c-119">Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4f87c-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
