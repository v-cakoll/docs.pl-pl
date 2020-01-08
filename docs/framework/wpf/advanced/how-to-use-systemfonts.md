---
title: 'Porady: korzystanie z SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 157565ceb9057049aef8b2bf274847d58c6b8dc8
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559966"
---
# <a name="how-to-use-systemfonts"></a>Porady: korzystanie z SystemFonts
Ten przykład pokazuje, jak używać zasobów statycznych klasy <xref:System.Windows.SystemFonts> w celu uzyskania stylu lub dostosowania przycisku.  
  
## <a name="example"></a>Przykład  
 Zasoby systemowe uwidaczniają kilka wartości określanych przez system jako zasoby i właściwości w celu ułatwienia tworzenia wizualizacji, które są spójne z ustawieniami systemowymi. <xref:System.Windows.SystemFonts> jest klasą, która zawiera obie wartości czcionki systemowej jako właściwości statyczne i właściwości, które odwołują się do kluczy zasobów, których można użyć do dynamicznego uzyskiwania dostępu do tych wartości w czasie wykonywania. Na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> jest wartością <xref:System.Windows.SystemFonts>, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> jest odpowiednim kluczem zasobu.  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można użyć elementów członkowskich <xref:System.Windows.SystemFonts> jako właściwości statycznych lub dynamicznych odwołań do zasobów (z wartością właściwości statycznej jako klucz). Użyj odwołania do zasobów dynamicznych, jeśli chcesz, aby Metryka czcionki była automatycznie aktualizowana podczas uruchamiania aplikacji; w przeciwnym razie użyj statycznego odwołania do wartości.  
  
> [!NOTE]
> Klucze zasobów mają sufiks "klucz" dołączony do nazwy właściwości.  
  
 Poniższy przykład pokazuje, jak uzyskać dostęp do właściwości <xref:System.Windows.SystemFonts> jako wartości statycznych i używać ich w celu uzyskania stylu lub dostosowywania przycisku. Ten przykład znacznika służy do przypisywania wartości <xref:System.Windows.SystemFonts> do przycisku.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Aby użyć wartości <xref:System.Windows.SystemFonts> w kodzie, nie trzeba używać wartości statycznej ani dynamicznego odwołania do zasobów. Zamiast tego należy użyć właściwości, które nie są kluczami klasy <xref:System.Windows.SystemFonts>. Chociaż właściwości, które nie są kluczami, są prawdopodobnie zdefiniowane jako właściwości statyczne, zachowanie w czasie wykonywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które jest hostowane przez system, będzie ponownie szacować właściwości w czasie rzeczywistym i będzie prawidłowo obsługiwać zmiany wartości systemu przez użytkownika. Poniższy przykład pokazuje, jak określić ustawienia czcionki przycisku.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.SystemFonts>
- [Malowanie obszaru pędzlem systemowym](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Używanie elementu SystemParameters](how-to-use-systemparameters.md)
- [Używanie kluczy czcionek systemowych](how-to-use-system-fonts-keys.md)
- [Tematy z instrukcjami](resources-how-to-topics.md)
- [x:Static, rozszerzenie znaczników](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md)
- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [DynamicResource, rozszerzenie znaczników](dynamicresource-markup-extension.md)
