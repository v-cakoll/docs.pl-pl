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
ms.openlocfilehash: e21cf160d10f308990894d1a85c4f5d05b90f68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603486"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="aea5e-102">GetXmlNamespace — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aea5e-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="aea5e-103">Pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada określony prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="aea5e-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aea5e-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="aea5e-105">Części</span><span class="sxs-lookup"><span data-stu-id="aea5e-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="aea5e-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="aea5e-106">Optional.</span></span> <span data-ttu-id="aea5e-107">Ciąg, który identyfikuje prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="aea5e-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="aea5e-108">Jeśli podany, ten ciąg musi być prawidłowym identyfikatorem XML.</span><span class="sxs-lookup"><span data-stu-id="aea5e-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="aea5e-109">Aby uzyskać więcej informacji, zobacz [nazwy z zadeklarowany elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="aea5e-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="aea5e-110">Jeśli określono bez prefiksu, jest zwracany domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="aea5e-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="aea5e-111">Jeśli nie domyślnej przestrzeni nazw jest określony, zwracana jest pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="aea5e-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aea5e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aea5e-112">Return Value</span></span>  
 <span data-ttu-id="aea5e-113"><xref:System.Xml.Linq.XNamespace> Obiekt, który odpowiada prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="aea5e-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aea5e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aea5e-114">Remarks</span></span>  
 <span data-ttu-id="aea5e-115">`GetXmlNamespace` Uzyskuje operator <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada prefiks przestrzeni nazw XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="aea5e-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="aea5e-116">Możesz użyć prefiksy przestrzeni nazw XML bezpośrednio w literałach XML i właściwości osi XML.</span><span class="sxs-lookup"><span data-stu-id="aea5e-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="aea5e-117">Jednak należy użyć `GetXmlNamespace` operatora prefiksu przestrzeni nazw, aby przekonwertować <xref:System.Xml.Linq.XNamespace> obiekt przed użyciem w kodzie.</span><span class="sxs-lookup"><span data-stu-id="aea5e-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="aea5e-118">Możesz dołączyć nazwę elementu niekwalifikowane do <xref:System.Xml.Linq.XNamespace> obiektu można uzyskać w pełni kwalifikowanej <xref:System.Xml.Linq.XName> obiektów, które wielu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody wymagają.</span><span class="sxs-lookup"><span data-stu-id="aea5e-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea5e-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="aea5e-119">Example</span></span>  
 <span data-ttu-id="aea5e-120">Poniższy przykład importuje `ns` jako prefiks przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="aea5e-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="aea5e-121">Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępu do pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="aea5e-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="aea5e-122">Następnie przekazuje tego węzła podrzędnego do `ShowName` procedury, która tworzy nazwy kwalifikowanej przy użyciu `GetXmlNamespace` operatora.</span><span class="sxs-lookup"><span data-stu-id="aea5e-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="aea5e-123">`ShowName` Podprocedury następnie przekazuje nazwę kwalifikowaną <xref:System.Xml.Linq.XNode.Ancestors%2A> metodę, aby pobrać element nadrzędny `ns:contact` węzła.</span><span class="sxs-lookup"><span data-stu-id="aea5e-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="aea5e-124">Podczas wywoływania `TestGetXmlNamespace.RunSample()`, wyświetla komunikat, który zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="aea5e-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="aea5e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aea5e-125">See Also</span></span>  
 [<span data-ttu-id="aea5e-126">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="aea5e-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="aea5e-127">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aea5e-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
