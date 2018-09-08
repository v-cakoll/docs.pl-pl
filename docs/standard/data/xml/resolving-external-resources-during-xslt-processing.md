---
title: Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 958699b8e3a00cfe3f8fd8ac4bb96914dcd0598c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137593"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
Istnieje kilka razy podczas transformacji XSLT, gdy trzeba rozwiązać zasobów zewnętrznych.  
  
## <a name="using-the-xmlresolver-class"></a>Używanie klasy element XmlResolver  
 <xref:System.Xml.XmlResolver> Klasy jest używany do rozpoznawania zasobów zewnętrznych. Poniższa tabela opisuje, kiedy <xref:System.Xml.XmlResolver> staje się zaangażowane podczas przetwarzania XSLT.  
  
|Zadanie XSLT|Element XmlResolver do czego służy|  
|---------------|--------------------------------------|  
|Skompiluj arkusza stylów.|Rozwiązany identyfikator URI w arkusza stylów.<br /><br /> - i -<br /><br /> Rozpoznać identyfikatora URI odwołania w żadnym `xsl:import` lub `xsl:include` elementów.|  
|Wykonaj arkusza stylów.|Rozwiązany identyfikator URI dokumentu kontekstu.<br /><br /> - i -<br /><br /> Rozwiązać odwołania do identyfikatora URI w dowolnym XSLT `document()` funkcji.|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody obejmują przeciążeń, które przyjmują <xref:System.Xml.XmlResolver> obiektu jako jeden z jej argumentów. Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, domyślnie <xref:System.Xml.XmlUrlResolver> bez poświadczeń jest używany.  
  
 Na poniższej liście opisano, kiedy warto określić <xref:System.Xml.XmlResolver> obiektu:  
  
-   Jeśli proces XSLT musi uzyskać dostęp do zasobów sieciowych, która wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> niezbędne poświadczenia.  
  
-   Jeśli chcesz ograniczyć zasoby, które proces XSLT można uzyskać dostępu, możesz użyć <xref:System.Xml.XmlSecureResolver> with odpowiednie uprawnienie jest ustawiona. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli trzeba otworzyć zasób, które nie mają kontroli nad lub które nie jest zaufany.  
  
-   Jeśli chcesz dostosować zachowanie, możesz zaimplementować własną <xref:System.Xml.XmlResolver> klasy i używane w celu rozwiązania zasobów.  
  
-   Jeśli chcesz upewnić się, że są dostępne nie zasoby zewnętrzne, można określić `null` dla <xref:System.Xml.XmlResolver> argumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje arkusza stylów, który jest przechowywany w zasobie sieciowym. <xref:System.Xml.XmlUrlResolver> Obiekt Określa poświadczenia niezbędne do uzyskania dostępu arkusza stylów.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- <xref:System.Xml.Xsl.XsltSettings>  
- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
