---
title: Operator GetXmlNamespace
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353193"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="9463d-102">GetXmlNamespace — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9463d-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="9463d-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="9463d-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9463d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9463d-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="9463d-105">Części</span><span class="sxs-lookup"><span data-stu-id="9463d-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="9463d-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9463d-106">Optional.</span></span> <span data-ttu-id="9463d-107">The string that identifies the XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="9463d-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="9463d-108">If supplied, this string must be a valid XML identifier.</span><span class="sxs-lookup"><span data-stu-id="9463d-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="9463d-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9463d-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="9463d-110">If no prefix is specified, the default namespace is returned.</span><span class="sxs-lookup"><span data-stu-id="9463d-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="9463d-111">If no default namespace is specified, the empty namespace is returned.</span><span class="sxs-lookup"><span data-stu-id="9463d-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9463d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9463d-112">Return Value</span></span>  
 <span data-ttu-id="9463d-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="9463d-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9463d-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9463d-114">Remarks</span></span>  
 <span data-ttu-id="9463d-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="9463d-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="9463d-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span><span class="sxs-lookup"><span data-stu-id="9463d-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="9463d-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span><span class="sxs-lookup"><span data-stu-id="9463d-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="9463d-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span><span class="sxs-lookup"><span data-stu-id="9463d-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9463d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="9463d-119">Example</span></span>  
 <span data-ttu-id="9463d-120">The following example imports `ns` as an XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="9463d-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="9463d-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="9463d-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="9463d-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span><span class="sxs-lookup"><span data-stu-id="9463d-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="9463d-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span><span class="sxs-lookup"><span data-stu-id="9463d-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="9463d-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span><span class="sxs-lookup"><span data-stu-id="9463d-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="9463d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9463d-125">See also</span></span>

- [<span data-ttu-id="9463d-126">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="9463d-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="9463d-127">Accessing XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9463d-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
