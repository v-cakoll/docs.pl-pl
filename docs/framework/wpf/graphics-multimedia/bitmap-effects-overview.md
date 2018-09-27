---
title: Przegląd Efekty mapy bitowej
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 97b878621d5aa1860cd955755d9bbc344b95b993
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47236504"
---
# <a name="bitmap-effects-overview"></a>Przegląd Efekty mapy bitowej
Efekty mapy bitowej umożliwia projektantom i deweloperom stosowanie efektów wizualnych do renderowania zawartości Windows Presentation Foundation (WPF). Na przykład efektów mapy bitowej pozwalają łatwo zastosować <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efekt lub efekt rozmycie obrazu lub przycisku.  
  
> [!IMPORTANT]
>  W [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] lub nowszym, <xref:System.Windows.Media.Effects.BitmapEffect> klasa jest przestarzała. Jeśli spróbujesz użyć <xref:System.Windows.Media.Effects.BitmapEffect> klasy, wystąpi wyjątek przestarzały. Nieprzestarzała alternatywa do <xref:System.Windows.Media.Effects.BitmapEffect> klasa jest <xref:System.Windows.Media.Effects.Effect> klasy. W większości sytuacji <xref:System.Windows.Media.Effects.Effect> klasy jest znacznie szybsze.  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efekty mapy bitowej WPF  
 Efekty mapy bitowej (<xref:System.Windows.Media.Effects.BitmapEffect> obiektu) są pikseli proste operacje przetwarzania. Efekt mapy bitowej przyjmuje <xref:System.Windows.Media.Imaging.BitmapSource> jako dane wejściowe i tworzy nowy <xref:System.Windows.Media.Imaging.BitmapSource> po zastosowaniu efektu, takich jak rozmycie lub Usuń w tle. Każdy efekt mapy bitowej udostępnia właściwości, które można kontrolować filtrowania właściwości, takie jak <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> z <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 W szczególnych przypadkach w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], efekty można ustawić jako właściwości na żywo <xref:System.Windows.Media.Visual> obiekty, takie jak <xref:System.Windows.Controls.Button> lub <xref:System.Windows.Controls.TextBox>. Przetwarzanie pikseli zostaną zastosowane i renderowania w czasie wykonywania. W takim przypadku w czasie renderowania <xref:System.Windows.Media.Visual> jest automatycznie konwertowany do jego <xref:System.Windows.Media.Imaging.BitmapSource> równoważne i jest podawany jako dane wejściowe <xref:System.Windows.Media.Effects.BitmapEffect>. Dane wyjściowe zastępuje <xref:System.Windows.Media.Visual> obiektu domyślnym zachowaniu renderowania. Dlatego <xref:System.Windows.Media.Effects.BitmapEffect> obiektów wymusić wizualizacji do renderowania w oprogramowaniu tylko czyli nie przyspieszanie sprzętowe na elementy wizualne, gdy zostaną one zastosowane.  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> symuluje obiekt, który pojawia się poza koncentracji uwagi.  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> Tworzy halo koloru na obwodzie obiektu.  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Tworzy cieniowanie obiektu.  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> Tworzy skos, który wywołuje powierzchni obrazu zgodnie z określonym krzywej.  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> tworzy mapowanie nierówności <xref:System.Windows.Media.Visual> aby stworzyć wrażenie głębokości i tekstur z sztuczne źródła światła.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] efekty mapy bitowej są renderowane w trybie oprogramowania. Każdy obiekt, który ma zastosowanie efektu również będą renderowane w oprogramowaniu. Wydajność jest obniżona, najbardziej po za pomocą mapy bitowej wpływ na duże wizualizacji lub animowanie właściwości efekt mapy bitowej. To nie Załóżmy, że efekty bitmapowe nie należy używać w ten sposób wszystkie, ale powinien zachować ostrożność i dokładnie przetestuj, aby upewnić się, że użytkownicy otrzymują środowiska, których oczekujesz od.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Efekty bitmapowe nie obsługują wykonywanie częściowej relacji zaufania. Aplikacja musi mieć uprawnienia pełnego zaufania do korzystania z efektów mapy bitowej.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Jak zastosować efektu  
 <xref:System.Windows.Media.Effects.BitmapEffect> jest to właściwość na <xref:System.Windows.Media.Visual>. W związku z tym stosowanie efektów w wizualizacji, takich jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, lub <xref:System.Windows.UIElement>, jest równie proste jak konfigurowanie właściwości. <xref:System.Windows.UIElement.BitmapEffect%2A> można ustawić na wartość typu single <xref:System.Windows.Media.Effects.BitmapEffect> obiekt lub wiele efektów umożliwia tworzenie łańcucha przy użyciu <xref:System.Windows.Media.Effects.BitmapEffectGroup> obiektu.  
  
 W poniższym przykładzie pokazano sposób stosowania <xref:System.Windows.Media.Effects.BitmapEffect> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 W poniższym przykładzie pokazano sposób stosowania <xref:System.Windows.Media.Effects.BitmapEffect> w kodzie.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Gdy <xref:System.Windows.Media.Effects.BitmapEffect> jest stosowany do kontener układu, takich jak <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.Canvas>, efekt jest stosowany do drzewa wizualnego elementu lub wizualizacji, w tym wszystkie jego elementy podrzędne.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Tworzenie niestandardowych efektów  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia również niezarządzane interfejsy do tworzenia niestandardowych efektów, które mogą być używane w zarządzanych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Aby uzyskać dodatkowe materiały źródłowe do tworzenia efektów niestandardowej mapy bitowej, zobacz [niezarządzanych efekt mapy bitowej WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [Efekt mapy bitowej niezarządzanych WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)  
 [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Zabezpieczenia](../../../../docs/framework/wpf/security-wpf.md)  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
