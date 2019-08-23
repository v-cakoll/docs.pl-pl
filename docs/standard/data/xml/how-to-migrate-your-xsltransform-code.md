---
title: 'Instrukcje: Migrowanie kodu XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7022a0f55cd7994141148bc6b2faefb10bfea416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966979"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Instrukcje: Migrowanie kodu XslTransform
Nowe klasy XSLT zostały zaprojektowane tak, aby były bardzo podobne do istniejących klas. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa<xref:System.Xml.Xsl.XslTransform> zastępuje klasę. Arkusze stylów są kompilowane przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Transformacje są wykonywane przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. W poniższych procedurach przedstawiono typowe zadania XSLT i porównano kod przy użyciu <xref:System.Xml.Xsl.XslTransform> klasy w porównaniu <xref:System.Xml.Xsl.XslCompiledTransform> z klasą.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Aby przekształcić plik i dane wyjściowe na identyfikator URI  
  
- Kod używający <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- Kod używający <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Aby skompilować arkusz stylów i użyć programu rozpoznawania nazw z poświadczeniami domyślnymi  
  
- Kod używający <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- Kod używający <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>Aby użyć parametru XSLT  
  
- Kod używający <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- Kod używający <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>Aby włączyć obsługę skryptów XSLT  
  
- Kod używający <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- Kod używający <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Aby załadować wyniki do obiektu DOM  
  
- Kod używający <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- Kod używający <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
    > [!NOTE]
    > Klasa nie ma metody, która zwraca wyniki transformacji XSLT <xref:System.Xml.XmlReader> jako obiekt. <xref:System.Xml.Xsl.XslCompiledTransform> Można jednak wykonać wyjście do pliku XML i załadować plik XML do innego obiektu.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Aby przesłać strumieniowo wyniki do innego magazynu danych  
  
- Kod używający <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- Kod używający <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Zobacz także

- [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
