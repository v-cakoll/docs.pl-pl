---
title: "Osadzony w dokumencie dyrektywy arkusza stylów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b0d4589dc73b4effeff553e5b7bf5562a7602c2d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="71fc9-102">Osadzony w dokumencie dyrektywy arkusza stylów</span><span class="sxs-lookup"><span data-stu-id="71fc9-102">Style Sheet Directives Embedded in a Document</span></span>
<span data-ttu-id="71fc9-103">Czasami istniejący kod XML zawiera dyrektywy arkusz stylów z `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="71fc9-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="71fc9-104">Program Microsoft Internet Explorer akceptuje, to zamiast `<?xml-stylesheet?>` składni.</span><span class="sxs-lookup"><span data-stu-id="71fc9-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="71fc9-105">Jeśli dane XML zawiera `<?xml:stylesheet?>` dyrektywy, jak przedstawiono w następujących danych próby załadowania tych danych do XML modelu DOM (Document Object) zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="71fc9-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 <span data-ttu-id="71fc9-106">Dzieje się tak dlatego `<?xml:stylesheet?>` jest uznawany za nieprawidłową **ProcessingInstruction** do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="71fc9-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="71fc9-107">Wszelkie **ProcessingInstruction**, zgodnie z przestrzeni nazw w specyfikacji XML, może być tylko nazwy nie dwukropka (NCNames), a nie kwalifikowanej nazwy (QNames).</span><span class="sxs-lookup"><span data-stu-id="71fc9-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>  
  
 <span data-ttu-id="71fc9-108">Z sekcji 6 przestrzeni nazw w specyfikacji XML, efekt o **obciążenia** i **działanie metody LoadXml** metody odpowiadają specyfikacji jest to, że w dokumencie:</span><span class="sxs-lookup"><span data-stu-id="71fc9-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>  
  
-   <span data-ttu-id="71fc9-109">Wszystkie typy elementu i nazwach atrybutów zawierać zero lub średnikami.</span><span class="sxs-lookup"><span data-stu-id="71fc9-109">All element types and attribute names contain either zero or one colon.</span></span>  
  
-   <span data-ttu-id="71fc9-110">Nie nazwy jednostek, ProcessingInstruction elementów docelowych lub nazw w notacji zawierać żadnych dwukropki.</span><span class="sxs-lookup"><span data-stu-id="71fc9-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>  
  
 <span data-ttu-id="71fc9-111">Z `<?xml:stylesheet?>` zawierające dwukropek, możesz teraz narusza reguły w drugim punktor.</span><span class="sxs-lookup"><span data-stu-id="71fc9-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>  
  
 <span data-ttu-id="71fc9-112">Zgodnie z sieci World Wide Web konsorcjum W3C kojarzenie arkusze stylów z dokumentów XML w wersji 1.0 zalecenia, znajdujący się w www.w3.org/TR/xml-stylesheet, instrukcji przetwarzania, aby skojarzyć arkusz stylów XSLT z dokumentu XML jest `<?xml-stylesheet?>`, z łącznikiem zastępowanie dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="71fc9-112">According to the World Wide Web Consortium (W3C) Associating Style Sheets with XML documents Version 1.0 Recommendation, located at www.w3.org/TR/xml-stylesheet, the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71fc9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71fc9-113">See Also</span></span>  
 [<span data-ttu-id="71fc9-114">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="71fc9-114">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
