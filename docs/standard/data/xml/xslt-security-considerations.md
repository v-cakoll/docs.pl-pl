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
  
- Skrypty można osadzić w arkuszu stylów przy użyciu elementu rozszerzenia `msxsl:script`.  
  
### <a name="extension-objects"></a>Obiekty rozszerzeń  
 Obiekty rozszerzeń są dodawane za pomocą metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Zestaw uprawnień FullTrust jest wymagany do obsługi obiektów rozszerzeń. Dzięki temu podniesienie uprawnień nie następuje, gdy zostanie wykonany kod obiektu rozszerzenia. Próba wywołania metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> bez uprawnień FullTrust powoduje zgłoszenie wyjątku zabezpieczeń.  
  
### <a name="style-sheet-scripts"></a>Skrypty arkusza stylów  
 Skrypty można osadzić w arkuszu stylów przy użyciu elementu rozszerzenia `msxsl:script`. Obsługa skryptów jest opcjonalną funkcją w klasie <xref:System.Xml.Xsl.XslCompiledTransform>, która jest domyślnie wyłączona. Można włączyć obsługę skryptów przez ustawienie właściwości <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> na `true` i przekazanie obiektu <xref:System.Xml.Xsl.XsltSettings> do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
#### <a name="guidelines"></a>Wytyczne dotyczące  
 Włącz obsługę skryptów tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła. Jeśli nie możesz zweryfikować źródła arkusza stylów lub jeśli arkusz stylów nie pochodzi z zaufanego źródła, Przekaż `null` dla argumentu ustawienia XSLT.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Język XSLT zawiera funkcje, takie jak `xsl:import`, `xsl:include`lub funkcja `document()`, gdzie procesor wymaga rozpoznania odwołań do identyfikatorów URI. Klasa <xref:System.Xml.XmlResolver> jest używana do rozpoznawania zasobów zewnętrznych. Zasoby zewnętrzne mogą wymagać rozwiązania w następujących dwóch przypadkach:  
  
- Podczas kompilowania arkusza stylów <xref:System.Xml.XmlResolver> jest używany do rozpoznawania `xsl:import` i `xsl:include`.  
  
- Podczas wykonywania transformacji <xref:System.Xml.XmlResolver> jest używana do rozpoznawania funkcji `document()`.  
  
    > [!NOTE]
    > Funkcja `document()` jest domyślnie wyłączona w klasie <xref:System.Xml.Xsl.XslCompiledTransform>. Tę funkcję można włączyć przez ustawienie właściwości <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> na `true` i przekazanie obiektu <xref:System.Xml.Xsl.XsltSettings> do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
 Metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> obejmują przeciążenia, które akceptują <xref:System.Xml.XmlResolver> jako jeden z argumentów. Jeśli nie określono <xref:System.Xml.XmlResolver>, zostanie użyta domyślna <xref:System.Xml.XmlUrlResolver> bez poświadczeń.  
  
#### <a name="guidelines"></a>Wytyczne dotyczące  
 Włącz funkcję `document()` tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła.  
  
 Na poniższej liście opisano, kiedy warto określić obiekt <xref:System.Xml.XmlResolver>:  
  
- Jeśli proces XSLT musi uzyskać dostęp do zasobu sieciowego, który wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> z niezbędnymi poświadczeniami.  
  
- Jeśli chcesz ograniczyć zasoby, do których proces XSLT może uzyskać dostęp, możesz użyć <xref:System.Xml.XmlSecureResolver> z prawidłowym zestawem uprawnień. Użyj klasy <xref:System.Xml.XmlSecureResolver>, jeśli konieczne jest otwarcie zasobu, który nie jest kontrolowany lub że nie jest zaufany.  
  
- Aby dostosować zachowanie, można zaimplementować własną klasę <xref:System.Xml.XmlResolver> i używać jej do rozwiązywania zasobów.  
  
- Jeśli chcesz się upewnić, że nie ma dostępu do zasobów zewnętrznych, możesz określić `null` dla argumentu <xref:System.Xml.XmlResolver>.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Zabezpieczenia dostępu kodu](../../../../docs/framework/misc/code-access-security.md)
