---
title: "Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="5624a-102">Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5624a-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="5624a-103">Ten temat zawiera [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zasady nazewnictwa elementów XML oraz atrybuty w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="5624a-103">This topic provides [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="5624a-104">W literał XML można określić nazwę lokalną lub kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5624a-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="5624a-105">Kwalifikowana nazwa składa się z prefiksu przestrzeni nazw XML, dwukropek i nazwa lokalna.</span><span class="sxs-lookup"><span data-stu-id="5624a-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="5624a-106">Aby uzyskać więcej informacji na temat prefiksy przestrzeni nazw XML, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5624a-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5624a-107">Reguły</span><span class="sxs-lookup"><span data-stu-id="5624a-107">Rules</span></span>  
 <span data-ttu-id="5624a-108">Lokalna nazwa elementu lub atrybutu w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] muszą być zgodne z następującymi zasadami.</span><span class="sxs-lookup"><span data-stu-id="5624a-108">A local name of an element or attribute in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="5624a-109">Może ona rozpoczynać przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5624a-109">It can begin with a namespace.</span></span> <span data-ttu-id="5624a-110">Musi zaczynać się od litery lub znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="5624a-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="5624a-111">Musi zawierać tylko znaki alfabetyczne, cyfry dziesiętne, znaki podkreślenia, kropki (.) i łączniki (-).</span><span class="sxs-lookup"><span data-stu-id="5624a-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="5624a-112">Nie może być więcej niż 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="5624a-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="5624a-113">Dwukropki, które pojawiają się w nazwach wskazują odgraniczenie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5624a-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="5624a-114">W związku z tym umożliwia dwukropki tylko określić przestrzeń nazw XML dla określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5624a-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="5624a-115">Ponadto należy przestrzegać następujących wytycznych.</span><span class="sxs-lookup"><span data-stu-id="5624a-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="5624a-116">Specyfikacja XML 1.0 zastrzega sobie wszystkie nazwy zaczynającym się od ciągu "xml" jakiekolwiek zmiany wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="5624a-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="5624a-117">W związku z tym nie należy używać tych nazw dla danego elementu i nazwach atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5624a-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="5624a-118">Wskazówki dotyczące długość nazwy</span><span class="sxs-lookup"><span data-stu-id="5624a-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="5624a-119">Jak to w praktyce nazwa powinna być możliwie krótki podczas nadal jednoznacznie identyfikujący rodzaj elementu.</span><span class="sxs-lookup"><span data-stu-id="5624a-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="5624a-120">To poprawia czytelność kodu i zmniejsza rozmiar linii długość i pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5624a-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="5624a-121">Nazwa nie należy jednak tak krótki, że nie można ją było właściwie opisano element lub kodu używaniu go.</span><span class="sxs-lookup"><span data-stu-id="5624a-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="5624a-122">Jest to ważne w przypadku czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="5624a-122">This is important for the readability of your code.</span></span> <span data-ttu-id="5624a-123">Jeśli ktoś próbuje go zrozumieć, lub jeśli chcesz samodzielnie go przez długi czas, po jego zapisano, nazwy odpowiednich elementów zaoszczędzić czas.</span><span class="sxs-lookup"><span data-stu-id="5624a-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="5624a-124">Uwzględniana wielkość liter w nazwach</span><span class="sxs-lookup"><span data-stu-id="5624a-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="5624a-125">Nazwy elementów XML jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="5624a-125">XML element names are case sensitive.</span></span> <span data-ttu-id="5624a-126">Oznacza to, że w przypadku [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora porównuje dwie nazwy, które różnią się alfabetycznej tylko wielkością liter, jego interpretuje je jako różne nazwy.</span><span class="sxs-lookup"><span data-stu-id="5624a-126">This means that when the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="5624a-127">Na przykład interpretuje `ABC` i `abc` jako odnoszące się do oddzielania elementów.</span><span class="sxs-lookup"><span data-stu-id="5624a-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5624a-128">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="5624a-128">XML Namespaces</span></span>  
 <span data-ttu-id="5624a-129">Podczas tworzenia literał elementu XML, można określić prefiks przestrzeni nazw XML dla nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="5624a-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="5624a-130">Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5624a-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5624a-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5624a-131">See Also</span></span>  
 [<span data-ttu-id="5624a-132">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5624a-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="5624a-133">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="5624a-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
