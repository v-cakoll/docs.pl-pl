---
title: Przegląd Efekty mapy bitowej
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5c304363efe7d0e9bd9e14ff916f8d852ab3a8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636019"
---
# <a name="bitmap-effects-overview"></a>Przegląd Efekty mapy bitowej
Efekty mapy bitowej umożliwiają projektantom i deweloperom stosowanie efektów wizualnych do renderowanej zawartości Windows Presentation Foundation (WPF). Na przykład efekty mapy bitowej umożliwiają łatwe stosowanie efektu <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> lub efektu rozmycia do obrazu lub przycisku.  
  
> [!IMPORTANT]
> W .NET Framework 4 lub nowszych Klasa <xref:System.Windows.Media.Effects.BitmapEffect> jest przestarzała. Jeśli spróbujesz użyć klasy <xref:System.Windows.Media.Effects.BitmapEffect>, zostanie wyświetlony przestarzały wyjątek. Nieprzestarzała alternatywa dla klasy <xref:System.Windows.Media.Effects.BitmapEffect> jest klasą <xref:System.Windows.Media.Effects.Effect>. W większości sytuacji Klasa <xref:System.Windows.Media.Effects.Effect> jest znacznie szybsza.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efekty mapy bitowej WPF  
 Efekty mapy bitowej (<xref:System.Windows.Media.Effects.BitmapEffect> Object) to proste operacje przetwarzania pikseli. Efekt mapy bitowej przyjmuje <xref:System.Windows.Media.Imaging.BitmapSource> jako dane wejściowe i tworzy nowy <xref:System.Windows.Media.Imaging.BitmapSource> po zastosowaniu efektu, takiego jak rozmycie lub cień. Każdy efekt mapy bitowej uwidacznia właściwości, które mogą kontrolować właściwości filtrowania, takie jak <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 W specjalnym przypadku, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], efekty mogą być ustawiane jako właściwości obiektów <xref:System.Windows.Media.Visual> na żywo, takich jak <xref:System.Windows.Controls.Button> lub <xref:System.Windows.Controls.TextBox>. Przetwarzanie pikseli jest stosowane i renderowane w czasie wykonywania. W tym przypadku w czasie renderowania <xref:System.Windows.Media.Visual> jest automatycznie konwertowana na <xref:System.Windows.Media.Imaging.BitmapSource> równoważne i jest podawana jako dane wejściowe do <xref:System.Windows.Media.Effects.BitmapEffect>. Dane wyjściowe zastępują domyślne zachowanie renderowania obiektu <xref:System.Windows.Media.Visual>. Dlatego <xref:System.Windows.Media.Effects.BitmapEffect> obiekty wymuszają wizualizację do renderowania wyłącznie w oprogramowaniu, tj. bez przyspieszania sprzętowego dla wizualizacji, gdy są stosowane efekty.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect> symuluje nieskoncentrowany obiekt.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> tworzy otoczkę koloru wokół obwodu obiektu.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> tworzy cień za obiektem.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect> tworzy skos, który podnosi powierzchnię obrazu zgodnie z określoną krzywą.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect> tworzy mapowanie nierówności <xref:System.Windows.Media.Visual>, aby dać wrażenie głębokości i tekstury z sztucznego źródła światła.  
  
> [!NOTE]
> Efekty mapy bitowej WPF są renderowane w trybie oprogramowania. Każdy obiekt, który stosuje efekt, będzie również renderowany w oprogramowaniu. Wydajność jest obniżana w przypadku używania efektów mapy bitowej w dużych wizualizacjach lub animowania właściwości efektu mapy bitowej. Nie oznacza to, że w ten sposób nie powinno się używać efektów mapy bitowej w ten sposób, ale należy zachować ostrożność i przetestować dokładnie, aby upewnić się, że użytkownicy uzyskują oczekiwane doświadczenie.  
  
> [!NOTE]
> Efekty mapy bitowej WPF nie obsługują częściowego wykonywania zaufania. Aplikacja musi mieć uprawnienia pełnego zaufania, aby można było używać efektów mapy bitowej.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Jak zastosować efekt  
 <xref:System.Windows.Media.Effects.BitmapEffect> jest właściwością <xref:System.Windows.Media.Visual>. W związku z tym stosowanie efektów do wizualizacji, takich jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>lub <xref:System.Windows.UIElement>, jest tak proste jak ustawienie właściwości. <xref:System.Windows.UIElement.BitmapEffect%2A> można ustawić na pojedynczy obiekt <xref:System.Windows.Media.Effects.BitmapEffect> lub wiele efektów może być łańcucha przy użyciu obiektu <xref:System.Windows.Media.Effects.BitmapEffectGroup>.  
  
 W poniższym przykładzie pokazano, jak zastosować <xref:System.Windows.Media.Effects.BitmapEffect> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 W poniższym przykładzie pokazano, jak zastosować <xref:System.Windows.Media.Effects.BitmapEffect> w kodzie.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Gdy <xref:System.Windows.Media.Effects.BitmapEffect> jest stosowana do kontenera układu, takiego jak <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.Canvas>, efekt jest stosowany do drzewa wizualnego elementu lub wizualizacji, w tym wszystkich elementów podrzędnych.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Tworzenie niestandardowych efektów  
 WPF udostępnia także niezarządzane interfejsy do tworzenia niestandardowych efektów, które mogą być używane w zarządzanych aplikacjach WPF. Dodatkowe materiały referencyjne służące do tworzenia niestandardowych efektów mapy bitowej można znaleźć w dokumentacji dotyczącej [niezarządzanego efektu mapy BITOWEJ WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Niezarządzany efekt mapy bitowej WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Obrazowanie — przegląd](imaging-overview.md)
- [Zabezpieczenia](../security-wpf.md)
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
