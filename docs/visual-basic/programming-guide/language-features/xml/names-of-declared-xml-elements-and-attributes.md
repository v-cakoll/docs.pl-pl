---
title: Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07666ead0770c8055a62f75cb481648b0c72ef8b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="dce9f-102">Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dce9f-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="dce9f-103">Ten temat zawiera wskazówki dotyczące języka Visual Basic dla nazw elementów XML oraz atrybuty w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="dce9f-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="dce9f-104">W literał XML można określić nazwę lokalną lub kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="dce9f-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="dce9f-105">Kwalifikowana nazwa składa się z prefiksu przestrzeni nazw XML, dwukropek i nazwa lokalna.</span><span class="sxs-lookup"><span data-stu-id="dce9f-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="dce9f-106">Aby uzyskać więcej informacji na temat prefiksy przestrzeni nazw XML, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dce9f-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="dce9f-107">Reguły</span><span class="sxs-lookup"><span data-stu-id="dce9f-107">Rules</span></span>  
 <span data-ttu-id="dce9f-108">Lokalna nazwa elementu lub atrybutu w języku Visual Basic muszą spełniać następujące reguły.</span><span class="sxs-lookup"><span data-stu-id="dce9f-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="dce9f-109">Może ona rozpoczynać przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dce9f-109">It can begin with a namespace.</span></span> <span data-ttu-id="dce9f-110">Musi zaczynać się od litery lub znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="dce9f-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="dce9f-111">Musi zawierać tylko znaki alfabetyczne, cyfry dziesiętne, znaki podkreślenia, kropki (.) i łączniki (-).</span><span class="sxs-lookup"><span data-stu-id="dce9f-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="dce9f-112">Nie może być więcej niż 1024 znaków.</span><span class="sxs-lookup"><span data-stu-id="dce9f-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="dce9f-113">Dwukropki, które pojawiają się w nazwach wskazują odgraniczenie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dce9f-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="dce9f-114">W związku z tym umożliwia dwukropki tylko określić przestrzeń nazw XML dla określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="dce9f-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="dce9f-115">Ponadto należy przestrzegać następujących wytycznych.</span><span class="sxs-lookup"><span data-stu-id="dce9f-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="dce9f-116">Specyfikacja XML 1.0 zastrzega sobie wszystkie nazwy zaczynającym się od ciągu "xml" jakiekolwiek zmiany wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="dce9f-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="dce9f-117">W związku z tym nie należy używać tych nazw dla danego elementu i nazwach atrybutów.</span><span class="sxs-lookup"><span data-stu-id="dce9f-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="dce9f-118">Wskazówki dotyczące długość nazwy</span><span class="sxs-lookup"><span data-stu-id="dce9f-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="dce9f-119">Jak to w praktyce nazwa powinna być możliwie krótki podczas nadal jednoznacznie identyfikujący rodzaj elementu.</span><span class="sxs-lookup"><span data-stu-id="dce9f-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="dce9f-120">To poprawia czytelność kodu i zmniejsza rozmiar linii długość i pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="dce9f-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="dce9f-121">Nazwa nie należy jednak tak krótki, że nie można ją było właściwie opisano element lub kodu używaniu go.</span><span class="sxs-lookup"><span data-stu-id="dce9f-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="dce9f-122">Jest to ważne w przypadku czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="dce9f-122">This is important for the readability of your code.</span></span> <span data-ttu-id="dce9f-123">Jeśli ktoś próbuje go zrozumieć, lub jeśli chcesz samodzielnie go przez długi czas, po jego zapisano, nazwy odpowiednich elementów zaoszczędzić czas.</span><span class="sxs-lookup"><span data-stu-id="dce9f-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="dce9f-124">Uwzględniana wielkość liter w nazwach</span><span class="sxs-lookup"><span data-stu-id="dce9f-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="dce9f-125">Nazwy elementów XML jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="dce9f-125">XML element names are case sensitive.</span></span> <span data-ttu-id="dce9f-126">Oznacza to, że gdy kompilator Visual Basic porównuje dwie nazwy, które różnią się alfabetycznej tylko wielkością liter, jego interpretuje je jako różne nazwy.</span><span class="sxs-lookup"><span data-stu-id="dce9f-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="dce9f-127">Na przykład interpretuje `ABC` i `abc` jako odnoszące się do oddzielania elementów.</span><span class="sxs-lookup"><span data-stu-id="dce9f-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="dce9f-128">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="dce9f-128">XML Namespaces</span></span>  
 <span data-ttu-id="dce9f-129">Podczas tworzenia literał elementu XML, można określić prefiks przestrzeni nazw XML dla nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="dce9f-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="dce9f-130">Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dce9f-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce9f-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dce9f-131">See Also</span></span>  
 [<span data-ttu-id="dce9f-132">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dce9f-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="dce9f-133">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="dce9f-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
