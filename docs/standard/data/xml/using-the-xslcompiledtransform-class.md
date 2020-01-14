---
title: Używanie klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 6fc29b523e59590138cb7ca4db1b0da1bfee99c8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937943"
---
# <a name="using-the-xslcompiledtransform-class"></a>Używanie klasy XslCompiledTransform
Klasa <xref:System.Xml.Xsl.XslCompiledTransform> jest procesorem XSLT środowiska Microsoft .NET Framework. Ta klasa jest używana do kompilowania arkuszy stylów i wykonywania transformacji XSLT.  
  
> [!NOTE]
> Chociaż ogólna wydajność klasy <xref:System.Xml.Xsl.XslCompiledTransform> jest lepsza niż Klasa <xref:System.Xml.Xsl.XslTransform>, Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> klasy <xref:System.Xml.Xsl.XslCompiledTransform> może działać wolniej niż Metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> klasy <xref:System.Xml.Xsl.XslTransform> przy pierwszym wywołaniu dla transformacji. Jest to spowodowane tym, że plik XSLT musi być skompilowany przed załadowaniem. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dane wejściowe klasy XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Opisuje dostępne opcje wejściowe XSLT.  
  
 [Opcje danych wyjściowych klasy XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Opisuje dostępne opcje wyjściowe XSLT.  
  
 [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 W tym artykule omówiono korzystanie z klasy <xref:System.Xml.XmlResolver> w celu rozwiązywania zasobów zewnętrznych.  
  
 [Rozszerzanie arkuszy stylów XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Omawia, w jaki sposób rozszerzenia XSLT są obsługiwane.  
  
|||  
|-|-|  
|[Odwracalne błędy XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Wyświetla listę arbitralnych zachowań dozwolonych przez organizacja World Wide Web Consortium (W3C) 1,0 zalecenia i opisuje sposób obsługi tych zachowań przez klasę <xref:System.Xml.Xsl.XslCompiledTransform>.|  
|[Instrukcje: Przekształcanie fragmentu węzła](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Opisuje sposób przekształcania fragmentu węzła.|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 W tym artykule omówiono sposób migrowania kodu z klasy <xref:System.Xml.Xsl.XslTransform>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
