---
title: Tworzenie kodu XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 1c720bc2aca4cec3dd10656d924cf2413fc18a2d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351736"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="1e792-102">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e792-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="1e792-103">Visual Basic umożliwia używanie *literałów XML* bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1e792-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="1e792-104">Składnia literału XML reprezentuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów i jest podobna do składni XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="1e792-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="1e792-105">Ułatwia to tworzenie elementów XML, dokumentów i fragmentów programowo, ponieważ kod ma taką samą strukturę jak końcowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="1e792-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e792-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1e792-106">In This Section</span></span>  
  
|<span data-ttu-id="1e792-107">Termin</span><span class="sxs-lookup"><span data-stu-id="1e792-107">Term</span></span>|<span data-ttu-id="1e792-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="1e792-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="1e792-109">Literały XML — przegląd</span><span class="sxs-lookup"><span data-stu-id="1e792-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="1e792-110">Wprowadzenie do literałów XML i sposobu ich powiązania z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e792-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="1e792-111">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="1e792-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="1e792-112">Opisuje sposób używania osadzonych wyrażeń w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="1e792-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="1e792-113">Instrukcje: tworzenie literałów XML</span><span class="sxs-lookup"><span data-stu-id="1e792-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="1e792-114">Opisuje sposób tworzenia elementu XML w kodzie przy użyciu literału XML.</span><span class="sxs-lookup"><span data-stu-id="1e792-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="1e792-115">Biały znak w literałach XML</span><span class="sxs-lookup"><span data-stu-id="1e792-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="1e792-116">Opisuje sposób, w jaki Visual Basic traktuje odstępy w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="1e792-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="1e792-117">Literały XML i specyfikacja XML 1.0</span><span class="sxs-lookup"><span data-stu-id="1e792-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="1e792-118">Opisuje, jak składnia literału XML w Visual Basic odnosi się do specyfikacji XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="1e792-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="1e792-119">Instrukcje: osadzanie wyrażeń w literałach XML</span><span class="sxs-lookup"><span data-stu-id="1e792-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="1e792-120">Opisuje sposób używania osadzonych wyrażeń w literałach XML do tworzenia zawartości w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1e792-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="1e792-121">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="1e792-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="1e792-122">Opisuje wskazówki dotyczące nazewnictwa elementów i atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="1e792-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e792-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e792-123">See also</span></span>

- [<span data-ttu-id="1e792-124">XML</span><span class="sxs-lookup"><span data-stu-id="1e792-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
