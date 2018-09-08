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
ms.openlocfilehash: 71e5ae19b1e0123dc28713befef070a9cc23bdc5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188231"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Instrukcje: Migrowanie kodu XslTransform
Nowe klasy XSLT zostały zaprojektowane, aby być bardzo podobne do istniejących klas. <xref:System.Xml.Xsl.XslCompiledTransform> Klasy zastępuje <xref:System.Xml.Xsl.XslTransform> klasy. Arkusze stylów są kompilowane przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Transformacje są wykonywane przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Poniższe procedury Pokaż popularne zadania XSLT i porównaj przy użyciu kodu <xref:System.Xml.Xsl.XslTransform> klasy a <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Aby przekształcić plik i dane wyjściowe do identyfikatora URI  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Aby skompilować arkusza stylów i program rozpoznawania nazw za pomocą poświadczeń domyślnych  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>Aby użyć parametru XSLT  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>Aby włączyć obsługę skryptów XSLT  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Aby załadować wyniki do obiektu modelu DOM.  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
    > [!NOTE]
    >  <xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie ma metodę, która zwraca wyniki przekształcenia XSLT w postaci <xref:System.Xml.XmlReader> obiektu. Można jednak przesyłać dane wyjściowe do pliku XML i załadować plik XML do innego obiektu.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Aby przesyłać strumieniowo wyniki w innym magazynie danych  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslTransform> klasy.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
-   Kodowanie przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Zobacz także

- [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
