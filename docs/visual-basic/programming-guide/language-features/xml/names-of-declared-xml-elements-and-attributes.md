---
title: Nazwy deklarowanych elementów i atrybutów XML
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 12fbd1f4332391b1acdcf12e101d82627ebbeaff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335985"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="6fcf2-102">Nazwy deklarowanych elementów XML oraz atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fcf2-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="6fcf2-103">Ten temat zawiera Visual Basic wskazówki dotyczące nazewnictwa elementów i atrybutów XML w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="6fcf2-104">W literale XML można określić nazwę lokalną lub kwalifikowaną nazwę.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="6fcf2-105">Kwalifikowana nazwa składa się z prefiksu przestrzeni nazw XML, dwukropka i nazwy lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="6fcf2-106">Aby uzyskać więcej informacji na temat prefiksów przestrzeni nazw XML, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="6fcf2-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6fcf2-107">Reguły</span><span class="sxs-lookup"><span data-stu-id="6fcf2-107">Rules</span></span>  
 <span data-ttu-id="6fcf2-108">Lokalna nazwa elementu lub atrybutu w Visual Basic musi być zgodna z poniższymi regułami.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="6fcf2-109">Może zaczynać się od przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-109">It can begin with a namespace.</span></span> <span data-ttu-id="6fcf2-110">Musi zaczynać się od litery lub znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="6fcf2-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="6fcf2-111">Musi zawierać tylko litery alfabetu, cyfry dziesiętne, podkreślenia, kropki (.) i łączniki (-).</span><span class="sxs-lookup"><span data-stu-id="6fcf2-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="6fcf2-112">Nie może być dłuższa niż 1 024 znaków.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="6fcf2-113">Dwukropek, które pojawiają się w nazwach, wskazują na rozgraniczenie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="6fcf2-114">W związku z tym, można użyć dwukropka, aby określić przestrzeń nazw XML dla określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="6fcf2-115">Ponadto należy przestrzegać następujących wytycznych.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="6fcf2-116">Specyfikacja XML 1,0 rezerwuje wszystkie nazwy zaczynające się od ciągu "XML" dowolnej zmiany wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="6fcf2-117">W związku z tym nie należy używać tych nazw dla nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="6fcf2-118">Wskazówki dotyczące długości nazwy</span><span class="sxs-lookup"><span data-stu-id="6fcf2-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="6fcf2-119">Jako praktyczna nazwa powinna być tak krótka, jak to możliwe, podczas gdy nadal jednoznacznie identyfikuje charakter elementu.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="6fcf2-120">Poprawia to czytelność kodu i zmniejsza długość wiersza i rozmiar pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="6fcf2-121">Jednak Twoja nazwa nie powinna być tak krótka, aby nie była odpowiednio opisywana elementu lub jak kod używa go.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="6fcf2-122">Jest to ważne dla czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-122">This is important for the readability of your code.</span></span> <span data-ttu-id="6fcf2-123">Jeśli ktoś inny próbuje zrozumieć ten element, lub jeśli ty zobaczysz swoją godzinę po jej zapisaniu, odpowiednie nazwy elementów mogą zaoszczędzić czas.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="6fcf2-124">Rozróżnianie wielkości liter w nazwach</span><span class="sxs-lookup"><span data-stu-id="6fcf2-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="6fcf2-125">W nazwach elementów XML jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-125">XML element names are case sensitive.</span></span> <span data-ttu-id="6fcf2-126">Oznacza to, że kiedy kompilator Visual Basic porównuje dwie nazwy, które różnią się tylko wielkością liter, interpretuje je jako różne nazwy.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="6fcf2-127">Na przykład interpretuje `ABC` i `abc` w odniesieniu do oddzielnych elementów.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="6fcf2-128">Przestrzenie nazw XML</span><span class="sxs-lookup"><span data-stu-id="6fcf2-128">XML Namespaces</span></span>  
 <span data-ttu-id="6fcf2-129">Podczas tworzenia literału elementu XML, można określić prefiks przestrzeni nazw XML dla nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="6fcf2-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="6fcf2-130">Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="6fcf2-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcf2-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fcf2-131">See also</span></span>

- [<span data-ttu-id="6fcf2-132">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fcf2-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="6fcf2-133">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="6fcf2-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
