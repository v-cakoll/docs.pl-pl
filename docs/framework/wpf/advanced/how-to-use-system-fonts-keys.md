---
title: 'Instrukcje: Używanie kluczy czcionek systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: e924f4c14d98380d9f4c0defe27d9f98c3293114
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148931"
---
# <a name="how-to-use-system-fonts-keys"></a>Instrukcje: Używanie kluczy czcionek systemowych
Zasoby systemowe ujawnić różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemFonts> to klasa, która zawiera wartości czcionki systemowe i zasobów czcionek systemowych, które wartości należy powiązać — na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> i <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Metryki czcionki systemu może służyć jako zasoby statyczne lub dynamiczne. Użyj dynamicznych zasobów, jeśli chcesz, aby metryki czcionki na automatyczne aktualizowanie podczas jej uruchomieniu; w przeciwnym razie użyj zasób statyczny.  
  
> [!NOTE]
>  Dynamiczne zasoby mają słowa kluczowego *klucz* dołączana do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamicznej czcionek systemowych do nadawania stylu i dostosowywania przycisku. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład tworzy styl przycisku, który przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Zobacz także

- [Malowanie obszaru pędzlem systemowym](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Używanie elementu SystemParameters](how-to-use-systemparameters.md)
- [Używanie elementu SystemFonts](how-to-use-systemfonts.md)
