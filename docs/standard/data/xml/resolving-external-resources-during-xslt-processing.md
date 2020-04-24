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
 <xref:System.Xml.XmlResolver> Klasa jest używana do rozpoznawania zasobów zewnętrznych. W poniższej tabeli opisano, <xref:System.Xml.XmlResolver> Kiedy zostanie ona uwzględniona podczas przetwarzania XSLT.  
  
|Zadanie XSLT|Do czego służy element XmlResolver|  
|---------------|--------------------------------------|  
|Kompiluj arkusz stylów.|Rozpoznanie identyfikatora URI arkusza stylów.<br /><br /> lub<br /><br /> Rozpoznaj odwołania do identyfikatorów `xsl:import` URI `xsl:include` w dowolnych lub elementach.|  
|Wykonaj arkusz stylów.|Rozpoznanie identyfikatora URI dokumentu kontekstowego.<br /><br /> lub<br /><br /> Rozpoznawanie odwołań do identyfikatorów URI w `document()` dowolnych funkcjach XSLT.|  
  
 Metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> obejmują przeciążenia przyjmujące <xref:System.Xml.XmlResolver> obiekt jako jeden z argumentów. Jeśli nie <xref:System.Xml.XmlResolver> jest określony, zostanie użyta <xref:System.Xml.XmlUrlResolver> wartość domyślna bez poświadczeń.  
  
 Na poniższej liście opisano, kiedy warto określić <xref:System.Xml.XmlResolver> obiekt:  
  
- Jeśli proces XSLT musi uzyskać dostęp do zasobu sieciowego, który wymaga uwierzytelnienia, możesz użyć <xref:System.Xml.XmlResolver> z niezbędnymi poświadczeniami.  
  
- Jeśli chcesz ograniczyć zasoby, do których proces XSLT może uzyskać dostęp, możesz użyć <xref:System.Xml.XmlSecureResolver> z prawidłowym zestawem uprawnień. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli konieczne jest otwarcie zasobu, którego nie kontrolujesz lub który nie jest zaufany.  
  
- Jeśli chcesz dostosować zachowanie, możesz zaimplementować własną <xref:System.Xml.XmlResolver> klasę i używać jej do rozwiązywania zasobów.  
  
- Jeśli chcesz się upewnić, że nie ma dostępu do zasobów zewnętrznych, możesz `null` określić dla <xref:System.Xml.XmlResolver> tego argumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje arkusz stylów, który jest przechowywany w zasobów sieciowych. <xref:System.Xml.XmlUrlResolver> Obiekt określa poświadczenia niezbędne do uzyskania dostępu do arkusza stylów.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
