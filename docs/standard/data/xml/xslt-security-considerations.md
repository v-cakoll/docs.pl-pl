---
title: "Zagadnienia dotyczące zabezpieczeń XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fea695be-617c-4977-9567-140e820436fc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 560a0866a526caf4c8fe129209d0077374306a9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń XSLT
Język XSLT zawiera bogaty zestaw funkcji, które zapewniają dużą możliwościach i elastyczności. Zawiera wiele funkcji, które jest to przydatne, mogą być również wykorzystywane przez zewnętrznych źródeł. Aby można było używać bezpiecznie XSLT, muszą zrozumieć typy problemy z zabezpieczeniami, które użytkowania XSLT i podstawowe strategie, których można użyć, aby ograniczyć te zagrożenia.  
  
## <a name="xslt-extensions"></a>Rozszerzenia XSLT  
 Dwa popularne rozszerzenia XSLT są obiektami skryptów i rozszerzenia arkusza stylów. Te rozszerzenia umożliwiają procesorze XSLT do wykonywania kodu.  
  
-   Obiekty rozszerzenia dodać możliwości programowania do transformacji XSL.  
  
-   Skrypty można ją osadzić w arkuszu stylów przy użyciu `msxsl:script` elementu rozszerzenia.  
  
### <a name="extension-objects"></a>Rozszerzenia obiektów  
 Obiekty rozszerzenia są dodawane przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Zestaw uprawnień FullTrust jest wymagany do obsługi obiektów rozszerzeń. Dzięki temu, że podwyższenie poziomu uprawnień nie odbywa się podczas wykonywania kodu obiektu rozszerzenia. Próba wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody bez powoduje uprawnień FullTrust został zgłoszony wyjątek zabezpieczeń.  
  
### <a name="style-sheet-scripts"></a>Skrypty arkusza stylów  
 Skrypty mogą być osadzone w arkuszu stylów przy użyciu `msxsl:script` elementu rozszerzenia. Obsługa skryptów jest funkcją opcjonalną na <xref:System.Xml.Xsl.XslCompiledTransform> klasy, która jest domyślnie wyłączona. Może być włączona obsługa skryptów przez ustawienie <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> właściwości `true` i przekazywanie <xref:System.Xml.Xsl.XsltSettings> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
#### <a name="guidelines"></a>Wytyczne dotyczące  
 Włącz wykonywanie skryptów, tylko gdy arkusz stylów pochodzi z zaufanego źródła. Jeśli nie można zweryfikować źródła arkusza stylów lub arkusz stylów nie pochodzi z zaufanego źródła, Przekaż `null` argumentu ustawienia XSLT.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Język XSLT zawiera funkcje, takie jak `xsl:import`, `xsl:include`, lub `document()` funkcja, gdy procesor musi rozpoznać odwołań do identyfikatora URI. <xref:System.Xml.XmlResolver> Klasa jest używana do rozpoznawania zasobów zewnętrznych. Zasoby zewnętrzne mogą muszą zostać rozwiązane w dwóch następujących przypadków:  
  
-   W przypadku kompilowania kodu arkusz stylów <xref:System.Xml.XmlResolver> służy do `xsl:import` i `xsl:include` rozpoznawania.  
  
-   Podczas wykonywania transformacji, <xref:System.Xml.XmlResolver> jest używany do rozpoznawania `document()` funkcji.  
  
    > [!NOTE]
    >  `document()` Funkcja jest domyślnie wyłączony na <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Ta funkcja może być włączona <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> właściwości `true` i przekazywanie <xref:System.Xml.Xsl.XsltSettings> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody każdego obejmują przeciążenia, które akceptują <xref:System.Xml.XmlResolver> jako jeden z jego argumentów. Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, domyślnie <xref:System.Xml.XmlUrlResolver> bez poświadczeń jest używany.  
  
#### <a name="guidelines"></a>Wytyczne dotyczące  
 Włącz `document()` działa tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła.  
  
 Na poniższej liście opisano, kiedy można określić <xref:System.Xml.XmlResolver> obiektu:  
  
-   Jeśli proces XSLT wymaga dostępu do zasobu sieciowego, która wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> niezbędne poświadczenia.  
  
-   Jeśli chcesz ograniczyć zasoby, do których dostęp procesu XSLT, możesz użyć <xref:System.Xml.XmlSecureResolver> ustawienie odpowiednie uprawnienia. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli trzeba otworzyć zasobu, która kontroluje, lub niezaufanych.  
  
-   Jeśli chcesz dostosować zachowanie, można zaimplementować własne <xref:System.Xml.XmlResolver> klasy i użyć go do rozwiązania zasobów.  
  
-   Jeśli chcesz upewnić się, że nie zewnętrzne zasoby są dostępne, można określić `null` dla <xref:System.Xml.XmlResolver> argumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [Zabezpieczenia dostępu kodu](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)
