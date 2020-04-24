---
title: Dyrektywy dotyczące arkusza stylów osadzone w dokumencie
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 19e25ab7262bb006144eea71e74bd7454066b3f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710157"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="7364a-102">Dyrektywy dotyczące arkusza stylów osadzone w dokumencie</span><span class="sxs-lookup"><span data-stu-id="7364a-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="7364a-103">Czasami istniejący kod XML zawiera dyrektywę arkusz stylów `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="7364a-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="7364a-104">Program Microsoft Internet Explorer akceptuje to jako alternatywę dla `<?xml-stylesheet?>` składni.</span><span class="sxs-lookup"><span data-stu-id="7364a-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="7364a-105">Gdy dane XML zawierają `<?xml:stylesheet?>` dyrektywę, jak pokazano w poniższych danych, próba załadowania tych danych do pliku XML Document Object Model (dom) zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7364a-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="7364a-106">Dzieje się tak, `<?xml:stylesheet?>` ponieważ jest uznawany za nieprawidłową **ProcessingInstruction** do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="7364a-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="7364a-107">Każdy **ProcessingInstruction**, zgodnie z przestrzeniami nazw w specyfikacji XML, może mieć tylko nazwy bez dwukropka (NCNames), w przeciwieństwie do nazw kwalifikowanych (QName).</span><span class="sxs-lookup"><span data-stu-id="7364a-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="7364a-108">Z sekcji 6 przestrzeni nazw w specyfikacji XML, efekt zastosowania metod **Load** i **LoadXml** jest zgodny ze specyfikacją w dokumencie:</span><span class="sxs-lookup"><span data-stu-id="7364a-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="7364a-109">Wszystkie typy elementów i nazwy atrybutów zawierają jeden dwukropek.</span><span class="sxs-lookup"><span data-stu-id="7364a-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="7364a-110">Brak nazw jednostek, obiektów docelowych ProcessingInstruction ani nazw notacji zawierających dowolne dwukropki.</span><span class="sxs-lookup"><span data-stu-id="7364a-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="7364a-111">Z `<?xml:stylesheet?>` zawierającym dwukropek, nastąpi naruszenie reguły w drugim punkcie.</span><span class="sxs-lookup"><span data-stu-id="7364a-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="7364a-112">Zgodnie z zaleceniami organizacja World Wide Web Consortium (W3C) [kojarzenia arkuszy stylów z dokumentami XML w wersji 1,0 zalecenie](https://www.w3.org/TR/xml-stylesheet/), instrukcja przetwarzania, aby skojarzyć arkusz stylów XSLT z dokumentem XML `<?xml-stylesheet?>`, z kreską zastępującą dwukropek.</span><span class="sxs-lookup"><span data-stu-id="7364a-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="7364a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7364a-113">See also</span></span>

- [<span data-ttu-id="7364a-114">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="7364a-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
