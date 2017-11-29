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
ms.openlocfilehash: 8c5cfcc9f35e4a07e9426a4dd24c1e2f04985f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Osadzony w dokumencie dyrektywy arkusza stylów
Czasami istniejący kod XML zawiera dyrektywy arkusz stylów z `<?xml:stylesheet?>`. Program Microsoft Internet Explorer akceptuje, to zamiast `<?xml-stylesheet?>` składni. Jeśli dane XML zawiera `<?xml:stylesheet?>` dyrektywy, jak przedstawiono w następujących danych próby załadowania tych danych do XML modelu DOM (Document Object) zgłasza wyjątek.  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 Dzieje się tak dlatego `<?xml:stylesheet?>` jest uznawany za nieprawidłową **ProcessingInstruction** do modelu DOM. Wszelkie **ProcessingInstruction**, zgodnie z przestrzeni nazw w specyfikacji XML, może być tylko nazwy nie dwukropka (NCNames), a nie kwalifikowanej nazwy (QNames).  
  
 Z sekcji 6 przestrzeni nazw w specyfikacji XML, efekt o **obciążenia** i **działanie metody LoadXml** metody odpowiadają specyfikacji jest to, że w dokumencie:  
  
-   Wszystkie typy elementu i nazwach atrybutów zawierać zero lub średnikami.  
  
-   Nie nazwy jednostek, ProcessingInstruction elementów docelowych lub nazw w notacji zawierać żadnych dwukropki.  
  
 Z `<?xml:stylesheet?>` zawierające dwukropek, możesz teraz narusza reguły w drugim punktor.  
  
 Zgodnie z sieci World Wide Web konsorcjum W3C kojarzenie arkusze stylów z dokumentów XML w wersji 1.0 zalecenia, znajdujący się w www.w3.org/TR/xml-stylesheet, instrukcji przetwarzania, aby skojarzyć arkusz stylów XSLT z dokumentu XML jest `<?xml-stylesheet?>`, z łącznikiem zastępowanie dwukropkiem.  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
