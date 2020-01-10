---
title: 'Instrukcje: Migrowanie kodu XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 2bc5cbc1b0857a82d3b0a11f05a4eb5756724546
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710846"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Instrukcje: Migrowanie kodu XslTransform
Nowe klasy XSLT zostały zaprojektowane tak, aby były bardzo podobne do istniejących klas. Klasa <xref:System.Xml.Xsl.XslCompiledTransform> zastępuje klasę <xref:System.Xml.Xsl.XslTransform>. Arkusze stylów są kompilowane przy użyciu metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>. Transformacje są wykonywane przy użyciu metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. W poniższych procedurach przedstawiono typowe zadania XSLT i porównano kod przy użyciu klasy <xref:System.Xml.Xsl.XslTransform> a klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Aby przekształcić plik i dane wyjściowe na identyfikator URI  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Aby skompilować arkusz stylów i użyć programu rozpoznawania nazw z poświadczeniami domyślnymi  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>Aby użyć parametru XSLT  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>Aby włączyć obsługę skryptów XSLT  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Aby załadować wyniki do obiektu DOM  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
    > [!NOTE]
    > Klasa <xref:System.Xml.Xsl.XslCompiledTransform> nie ma metody, która zwraca wyniki transformacji XSLT jako obiekt <xref:System.Xml.XmlReader>. Można jednak wykonać wyjście do pliku XML i załadować plik XML do innego obiektu.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Aby przesłać strumieniowo wyniki do innego magazynu danych  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslTransform>.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- Kod korzystający z klasy <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Zobacz także

- [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
