---
title: 'Instrukcje: Używanie elementu SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 7438705a82faee464649b5f6f577627a379e9a8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918365"
---
# <a name="how-to-use-systemfonts"></a>Instrukcje: Używanie elementu SystemFonts
Ten przykład pokazuje, jak używać zasobów <xref:System.Windows.SystemFonts> statycznych klasy w celu uzyskania stylu lub dostosowywania przycisku.  
  
## <a name="example"></a>Przykład  
 Zasoby systemowe uwidaczniają kilka wartości określanych przez system jako zasoby i właściwości w celu ułatwienia tworzenia wizualizacji, które są spójne z ustawieniami systemowymi. <xref:System.Windows.SystemFonts>to Klasa, która zawiera obie wartości czcionki systemowej jako właściwości statyczne i właściwości, które odwołują się do kluczy zasobów, których można użyć do dynamicznego uzyskiwania dostępu do tych wartości w czasie wykonywania. Na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> <xref:System.Windows.SystemFonts> jest wartością i <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> jest odpowiednim kluczem zasobu.  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programie można użyć <xref:System.Windows.SystemFonts> elementów członkowskich jako właściwości statycznych lub dynamicznych odwołań do zasobów (z wartością właściwości statycznej jako klucz). Użyj odwołania do zasobów dynamicznych, jeśli chcesz, aby Metryka czcionki była automatycznie aktualizowana podczas uruchamiania aplikacji; w przeciwnym razie użyj statycznego odwołania do wartości.  
  
> [!NOTE]
> Klucze zasobów mają sufiks "klucz" dołączony do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak uzyskać dostęp do właściwości <xref:System.Windows.SystemFonts> jako wartości statycznych i używać ich w celu uzyskania stylu lub dostosowywania przycisku. Ten przykład znacznika służy <xref:System.Windows.SystemFonts> do przypisywania wartości do przycisku.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Aby użyć wartości <xref:System.Windows.SystemFonts> w kodzie, nie trzeba używać wartości statycznej ani dynamicznego odwołania do zasobów. Zamiast tego należy użyć właściwości <xref:System.Windows.SystemFonts> , które nie są kluczami klasy. Mimo że właściwości nieklucza są prawdopodobnie zdefiniowane jako właściwości statyczne, zachowanie w czasie wykonywania, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest hostowane przez system, będzie ponownie szacować właściwości w czasie rzeczywistym i będzie prawidłowo obsługiwać zmiany wartości systemu przez użytkownika. Poniższy przykład pokazuje, jak określić ustawienia czcionki przycisku.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.SystemFonts>
- [Malowanie obszaru pędzlem systemowym](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Używanie elementu SystemParameters](how-to-use-systemparameters.md)
- [Używanie kluczy czcionek systemowych](how-to-use-system-fonts-keys.md)
- [Tematy z instrukcjami](resources-how-to-topics.md)
- [x:Static, rozszerzenie znaczników](../../xaml-services/x-static-markup-extension.md)
- [Zasoby XAML](xaml-resources.md)
- [DynamicResource, rozszerzenie znaczników](dynamicresource-markup-extension.md)
