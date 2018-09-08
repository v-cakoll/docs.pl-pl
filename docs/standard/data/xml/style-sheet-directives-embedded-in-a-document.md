---
title: Dyrektywy dotyczące arkusza stylów osadzone w dokumencie
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65987c5e29d593758b21259d6367202c882df2de
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201832"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="72245-102">Dyrektywy dotyczące arkusza stylów osadzone w dokumencie</span><span class="sxs-lookup"><span data-stu-id="72245-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="72245-103">Od czasu do czasu istniejących XML zawiera dyrektywy arkusz stylów z `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="72245-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="72245-104">Program Microsoft Internet Explorer akceptuje to jako alternatywa `<?xml-stylesheet?>` składni.</span><span class="sxs-lookup"><span data-stu-id="72245-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="72245-105">Gdy dane XML zawierają `<?xml:stylesheet?>` dyrektywy, jak pokazano w poniższym danych próby załadowania tych danych do XML Document Object Model (DOM) zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="72245-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="72245-106">Dzieje się tak dlatego `<?xml:stylesheet?>` jest uznawany za nieprawidłową **ProcessingInstruction** do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="72245-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="72245-107">Wszelkie **ProcessingInstruction**, zgodnie z przestrzeni nazw w specyfikacji XML może zawierać tylko nazwy nie dwukropka (NCNames), w przeciwieństwie kwalifikowanej nazwy (QNames).</span><span class="sxs-lookup"><span data-stu-id="72245-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="72245-108">Od 6 sekcji przestrzeni nazw w specyfikacji XML, mających wpływ **obciążenia** i **działanie metody LoadXml** metody są zgodne ze specyfikacją jest to, że w dokumencie:</span><span class="sxs-lookup"><span data-stu-id="72245-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="72245-109">Wszystkie typy elementu i nazwach atrybutów zawiera zero lub dwukropka.</span><span class="sxs-lookup"><span data-stu-id="72245-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="72245-110">Nie nazwy jednostek, ProcessingInstruction elementów docelowych lub nazw w notacji zawierają wszystkie dwukropki.</span><span class="sxs-lookup"><span data-stu-id="72245-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="72245-111">Za pomocą `<?xml:stylesheet?>` zawierające dwukropek, możesz teraz naruszają reguły w drugim punktor.</span><span class="sxs-lookup"><span data-stu-id="72245-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="72245-112">Zgodnie z World Wide Web Consortium (W3C) [kojarzenie arkusze stylów, za pomocą XML dokumenty, wersja 1.0 zalecenie](https://www.w3.org/TR/xml-stylesheet/), jest instrukcja przetwarzania, aby skojarzyć arkusz stylów XSLT z dokumentu XML `<?xml-stylesheet?>`, za pomocą kreska, zastępując z dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="72245-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="72245-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72245-113">See also</span></span>

- [<span data-ttu-id="72245-114">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="72245-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
