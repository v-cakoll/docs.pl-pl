---
title: Używanie klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 8705b4c6324ce20a1f37d3ee864ab494adcdd6a5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281776"
---
# <a name="using-the-xslcompiledtransform-class"></a>Używanie klasy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform>Klasa jest procesorem XSLT środowiska Microsoft .NET Framework. Ta klasa jest używana do kompilowania arkuszy stylów i wykonywania transformacji XSLT.  
  
> [!NOTE]
> Chociaż ogólna wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepsza niż <xref:System.Xml.Xsl.XslTransform> Klasa, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslCompiledTransform> klasy może działać wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslTransform> klasy, gdy jest wywoływana po raz pierwszy. Jest to spowodowane tym, że plik XSLT musi być skompilowany przed załadowaniem. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dane wejściowe klasy XslCompiledTransform](inputs-to-the-xslcompiledtransform-class.md)  
 Opisuje dostępne opcje wejściowe XSLT.  
  
 [Opcje danych wyjściowych klasy XslCompiledTransform](output-options-on-the-xslcompiledtransform-class.md)  
 Opisuje dostępne opcje wyjściowe XSLT.  
  
 [Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT](resolving-external-resources-during-xslt-processing.md)  
 W tym artykule omówiono użycie <xref:System.Xml.XmlResolver> klasy do rozpoznawania zasobów zewnętrznych.  
  
 [Rozszerzanie arkuszy stylów XSLT](extending-xslt-style-sheets.md)  
 Omawia, w jaki sposób rozszerzenia XSLT są obsługiwane.  
  
|||  
|-|-|  
|[Odwracalne błędy XSLT](recoverable-xslt-errors.md)|Wyświetla listę arbitralnych zachowań dozwolonych przez organizacja World Wide Web Consortium (W3C) 1,0 zalecenia i opisuje sposób obsługi tych zachowań przez <xref:System.Xml.Xsl.XslCompiledTransform> klasę.|  
|[Instrukcje: Przekształcanie fragmentu węzła](how-to-transform-a-node-fragment.md)|Opisuje sposób przekształcania fragmentu węzła.|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md)  
 Omawia sposób migrowania kodu z <xref:System.Xml.Xsl.XslTransform> klasy  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
