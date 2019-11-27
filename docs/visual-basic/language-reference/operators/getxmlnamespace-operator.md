---
title: GetXmlNamespace, operator
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
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="d3102-102">GetXmlNamespace — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3102-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="d3102-103">Pobiera obiekt <xref:System.Xml.Linq.XNamespace>, który odnosi się do określonego prefiksu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="d3102-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3102-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3102-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="d3102-105">Części</span><span class="sxs-lookup"><span data-stu-id="d3102-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="d3102-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d3102-106">Optional.</span></span> <span data-ttu-id="d3102-107">Ciąg, który identyfikuje prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="d3102-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="d3102-108">Jeśli jest podany, ten ciąg musi być prawidłowym identyfikatorem XML.</span><span class="sxs-lookup"><span data-stu-id="d3102-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="d3102-109">Aby uzyskać więcej informacji, zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d3102-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="d3102-110">Jeśli nie określono żadnego prefiksu, zwracana jest domyślna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="d3102-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="d3102-111">Jeśli nie określono domyślnej przestrzeni nazw, zwracana jest pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="d3102-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3102-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3102-112">Return Value</span></span>  
 <span data-ttu-id="d3102-113">Obiekt <xref:System.Xml.Linq.XNamespace>, który odnosi się do prefiksu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="d3102-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3102-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3102-114">Remarks</span></span>  
 <span data-ttu-id="d3102-115">Operator `GetXmlNamespace` pobiera obiekt <xref:System.Xml.Linq.XNamespace>, który odnosi się do prefiksu przestrzeni nazw XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="d3102-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="d3102-116">Prefiksy przestrzeni nazw XML można używać bezpośrednio w literałach XML i właściwościach osi XML.</span><span class="sxs-lookup"><span data-stu-id="d3102-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="d3102-117">Należy jednak użyć operatora `GetXmlNamespace`, aby skonwertować prefiks przestrzeni nazw do obiektu <xref:System.Xml.Linq.XNamespace>, zanim będzie można go użyć w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3102-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="d3102-118">Do obiektu <xref:System.Xml.Linq.XNamespace> można dołączyć niekwalifikowaną nazwę elementu, aby uzyskać w pełni kwalifikowany obiekt <xref:System.Xml.Linq.XName>, który jest wymagany przez wiele metod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3102-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3102-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3102-119">Example</span></span>  
 <span data-ttu-id="d3102-120">Poniższy przykład importuje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="d3102-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="d3102-121">Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i uzyskać dostęp do pierwszego węzła podrzędnego, który ma kwalifikowaną nazwę `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="d3102-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="d3102-122">Następnie przekazuje ten węzeł podrzędny do podprocedury `ShowName`, która konstruuje kwalifikowaną nazwę przy użyciu operatora `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="d3102-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="d3102-123">Podprocedura `ShowName` następnie przekazuje kwalifikowaną nazwę do metody <xref:System.Xml.Linq.XNode.Ancestors%2A>, aby uzyskać węzeł nadrzędny `ns:contact`.</span><span class="sxs-lookup"><span data-stu-id="d3102-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="d3102-124">Gdy wywołasz `TestGetXmlNamespace.RunSample()`, zostanie wyświetlone okno komunikatu zawierające następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="d3102-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="d3102-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3102-125">See also</span></span>

- [<span data-ttu-id="d3102-126">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="d3102-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="d3102-127">Uzyskiwanie dostępu do pliku XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3102-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
