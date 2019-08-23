---
title: 'Instrukcje: Używanie kluczy czcionek systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918389"
---
# <a name="how-to-use-system-fonts-keys"></a>Instrukcje: Używanie kluczy czcionek systemowych
Zasoby systemowe uwidaczniają różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są spójne z ustawieniami systemowymi. <xref:System.Windows.SystemFonts>to Klasa, która zawiera zarówno wartości czcionki systemowej, jak i zasoby czcionki systemowej, które są powiązane z <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> wartościami <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>— na przykład i.  
  
 Metryki czcionek systemowych mogą służyć jako zasoby statyczne lub dynamiczne. Użyj zasobu dynamicznego, jeśli chcesz, aby Metryka czcionki była aktualizowana automatycznie podczas uruchamiania aplikacji; w przeciwnym razie użyj zasobu statycznego.  
  
> [!NOTE]
> Zasoby dynamiczne mają *klucz* słowa kluczowego, który jest dołączany do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamicznych czcionki systemu i używać ich do nadawania stylu lub dostosowywania przycisku. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tym przykładzie tworzony jest styl przycisku przypisujący <xref:System.Windows.SystemFonts> wartości do przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Zobacz także

- [Malowanie obszaru pędzlem systemowym](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Używanie elementu SystemParameters](how-to-use-systemparameters.md)
- [Używanie elementu SystemFonts](how-to-use-systemfonts.md)
