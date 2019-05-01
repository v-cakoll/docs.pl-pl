---
title: Zagadnienia dotyczące bezpieczeństwa danych XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 526805dff9fc59ed317a38b2512c8a97a711227a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026669"
---
# <a name="xslt-security-considerations"></a>Zagadnienia dotyczące bezpieczeństwa danych XSLT
Język XSLT ma bogaty zestaw funkcji, które zapewniają dużą moc i elastyczność. Obejmuje wiele funkcji, które jest to przydatne, również może zostać wykorzystana przez zewnętrznych źródeł. Aby można było używać bezpiecznie XSLT, należy poznać rodzaje problemów z zabezpieczeniami, które powstają, gdy za pomocą XSLT i podstawowe strategie, których można używać, aby ograniczyć te zagrożenia.  
  
## <a name="xslt-extensions"></a>Rozszerzeń XSLT  
 Dwie popularne rozszerzenia XSLT są obiektami skryptów i rozszerzenia arkusza stylów. Te rozszerzenia umożliwiają procesora XSLT do wykonywania kodu.  
  
- Obiekty rozszerzeń Dodaj funkcje programowania do przekształcenia XSL.  
  
- Skrypty mogą być osadzone w arkuszu stylów za pomocą `msxsl:script` elementu rozszerzenia.  
  
### <a name="extension-objects"></a>Obiekty rozszerzeń  
 Obiekty rozszerzeń są dodawane przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Zestaw uprawnień FullTrust jest wymagany do obsługi obiekty rozszerzeń. Daje to gwarancję, że podniesienie uprawnień nie odbywa się podczas wykonywania kodu obiektowego rozszerzenia. Próba wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody bez uprawnień FullTrust powoduje wyjątek zabezpieczeń, zgłaszane.  
  
### <a name="style-sheet-scripts"></a>Skryptów arkusza stylów  
 Skrypty mogą być osadzone w arkuszu stylów przy użyciu `msxsl:script` elementu rozszerzenia. Obsługa skryptów jest opcjonalną funkcją na <xref:System.Xml.Xsl.XslCompiledTransform> klasę, która jest domyślnie wyłączona. Może być włączona obsługa skryptów przez ustawienie <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> właściwości `true` i przekazanie <xref:System.Xml.Xsl.XsltSettings> obiekt <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
#### <a name="guidelines"></a>Wytyczne dotyczące  
 Włączenie obsługi skryptów, tylko jeśli arkusz stylów pochodzi z zaufanego źródła. Jeśli nie można zweryfikować źródła arkusza stylów lub arkusz stylów nie pochodzi z zaufanego źródła, Przekaż `null` dla argumentu ustawień XSLT.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Język XSLT zawiera funkcje, takie jak `xsl:import`, `xsl:include`, lub `document()` funkcji, których wymaga procesor do rozpoznawania odwołań do identyfikatora URI. <xref:System.Xml.XmlResolver> Klasy jest używany do rozpoznawania zasobów zewnętrznych. Zasoby zewnętrzne może być konieczne jest rozpoznawany w dwóch przypadkach:  
  
- Podczas kompilowania arkusz stylów <xref:System.Xml.XmlResolver> służy do `xsl:import` i `xsl:include` rozwiązania.  
  
- Podczas wykonywania przekształcenia, <xref:System.Xml.XmlResolver> jest używany do rozpoznawania `document()` funkcji.  
  
    > [!NOTE]
    >  `document()` Funkcja jest domyślnie wyłączona na <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Ta funkcja może być włączona <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> właściwości `true` i przekazanie <xref:System.Xml.Xsl.XsltSettings> obiekt <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody każdego obejmują przeciążenia, które akceptują <xref:System.Xml.XmlResolver> jako jeden z jej argumentów. Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, domyślnie <xref:System.Xml.XmlUrlResolver> bez poświadczeń jest używany.  
  
#### <a name="guidelines"></a>Wytyczne dotyczące  
 Włącz `document()` działa tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła.  
  
 Na poniższej liście opisano, kiedy warto określić <xref:System.Xml.XmlResolver> obiektu:  
  
- Jeśli proces XSLT musi uzyskać dostęp do zasobów sieciowych, która wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> niezbędne poświadczenia.  
  
- Jeśli chcesz ograniczyć zasoby, które proces XSLT można uzyskać dostępu, możesz użyć <xref:System.Xml.XmlSecureResolver> with odpowiednie uprawnienie jest ustawiona. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli trzeba otworzyć zasób, które nie mają kontroli nad lub które nie jest zaufany.  
  
- Jeśli chcesz dostosować zachowanie, możesz zaimplementować własną <xref:System.Xml.XmlResolver> klasy i używane w celu rozwiązania zasobów.  
  
- Jeśli chcesz upewnić się, że są dostępne nie zasoby zewnętrzne, można określić `null` dla <xref:System.Xml.XmlResolver> argumentu.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Zabezpieczenia dostępu kodu](../../../../docs/framework/misc/code-access-security.md)
