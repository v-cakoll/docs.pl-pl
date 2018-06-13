---
title: Jak używać kluczy czcionek systemowych
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: c68f197daebd7423aa4ad2e7fdfb6e7f89c74ed0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544430"
---
# <a name="how-to-use-system-fonts-keys"></a>Jak używać kluczy czcionek systemowych
Zasoby systemowe ujawnia szereg metryki systemu jako zasoby, aby pomóc deweloperom tworzenie elementów wizualnych, które są zgodne z ustawieniami systemu. <xref:System.Windows.SystemFonts> jest klasa, która zawiera wartości czcionki systemu i zasobów systemowych czcionek powiązać wartości — na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> i <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Mierniki czcionki systemu może służyć jako zasoby statyczne lub dynamiczne. Użyć zasobu dynamicznego, jeśli Metryka czcionki automatycznej aktualizacji podczas aplikacji działa; w przeciwnym razie użyj statycznych zasobu.  
  
> [!NOTE]
>  Dynamiczne zasobów mieć słowa kluczowego *klucza* dołączonym do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak dostępu i korzystać z zasobów dynamicznej czcionki systemu do nadawania stylu lub dostosowywanie przycisku. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład tworzy styl przycisku, który przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie obszaru pędzlem systemowym](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Używanie elementu SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Używanie elementu SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
