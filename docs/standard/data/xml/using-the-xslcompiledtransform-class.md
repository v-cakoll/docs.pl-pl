---
title: Używanie klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a524b80d8789567dc2aa943d7321fd49fe3c7c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939425"
---
# <a name="using-the-xslcompiledtransform-class"></a>Używanie klasy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest procesorem XSLT środowiska Microsoft .NET Framework. Ta klasa jest używana do kompilowania arkuszy stylów i wykonywania transformacji XSLT.  
  
> [!NOTE]
> Chociaż ogólna <xref:System.Xml.Xsl.XslCompiledTransform> wydajność klasy jest lepsza <xref:System.Xml.Xsl.XslTransform> niż Klasa <xref:System.Xml.Xsl.XslCompiledTransform> , <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda klasy może być wykonywana wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslTransform> klasy przy pierwszym jest wywoływana w transformacji. Jest to spowodowane tym, że plik XSLT musi być skompilowany przed załadowaniem. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dane wejściowe klasy XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Opisuje dostępne opcje wejściowe XSLT.  
  
 [Opcje danych wyjściowych klasy XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Opisuje dostępne opcje wyjściowe XSLT.  
  
 [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 W tym artykule <xref:System.Xml.XmlResolver> omówiono użycie klasy do rozpoznawania zasobów zewnętrznych.  
  
 [Rozszerzanie arkuszy stylów XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Omawia, w jaki sposób rozszerzenia XSLT są obsługiwane.  
  
|||  
|-|-|  
|[Odwracalne błędy XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Wyświetla listę arbitralnych zachowań dozwolonych przez organizacja World Wide Web Consortium (W3C) 1,0 zalecenia i opisuje sposób obsługi tych zachowań przez <xref:System.Xml.Xsl.XslCompiledTransform> klasę.|  
|[Instrukcje: Przekształcanie fragmentu węzła](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Opisuje sposób przekształcania fragmentu węzła.|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Omawia sposób migrowania kodu z <xref:System.Xml.Xsl.XslTransform> klasy  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
