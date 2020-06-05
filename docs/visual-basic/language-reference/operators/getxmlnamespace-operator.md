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
ms.openlocfilehash: 85422fb9e11d78e228577adc25cba746149c645a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371119"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="3ccf8-102">GetXmlNamespace — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ccf8-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="3ccf8-103">Pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do określonego prefiksu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ccf8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ccf8-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="3ccf8-105">Części</span><span class="sxs-lookup"><span data-stu-id="3ccf8-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="3ccf8-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-106">Optional.</span></span> <span data-ttu-id="3ccf8-107">Ciąg, który identyfikuje prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="3ccf8-108">Jeśli jest podany, ten ciąg musi być prawidłowym identyfikatorem XML.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="3ccf8-109">Aby uzyskać więcej informacji, zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3ccf8-109">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="3ccf8-110">Jeśli nie określono żadnego prefiksu, zwracana jest domyślna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="3ccf8-111">Jeśli nie określono domyślnej przestrzeni nazw, zwracana jest pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ccf8-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3ccf8-112">Return Value</span></span>  
 <span data-ttu-id="3ccf8-113"><xref:System.Xml.Linq.XNamespace>Obiekt, który odnosi się do prefiksu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ccf8-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ccf8-114">Remarks</span></span>  
 <span data-ttu-id="3ccf8-115">`GetXmlNamespace`Operator pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do prefiksu przestrzeni nazw XML `xmlNamespacePrefix` .</span><span class="sxs-lookup"><span data-stu-id="3ccf8-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="3ccf8-116">Prefiksy przestrzeni nazw XML można używać bezpośrednio w literałach XML i właściwościach osi XML.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="3ccf8-117">Należy jednak użyć `GetXmlNamespace` operatora, aby przekonwertować prefiks przestrzeni nazw na <xref:System.Xml.Linq.XNamespace> obiekt, zanim będzie można go użyć w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="3ccf8-118">Do obiektu można dołączyć niekwalifikowaną nazwę elementu <xref:System.Xml.Linq.XNamespace> , aby uzyskać w pełni kwalifikowany <xref:System.Xml.Linq.XName> obiekt, którego [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wymaga wiele metod.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ccf8-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ccf8-119">Example</span></span>  
 <span data-ttu-id="3ccf8-120">Poniższy przykład importuje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="3ccf8-121">Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i uzyskać dostęp do pierwszego węzła podrzędnego, który ma kwalifikowaną nazwę `ns:phone` .</span><span class="sxs-lookup"><span data-stu-id="3ccf8-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="3ccf8-122">Następnie przekazuje ten węzeł podrzędny do `ShowName` podprocedury, która konstruuje kwalifikowaną nazwę przy użyciu `GetXmlNamespace` operatora.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="3ccf8-123">`ShowName`Procedura ta przekazuje nazwę kwalifikowaną do <xref:System.Xml.Linq.XNode.Ancestors%2A> metody w celu pobrania `ns:contact` węzła nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3ccf8-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="3ccf8-124">Po wywołaniu programu zostanie `TestGetXmlNamespace.RunSample()` wyświetlone okno komunikatu zawierające następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="3ccf8-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="3ccf8-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ccf8-125">See also</span></span>

- [<span data-ttu-id="3ccf8-126">Imports — Instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="3ccf8-126">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="3ccf8-127">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ccf8-127">Accessing XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/accessing-xml.md)
