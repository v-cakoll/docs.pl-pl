---
title: Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 58407d5f0c6e602af15f5b19b9a19cc6379b9af7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710287"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
Podczas transformacji XSLT występuje kilka razy, gdy konieczne jest rozwiązanie zasobów zewnętrznych.  
  
## <a name="using-the-xmlresolver-class"></a>Korzystanie z klasy XmlResolver  
 Klasa <xref:System.Xml.XmlResolver> jest używana do rozpoznawania zasobów zewnętrznych. W poniższej tabeli opisano, kiedy <xref:System.Xml.XmlResolver> jest uwzględniana podczas przetwarzania XSLT.  
  
|Zadanie XSLT|Do czego służy element XmlResolver|  
|---------------|--------------------------------------|  
|Kompiluj arkusz stylów.|Rozpoznanie identyfikatora URI arkusza stylów.<br /><br /> \- i -<br /><br /> Rozpoznaj odwołania do identyfikatorów URI w dowolnych `xsl:import` lub `xsl:include` elementów.|  
|Wykonaj arkusz stylów.|Rozpoznanie identyfikatora URI dokumentu kontekstowego.<br /><br /> \- i -<br /><br /> Rozwiąż odwołania do identyfikatorów URI w dowolnych funkcjach `document()` XSLT.|  
  
 Metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> obejmują przeciążenia przyjmujące obiekt <xref:System.Xml.XmlResolver> jako jeden z argumentów. Jeśli nie określono <xref:System.Xml.XmlResolver>, zostanie użyta domyślna <xref:System.Xml.XmlUrlResolver> bez poświadczeń.  
  
 Na poniższej liście opisano, kiedy warto określić obiekt <xref:System.Xml.XmlResolver>:  
  
- Jeśli proces XSLT musi uzyskać dostęp do zasobu sieciowego, który wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> z niezbędnymi poświadczeniami.  
  
- Jeśli chcesz ograniczyć zasoby, do których proces XSLT może uzyskać dostęp, możesz użyć <xref:System.Xml.XmlSecureResolver> z prawidłowym zestawem uprawnień. Użyj klasy <xref:System.Xml.XmlSecureResolver>, jeśli konieczne jest otwarcie zasobu, który nie jest kontrolowany lub że nie jest zaufany.  
  
- Aby dostosować zachowanie, można zaimplementować własną klasę <xref:System.Xml.XmlResolver> i używać jej do rozwiązywania zasobów.  
  
- Jeśli chcesz się upewnić, że nie ma dostępu do zasobów zewnętrznych, możesz określić `null` dla argumentu <xref:System.Xml.XmlResolver>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje arkusz stylów, który jest przechowywany w zasobów sieciowych. Obiekt <xref:System.Xml.XmlUrlResolver> określa poświadczenia niezbędne do uzyskania dostępu do arkusza stylów.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
