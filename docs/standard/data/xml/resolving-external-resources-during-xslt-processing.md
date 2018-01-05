---
title: "Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2bb115e14f8ff5d1065d87335d4d9021bd32ddd1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
Istnieje kilka razy podczas transformację XSLT, gdy trzeba rozwiązać zasobów zewnętrznych.  
  
## <a name="using-the-xmlresolver-class"></a>Używanie klasy element XmlResolver  
 <xref:System.Xml.XmlResolver> Klasa jest używana do rozpoznawania zasobów zewnętrznych. W poniższej tabeli opisano, kiedy <xref:System.Xml.XmlResolver> staje się zaangażowanych podczas przetwarzania XSLT.  
  
|Zadanie XSLT|Element XmlResolver służy do|  
|---------------|--------------------------------------|  
|Kompiluj arkusza stylów.|Rozwiąż URI arkusza stylów.<br /><br /> - i -<br /><br /> Rozpoznać odwołań do identyfikatora URI w żadnym `xsl:import` lub `xsl:include` elementów.|  
|Wykonanie arkusza stylów.|Rozwiąż identyfikator URI dokumentu kontekstu.<br /><br /> - i -<br /><br /> Rozpoznać odwołań do identyfikatora URI w dowolnym XSLT `document()` funkcji.|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metod uwzględnić przeciążeń, które przyjmują <xref:System.Xml.XmlResolver> obiektu jako jego argumenty. Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, domyślnie <xref:System.Xml.XmlUrlResolver> bez poświadczeń jest używany.  
  
 Na poniższej liście opisano, kiedy można określić <xref:System.Xml.XmlResolver> obiektu:  
  
-   Jeśli proces XSLT wymaga dostępu do zasobu sieciowego, która wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> niezbędne poświadczenia.  
  
-   Jeśli chcesz ograniczyć zasoby, do których dostęp procesu XSLT, możesz użyć <xref:System.Xml.XmlSecureResolver> ustawienie odpowiednie uprawnienia. Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli trzeba otworzyć zasobu, która kontroluje, lub niezaufanych.  
  
-   Jeśli chcesz dostosować zachowanie, można zaimplementować własne <xref:System.Xml.XmlResolver> klasy i użyć go do rozwiązania zasobów.  
  
-   Jeśli chcesz upewnić się, że nie zewnętrzne zasoby są dostępne, można określić `null` dla <xref:System.Xml.XmlResolver> argumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy arkusz stylów, który jest przechowywany w zasobie sieciowym. <xref:System.Xml.XmlUrlResolver> Obiektu Określa poświadczenia niezbędne do uzyskania dostępu arkusza stylów.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltSettings>  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
