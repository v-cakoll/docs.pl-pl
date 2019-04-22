---
title: GetXmlNamespace — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 757ca54e5ba370bf2cc48bc70499e7b43ec96ef6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834754"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="97d43-102">GetXmlNamespace — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97d43-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="97d43-103">Pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada określony prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="97d43-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97d43-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="97d43-105">Części</span><span class="sxs-lookup"><span data-stu-id="97d43-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="97d43-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="97d43-106">Optional.</span></span> <span data-ttu-id="97d43-107">Ciąg, który identyfikuje prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="97d43-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="97d43-108">Jeśli zostanie podany, ten ciąg musi być prawidłowym identyfikatorem XML.</span><span class="sxs-lookup"><span data-stu-id="97d43-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="97d43-109">Aby uzyskać więcej informacji, zobacz [nazwy z zadeklarowane elementy i atrybuty XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="97d43-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="97d43-110">Jeśli określono żadnego prefiksu, zwracany jest domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="97d43-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="97d43-111">Jeśli nie domyślny obszar nazw jest określony, zwracany jest pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="97d43-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97d43-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="97d43-112">Return Value</span></span>  
 <span data-ttu-id="97d43-113"><xref:System.Xml.Linq.XNamespace> Obiekt, który odnosi się do prefiksu przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="97d43-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d43-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97d43-114">Remarks</span></span>  
 <span data-ttu-id="97d43-115">`GetXmlNamespace` Operator pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do prefiksu przestrzeni nazw XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="97d43-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="97d43-116">Możesz użyć prefiksy przestrzeni nazw XML bezpośrednio w literałach XML i właściwości osi XML.</span><span class="sxs-lookup"><span data-stu-id="97d43-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="97d43-117">Jednakże, należy użyć `GetXmlNamespace` operatora konwersji prefiksu przestrzeni nazw <xref:System.Xml.Linq.XNamespace> obiekt przed jego użyciem w kodzie.</span><span class="sxs-lookup"><span data-stu-id="97d43-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="97d43-118">Możesz dołączyć niekwalifikowane nazwy do <xref:System.Xml.Linq.XNamespace> można uzyskać w pełni kwalifikowanym <xref:System.Xml.Linq.XName> obiekt, który wielu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody wymagają.</span><span class="sxs-lookup"><span data-stu-id="97d43-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97d43-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="97d43-119">Example</span></span>  
 <span data-ttu-id="97d43-120">Następujący przykład importuje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="97d43-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="97d43-121">Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="97d43-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="97d43-122">Następnie przekazuje tego węzła podrzędnego do `ShowName` podprocedury, który konstruuje nazwa kwalifikowana za pomocą `GetXmlNamespace` operatora.</span><span class="sxs-lookup"><span data-stu-id="97d43-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="97d43-123">`ShowName` Podprocedury następnie przekazuje kwalifikowanej nazwy, która <xref:System.Xml.Linq.XNode.Ancestors%2A> metodę, aby uzyskać element nadrzędny `ns:contact` węzła.</span><span class="sxs-lookup"><span data-stu-id="97d43-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="97d43-124">Gdy wywołujesz `TestGetXmlNamespace.RunSample()`, wyświetla okno komunikatu, który zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="97d43-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="97d43-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97d43-125">See also</span></span>

- [<span data-ttu-id="97d43-126">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="97d43-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="97d43-127">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="97d43-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
