---
title: Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: d38aea1a54c93b00ec14c6aac7ed11ceba288f7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291503"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
Podczas transformacji XSLT występuje kilka razy, gdy konieczne jest rozwiązanie zasobów zewnętrznych.  
  
## <a name="using-the-xmlresolver-class"></a>Korzystanie z klasy XmlResolver  
 <xref:System.Xml.XmlResolver>Klasa jest używana do rozpoznawania zasobów zewnętrznych. W poniższej tabeli opisano, kiedy zostanie <xref:System.Xml.XmlResolver> ona uwzględniona podczas przetwarzania XSLT.  
  
|Zadanie XSLT|Do czego służy element XmlResolver|  
|---------------|--------------------------------------|  
|Kompiluj arkusz stylów.|Rozpoznanie identyfikatora URI arkusza stylów.<br /><br /> lub<br /><br /> Rozpoznaj odwołania do identyfikatorów URI w dowolnych `xsl:import` lub `xsl:include` elementach.|  
|Wykonaj arkusz stylów.|Rozpoznanie identyfikatora URI dokumentu kontekstowego.<br /><br /> lub<br /><br /> Rozpoznawanie odwołań do identyfikatorów URI w dowolnych `document()` funkcjach XSLT.|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>Metody i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> obejmują przeciążenia przyjmujące <xref:System.Xml.XmlResolver> obiekt jako jeden z argumentów. Jeśli <xref:System.Xml.XmlResolver> nie jest określony, <xref:System.Xml.XmlUrlResolver> zostanie użyta wartość domyślna bez poświadczeń.  
  
 Na poniższej liście opisano, kiedy warto określić <xref:System.Xml.XmlResolver> obiekt:  
  
- Jeśli proces XSLT musi uzyskać dostęp do zasobu sieciowego, który wymaga uwierzytelnienia, możesz użyć <xref:System.Xml.XmlResolver> z niezbędnymi poświadczeniami.  
  
- Jeśli chcesz ograniczyć zasoby, do których proces XSLT może uzyskać dostęp, możesz użyć <xref:System.Xml.XmlSecureResolver> z prawidłowym zestawem uprawnień. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli konieczne jest otwarcie zasobu, którego nie kontrolujesz lub który nie jest zaufany.  
  
- Jeśli chcesz dostosować zachowanie, możesz zaimplementować własną <xref:System.Xml.XmlResolver> klasę i używać jej do rozwiązywania zasobów.  
  
- Jeśli chcesz się upewnić, że nie ma dostępu do zasobów zewnętrznych, możesz określić `null` dla tego <xref:System.Xml.XmlResolver> argumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje arkusz stylów, który jest przechowywany w zasobów sieciowych. <xref:System.Xml.XmlUrlResolver>Obiekt określa poświadczenia niezbędne do uzyskania dostępu do arkusza stylów.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [Przekształcenia XSLT](xslt-transformations.md)
