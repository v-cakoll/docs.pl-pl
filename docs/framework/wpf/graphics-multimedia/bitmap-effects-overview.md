---
title: Przegląd Efekty mapy bitowej
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: f2fa42d5d63cad6a71efd259416dad3416bf2d72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935301"
---
# <a name="bitmap-effects-overview"></a>Przegląd Efekty mapy bitowej
Efekty mapy bitowej umożliwiają projektantom i deweloperom stosowanie efektów wizualnych do renderowanej zawartości Windows Presentation Foundation (WPF). Na przykład efekt mapy bitowej pozwala łatwo zastosować <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efekt lub efekt rozmycia do obrazu lub przycisku.  
  
> [!IMPORTANT]
> W .NET Framework 4 lub nowszych <xref:System.Windows.Media.Effects.BitmapEffect> Klasa jest przestarzała. Jeśli spróbujesz użyć <xref:System.Windows.Media.Effects.BitmapEffect> klasy, zostanie wyświetlony przestarzały wyjątek. Nieprzestarzała alternatywa dla <xref:System.Windows.Media.Effects.BitmapEffect> klasy <xref:System.Windows.Media.Effects.Effect> jest klasą. W większości sytuacji <xref:System.Windows.Media.Effects.Effect> Klasa jest znacznie szybsza.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efekty mapy bitowej WPF  
 Efekty mapy bitowej<xref:System.Windows.Media.Effects.BitmapEffect> (Object) to proste operacje przetwarzania pikseli. Efekt mapy bitowej przyjmuje <xref:System.Windows.Media.Imaging.BitmapSource> jako dane wejściowe i tworzy nowy <xref:System.Windows.Media.Imaging.BitmapSource> po zastosowaniu efektu, takiego jak rozmycie lub cień. Każdy efekt mapy bitowej uwidacznia właściwości, które mogą kontrolować właściwości filtrowania, <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>na przykład.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]specjalnym przypadku, efekty mogą być ustawiane jako właściwości <xref:System.Windows.Controls.Button> obiektów na żywo <xref:System.Windows.Media.Visual> , takich jak lub <xref:System.Windows.Controls.TextBox>. Przetwarzanie pikseli jest stosowane i renderowane w czasie wykonywania. W tym przypadku w czasie renderowania <xref:System.Windows.Media.Visual> jest automatycznie konwertowane na jego <xref:System.Windows.Media.Imaging.BitmapSource> odpowiednik i jest <xref:System.Windows.Media.Effects.BitmapEffect>podawana jako dane wejściowe. Dane wyjściowe zastępują <xref:System.Windows.Media.Visual> domyślne zachowanie renderowania obiektu. Dlatego <xref:System.Windows.Media.Effects.BitmapEffect> obiekty wymuszają wizualizację do renderowania wyłącznie w oprogramowaniu, tj. bez przyspieszania sprzętowego dla wizualizacji, gdy są stosowane efekty.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>symuluje obiekt, który wygląda poza fokusem.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>tworzy otoczkę koloru wokół obwodu obiektu.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>tworzy cień za obiektem.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>tworzy skos, który podnosi powierzchnię obrazu zgodnie z określoną krzywą.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>tworzy mapowanie <xref:System.Windows.Media.Visual> nierówności, aby dać wrażenie głębokości i tekstury z sztucznego źródła światła.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]efekty mapy bitowej są renderowane w trybie oprogramowania. Każdy obiekt, który stosuje efekt, będzie również renderowany w oprogramowaniu. Wydajność jest obniżana w przypadku używania efektów mapy bitowej w dużych wizualizacjach lub animowania właściwości efektu mapy bitowej. Nie oznacza to, że w ten sposób nie powinno się używać efektów mapy bitowej w ten sposób, ale należy zachować ostrożność i przetestować dokładnie, aby upewnić się, że użytkownicy uzyskują oczekiwane doświadczenie.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]efekty bitmapowe nie obsługują częściowego wykonywania zaufania. Aplikacja musi mieć uprawnienia pełnego zaufania, aby można było używać efektów mapy bitowej.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Jak zastosować efekt  
 <xref:System.Windows.Media.Effects.BitmapEffect>jest właściwością <xref:System.Windows.Media.Visual>. W związku z tym stosowanie efektów do wizualizacji, <xref:System.Windows.Controls.Button>takich <xref:System.Windows.Controls.Image>jak <xref:System.Windows.Media.DrawingVisual>,, <xref:System.Windows.UIElement>, lub, jest tak proste jak ustawienie właściwości. <xref:System.Windows.UIElement.BitmapEffect%2A>może być ustawiony na pojedynczy <xref:System.Windows.Media.Effects.BitmapEffect> obiekt lub wiele efektów może być łańcucha przy <xref:System.Windows.Media.Effects.BitmapEffectGroup> użyciu obiektu.  
  
 <xref:System.Windows.Media.Effects.BitmapEffect> W[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]poniższym przykładzie pokazano, jak zastosować.  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 W poniższym przykładzie pokazano, <xref:System.Windows.Media.Effects.BitmapEffect> jak zastosować kod w kodzie.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Gdy jest stosowany do kontenera układu, takiego jak <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.Canvas>, efekt jest stosowany do drzewa wizualnego elementu lub wizualizacji, w tym wszystkich elementów podrzędnych. <xref:System.Windows.Media.Effects.BitmapEffect>  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Tworzenie niestandardowych efektów  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]udostępnia również interfejsy niezarządzane do tworzenia niestandardowych efektów, które mogą być używane w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zarządzanych aplikacjach. Dodatkowe materiały referencyjne służące do tworzenia niestandardowych efektów mapy bitowej można znaleźć w dokumentacji dotyczącej niezarządzanego [efektu mapy BITOWEJ WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Niezarządzany efekt mapy bitowej WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Obrazowanie — przegląd](imaging-overview.md)
- [Zabezpieczenia](../security-wpf.md)
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
