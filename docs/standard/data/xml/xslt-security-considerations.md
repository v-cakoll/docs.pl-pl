---
title: Zagadnienia dotyczące bezpieczeństwa danych XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: e6e490c0f637aace57dacc88ef49cc9be87532cd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709689"
---
# <a name="xslt-security-considerations"></a>Zagadnienia dotyczące bezpieczeństwa danych XSLT
Język XSLT oferuje bogaty zestaw funkcji, które zapewniają doskonałą wydajność i elastyczność. Zawiera ona wiele funkcji, które mogą być również wykorzystywane przez źródła zewnętrzne. Aby bezpiecznie używać XSLT, należy zrozumieć typy problemów z zabezpieczeniami, które powstają podczas korzystania z języka XSLT, oraz podstawowe strategie, których można użyć w celu ograniczenia tych zagrożeń.  
  
## <a name="xslt-extensions"></a>Rozszerzenia XSLT  
 Dwa popularne rozszerzenia XSLT to skrypty arkusza stylów i obiekty rozszerzeń. Te rozszerzenia umożliwiają procesorowi XSLT wykonywanie kodu.  
  
- Obiekty rozszerzeń dodają funkcje programistyczne do transformacji XSL.  
  
- Skrypty można osadzić w arkuszu stylów przy użyciu elementu `msxsl:script` rozszerzenia.  
  
### <a name="extension-objects"></a>Obiekty rozszerzeń  
 Obiekty rozszerzeń są dodawane przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Zestaw uprawnień FullTrust jest wymagany do obsługi obiektów rozszerzeń. Dzięki temu podniesienie uprawnień nie następuje, gdy zostanie wykonany kod obiektu rozszerzenia. Próba wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody bez uprawnień FullTrust powoduje zgłoszenie wyjątku zabezpieczeń.  
  
### <a name="style-sheet-scripts"></a>Skrypty arkusza stylów  
 Skrypty można osadzić w arkuszu stylów przy użyciu elementu `msxsl:script` rozszerzenia. Obsługa skryptów jest opcjonalną funkcją w <xref:System.Xml.Xsl.XslCompiledTransform> klasie, która jest domyślnie wyłączona. Obsługę skryptów <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> można włączyć przez ustawienie właściwości na `true` i przekazanie <xref:System.Xml.Xsl.XsltSettings> obiektu do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
#### <a name="guidelines"></a>Wytyczne  
 Włącz obsługę skryptów tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła. Jeśli nie możesz zweryfikować źródła arkusza stylów lub jeśli arkusz stylów nie pochodzi z zaufanego źródła, przekaż go `null` do ARGUMENTU ustawienia XSLT.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Język XSLT zawiera funkcje, takie jak `xsl:import`, `xsl:include`, lub `document()` funkcja, gdzie procesor wymaga rozpoznania odwołań do identyfikatorów URI. <xref:System.Xml.XmlResolver> Klasa jest używana do rozpoznawania zasobów zewnętrznych. Zasoby zewnętrzne mogą wymagać rozwiązania w następujących dwóch przypadkach:  
  
- Podczas kompilowania arkusza stylów, <xref:System.Xml.XmlResolver> jest używany do `xsl:import` rozpoznawania i `xsl:include` rozwiązywania.  
  
- Podczas wykonywania transformacji <xref:System.Xml.XmlResolver> jest używana do rozpoznawania `document()` funkcji.  
  
    > [!NOTE]
    > `document()` Funkcja jest domyślnie wyłączona w <xref:System.Xml.Xsl.XslCompiledTransform> klasie. Tę funkcję <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> można włączyć przez ustawienie właściwości na `true` i przekazanie <xref:System.Xml.Xsl.XsltSettings> obiektu do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
 Każdy <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> z <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> tych metod obejmuje przeciążenia, które akceptują <xref:System.Xml.XmlResolver> jako jeden z argumentów. Jeśli nie <xref:System.Xml.XmlResolver> jest określony, zostanie użyta <xref:System.Xml.XmlUrlResolver> wartość domyślna bez poświadczeń.  
  
#### <a name="guidelines"></a>Wytyczne  
 Włącz `document()` funkcję tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła.  
  
 Na poniższej liście opisano, kiedy warto określić <xref:System.Xml.XmlResolver> obiekt:  
  
- Jeśli proces XSLT musi uzyskać dostęp do zasobu sieciowego, który wymaga uwierzytelnienia, możesz użyć <xref:System.Xml.XmlResolver> z niezbędnymi poświadczeniami.  
  
- Jeśli chcesz ograniczyć zasoby, do których proces XSLT może uzyskać dostęp, możesz użyć <xref:System.Xml.XmlSecureResolver> z prawidłowym zestawem uprawnień. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli konieczne jest otwarcie zasobu, którego nie kontrolujesz lub który nie jest zaufany.  
  
- Jeśli chcesz dostosować zachowanie, możesz zaimplementować własną <xref:System.Xml.XmlResolver> klasę i używać jej do rozwiązywania zasobów.  
  
- Jeśli chcesz się upewnić, że nie ma dostępu do zasobów zewnętrznych, możesz `null` określić dla <xref:System.Xml.XmlResolver> tego argumentu.  
  
## <a name="see-also"></a>Zobacz też

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Zabezpieczenia dostępu kodu](../../../../docs/framework/misc/code-access-security.md)
