---
title: Tworzenie XML w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: d847f589bc47f8ab3d6691666bbd879e795db0c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756523"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="1cfc7-102">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cfc7-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="1cfc7-103">Visual Basic umożliwia użycie *literałów XML* bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="1cfc7-104">Literał składnia XML przedstawia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów która jest podobna do składni XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="1cfc7-105">Ta funkcja ułatwia programistycznym tworzeniu elementów, dokumenty i fragmenty XML, ponieważ kod ma tę samą strukturę jako ostatecznego XML.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cfc7-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1cfc7-106">In This Section</span></span>  
  
|<span data-ttu-id="1cfc7-107">Termin</span><span class="sxs-lookup"><span data-stu-id="1cfc7-107">Term</span></span>|<span data-ttu-id="1cfc7-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="1cfc7-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="1cfc7-109">Literały XML — przegląd</span><span class="sxs-lookup"><span data-stu-id="1cfc7-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="1cfc7-110">Wprowadzenie do literałów XML i ich relacje z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cfc7-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="1cfc7-111">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="1cfc7-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="1cfc7-112">W tym artykule opisano sposób użycia wyrażenia osadzone w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="1cfc7-113">Instrukcje: Tworzenie literałów XML</span><span class="sxs-lookup"><span data-stu-id="1cfc7-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="1cfc7-114">W tym artykule opisano, jak utworzyć XML element w kodzie przy użyciu literałów XML.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="1cfc7-115">Biały znak w literałach XML</span><span class="sxs-lookup"><span data-stu-id="1cfc7-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="1cfc7-116">W tym artykule opisano, jak Visual Basic traktuje biały znak w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="1cfc7-117">Literały XML i specyfikacja XML 1.0</span><span class="sxs-lookup"><span data-stu-id="1cfc7-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="1cfc7-118">W tym artykule opisano, jak składnia literał XML w Visual Basic odnosi się do specyfikacji XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="1cfc7-119">Instrukcje: Osadzanie wyrażeń w literałach XML</span><span class="sxs-lookup"><span data-stu-id="1cfc7-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="1cfc7-120">W tym artykule opisano sposób użycia wyrażenia osadzone w literałach XML do tworzenia zawartości w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="1cfc7-121">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="1cfc7-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="1cfc7-122">W tym artykule opisano zasady nazewnictwa elementów XML oraz atrybuty.</span><span class="sxs-lookup"><span data-stu-id="1cfc7-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cfc7-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cfc7-123">See also</span></span>

- [<span data-ttu-id="1cfc7-124">XML</span><span class="sxs-lookup"><span data-stu-id="1cfc7-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
