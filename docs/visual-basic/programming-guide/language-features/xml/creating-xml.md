---
title: Tworzenie XML w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95ab82f2a8ae11b04e3887d5a179931c47346155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="f2f43-102">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2f43-102">Creating XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="f2f43-103">pozwala na użycie *literałów XML* bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f2f43-103"> enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="f2f43-104">Reprezentuje składni literału XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów która jest podobna do składni XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="f2f43-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="f2f43-105">Ułatwia to programowo utworzyć elementy, dokumentów i fragmenty XML, ponieważ kod ma taką samą strukturę jak końcowego XML.</span><span class="sxs-lookup"><span data-stu-id="f2f43-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2f43-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f2f43-106">In This Section</span></span>  
  
|<span data-ttu-id="f2f43-107">Termin</span><span class="sxs-lookup"><span data-stu-id="f2f43-107">Term</span></span>|<span data-ttu-id="f2f43-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="f2f43-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="f2f43-109">Literały XML-Przegląd</span><span class="sxs-lookup"><span data-stu-id="f2f43-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="f2f43-110">Literały XML i ich relacji z wprowadzenie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2f43-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="f2f43-111">Wyrażenia osadzone w XML</span><span class="sxs-lookup"><span data-stu-id="f2f43-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="f2f43-112">Informacje dotyczące używania wyrażenia osadzone w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="f2f43-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="f2f43-113">Porady: tworzenie literałów XML</span><span class="sxs-lookup"><span data-stu-id="f2f43-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="f2f43-114">Opisuje sposób tworzenia elementu XML w kodzie za pomocą literału XML.</span><span class="sxs-lookup"><span data-stu-id="f2f43-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="f2f43-115">Odstęp w literałach XML</span><span class="sxs-lookup"><span data-stu-id="f2f43-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="f2f43-116">Opisuje sposób [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] traktuje odstęp w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="f2f43-116">Describes how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="f2f43-117">Literały XML i XML 1.0 specyfikacji</span><span class="sxs-lookup"><span data-stu-id="f2f43-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="f2f43-118">Opisuje sposób składni literału XML w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] odnosi się do Specyfikacja XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="f2f43-118">Describes how the XML literal syntax in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="f2f43-119">Porady: osadzanie wyrażeń w literałach XML</span><span class="sxs-lookup"><span data-stu-id="f2f43-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="f2f43-120">Informacje dotyczące używania wyrażenia osadzone w literałach XML do tworzenia zawartości w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f2f43-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="f2f43-121">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2f43-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="f2f43-122">W tym artykule opisano zasady nazewnictwa elementów XML oraz atrybuty.</span><span class="sxs-lookup"><span data-stu-id="f2f43-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2f43-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2f43-123">See Also</span></span>  
 [<span data-ttu-id="f2f43-124">XML</span><span class="sxs-lookup"><span data-stu-id="f2f43-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
