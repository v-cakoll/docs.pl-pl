---
title: Tworzenie XML w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 46f9174e78cc67c1e352d02ac6b5038f5da01086
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504672"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="7433a-102">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7433a-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="7433a-103">Visual Basic umożliwia użycie *literałów XML* bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7433a-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="7433a-104">Literał składnia XML przedstawia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów która jest podobna do składni XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="7433a-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="7433a-105">Ta funkcja ułatwia programistycznym tworzeniu elementów, dokumenty i fragmenty XML, ponieważ kod ma tę samą strukturę jako ostatecznego XML.</span><span class="sxs-lookup"><span data-stu-id="7433a-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7433a-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7433a-106">In This Section</span></span>  
  
|<span data-ttu-id="7433a-107">Termin</span><span class="sxs-lookup"><span data-stu-id="7433a-107">Term</span></span>|<span data-ttu-id="7433a-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="7433a-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="7433a-109">Literały XML — przegląd</span><span class="sxs-lookup"><span data-stu-id="7433a-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="7433a-110">Wprowadzenie do literałów XML i ich relacje z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7433a-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="7433a-111">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="7433a-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="7433a-112">W tym artykule opisano sposób użycia wyrażenia osadzone w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="7433a-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="7433a-113">Instrukcje: tworzenie literałów XML</span><span class="sxs-lookup"><span data-stu-id="7433a-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="7433a-114">W tym artykule opisano, jak utworzyć XML element w kodzie przy użyciu literałów XML.</span><span class="sxs-lookup"><span data-stu-id="7433a-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="7433a-115">Biały znak w literałach XML</span><span class="sxs-lookup"><span data-stu-id="7433a-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="7433a-116">W tym artykule opisano, jak Visual Basic traktuje biały znak w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="7433a-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="7433a-117">Literały XML i specyfikacja XML 1.0</span><span class="sxs-lookup"><span data-stu-id="7433a-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="7433a-118">W tym artykule opisano, jak składnia literał XML w Visual Basic odnosi się do specyfikacji XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="7433a-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="7433a-119">Instrukcje: osadzanie wyrażeń w literałach XML</span><span class="sxs-lookup"><span data-stu-id="7433a-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="7433a-120">W tym artykule opisano sposób użycia wyrażenia osadzone w literałach XML do tworzenia zawartości w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7433a-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="7433a-121">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="7433a-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="7433a-122">W tym artykule opisano zasady nazewnictwa elementów XML oraz atrybuty.</span><span class="sxs-lookup"><span data-stu-id="7433a-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7433a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7433a-123">See Also</span></span>  
 [<span data-ttu-id="7433a-124">XML</span><span class="sxs-lookup"><span data-stu-id="7433a-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
