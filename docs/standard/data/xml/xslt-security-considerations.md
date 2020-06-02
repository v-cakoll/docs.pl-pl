---
title: Zagadnienia dotyczące bezpieczeństwa danych XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: 81db764016607ebe6facfc530dbb2bac8e6b8cfe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282514"
---
# <a name="xslt-security-considerations"></a>Zagadnienia dotyczące bezpieczeństwa danych XSLT
Język XSLT oferuje bogaty zestaw funkcji, które zapewniają doskonałą wydajność i elastyczność. Zawiera ona wiele funkcji, które mogą być również wykorzystywane przez źródła zewnętrzne. Aby bezpiecznie używać XSLT, należy zrozumieć typy problemów z zabezpieczeniami, które powstają podczas korzystania z języka XSLT, oraz podstawowe strategie, których można użyć w celu ograniczenia tych zagrożeń.  
  
## <a name="xslt-extensions"></a>Rozszerzenia XSLT  
 Dwa popularne rozszerzenia XSLT to skrypty arkusza stylów i obiekty rozszerzeń. Te rozszerzenia umożliwiają procesorowi XSLT wykonywanie kodu.  
  
- Obiekty rozszerzeń dodają funkcje programistyczne do transformacji XSL.  
  
- Skrypty można osadzić w arkuszu stylów przy użyciu `msxsl:script` elementu rozszerzenia.  
  
### <a name="extension-objects"></a>Obiekty rozszerzeń  
 Obiekty rozszerzeń są dodawane przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Zestaw uprawnień FullTrust jest wymagany do obsługi obiektów rozszerzeń. Dzięki temu podniesienie uprawnień nie następuje, gdy zostanie wykonany kod obiektu rozszerzenia. Próba wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody bez uprawnień FullTrust powoduje zgłoszenie wyjątku zabezpieczeń.  
  
### <a name="style-sheet-scripts"></a>Skrypty arkusza stylów  
 Skrypty można osadzić w arkuszu stylów przy użyciu `msxsl:script` elementu rozszerzenia. Obsługa skryptów jest opcjonalną funkcją w <xref:System.Xml.Xsl.XslCompiledTransform> klasie, która jest domyślnie wyłączona. Obsługę skryptów można włączyć przez ustawienie <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> właściwości na `true` i przekazanie <xref:System.Xml.Xsl.XsltSettings> obiektu do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
#### <a name="guidelines"></a>Wytyczne  
 Włącz obsługę skryptów tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła. Jeśli nie możesz zweryfikować źródła arkusza stylów lub jeśli arkusz stylów nie pochodzi z zaufanego źródła, Przekaż `null` go do argumentu ustawienia XSLT.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Język XSLT zawiera funkcje, takie jak `xsl:import` , `xsl:include` , lub `document()` Funkcja, gdzie procesor wymaga rozpoznania odwołań do identyfikatorów URI. <xref:System.Xml.XmlResolver>Klasa jest używana do rozpoznawania zasobów zewnętrznych. Zasoby zewnętrzne mogą wymagać rozwiązania w następujących dwóch przypadkach:  
  
- Podczas kompilowania arkusza stylów, <xref:System.Xml.XmlResolver> jest używany do `xsl:import` rozpoznawania i `xsl:include` rozwiązywania.  
  
- Podczas wykonywania transformacji <xref:System.Xml.XmlResolver> jest używana do rozpoznawania `document()` funkcji.  
  
    > [!NOTE]
    > `document()`Funkcja jest domyślnie wyłączona w <xref:System.Xml.Xsl.XslCompiledTransform> klasie. Tę funkcję można włączyć przez ustawienie <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> właściwości na `true` i przekazanie <xref:System.Xml.Xsl.XsltSettings> obiektu do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
 Każdy z tych <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metod obejmuje przeciążenia, które akceptują <xref:System.Xml.XmlResolver> jako jeden z argumentów. Jeśli <xref:System.Xml.XmlResolver> nie jest określony, <xref:System.Xml.XmlUrlResolver> zostanie użyta wartość domyślna bez poświadczeń.  
  
#### <a name="guidelines"></a>Wytyczne  
 Włącz `document()` funkcję tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła.  
  
 Na poniższej liście opisano, kiedy warto określić <xref:System.Xml.XmlResolver> obiekt:  
  
- Jeśli proces XSLT musi uzyskać dostęp do zasobu sieciowego, który wymaga uwierzytelnienia, możesz użyć <xref:System.Xml.XmlResolver> z niezbędnymi poświadczeniami.  
  
- Jeśli chcesz ograniczyć zasoby, do których proces XSLT może uzyskać dostęp, możesz użyć <xref:System.Xml.XmlSecureResolver> z prawidłowym zestawem uprawnień. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli konieczne jest otwarcie zasobu, którego nie kontrolujesz lub który nie jest zaufany.  
  
- Jeśli chcesz dostosować zachowanie, możesz zaimplementować własną <xref:System.Xml.XmlResolver> klasę i używać jej do rozwiązywania zasobów.  
  
- Jeśli chcesz się upewnić, że nie ma dostępu do zasobów zewnętrznych, możesz określić `null` dla tego <xref:System.Xml.XmlResolver> argumentu.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](xslt-transformations.md)
- [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](resolving-external-resources-during-xslt-processing.md)
- [Zabezpieczenia dostępu kodu](../../../framework/misc/code-access-security.md)
