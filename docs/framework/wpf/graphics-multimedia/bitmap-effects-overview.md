---
title: Przegląd Efekty mapy bitowej
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5e73f21d4ce4988f56c139d13038dca902b5b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186993"
---
# <a name="bitmap-effects-overview"></a>Przegląd Efekty mapy bitowej
Efekty bitmapowe umożliwiają projektantom i deweloperom stosowanie efektów wizualnych do renderowanych treści Programu Windows Presentation Foundation (WPF). Na przykład efekty bitmapy umożliwiają <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> łatwe zastosowanie efektu lub efektu rozmycia do obrazu lub przycisku.  
  
> [!IMPORTANT]
> W .NET Framework 4 lub <xref:System.Windows.Media.Effects.BitmapEffect> nowszych klasa jest przestarzała. Jeśli spróbujesz <xref:System.Windows.Media.Effects.BitmapEffect> użyć klasy, otrzymasz przestarzały wyjątek. Nieprzestarzewszą <xref:System.Windows.Media.Effects.BitmapEffect> alternatywą <xref:System.Windows.Media.Effects.Effect> dla klasy jest klasa. W większości sytuacji <xref:System.Windows.Media.Effects.Effect> klasa jest znacznie szybsza.  

<a name="wpf_effects"></a>
## <a name="wpf-bitmap-effects"></a>Efekty bitmapy WPF  
 Efekty bitmapowe (obiekt)<xref:System.Windows.Media.Effects.BitmapEffect> są prostymi operacjami przetwarzania pikseli. Efekt mapy bitowej <xref:System.Windows.Media.Imaging.BitmapSource> przyjmuje jako dane wejściowe i tworzy nowy <xref:System.Windows.Media.Imaging.BitmapSource> po zastosowaniu efektu, na przykład rozmycie lub cień. Każdy efekt mapy bitowej udostępnia właściwości, które mogą kontrolować <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>właściwości filtrowania, takie jak .  
  
 W szczególnym przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]efekty w programie można ustawić <xref:System.Windows.Media.Visual> jako właściwości obiektów <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox>żywych, takich jak lub . Przetwarzanie pikseli jest stosowane i renderowane w czasie wykonywania. W takim przypadku, w czasie renderowania, a <xref:System.Windows.Media.Visual> jest <xref:System.Windows.Media.Imaging.BitmapSource> automatycznie konwertowany na <xref:System.Windows.Media.Effects.BitmapEffect>jego odpowiednik i jest podawany jako dane wejściowe do . Dane wyjściowe <xref:System.Windows.Media.Visual> zastępują domyślne zachowanie renderowania obiektu. Dlatego <xref:System.Windows.Media.Effects.BitmapEffect> obiekty zmuszają wizualizacje do renderowania w oprogramowaniu tylko wtedy, gdy są stosowane efekty, nie ma akceleracji sprzętowej na wizualizacjach.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>symuluje obiekt, który wydaje się nieokreślenia.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>tworzy aureolę koloru na obwodzie obiektu.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>tworzy cień za obiektem.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>tworzy skos, który podnosi powierzchnię obrazu zgodnie z określoną krzywą.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>tworzy odwzorowanie <xref:System.Windows.Media.Visual> wypukłości a, aby dać wrażenie głębi i tekstury ze sztucznego źródła światła.  
  
> [!NOTE]
> Efekty bitmapy WPF są renderowane w trybie oprogramowania. Każdy obiekt, który stosuje efekt, będzie również renderowany w oprogramowaniu. Wydajność jest najbardziej obniżana podczas używania efektów bitmapowych na dużych wizualizacjach lub animowaniu właściwości efektu bitmapy. Nie oznacza to, że nie należy używać efektów bitmapy w ten sposób w ogóle, ale należy zachować ostrożność i dokładnie przetestować, aby upewnić się, że użytkownicy są coraz doświadczenie można oczekiwać.  
  
> [!NOTE]
> Efekty mapy bitowej WPF nie obsługują częściowego wykonywania zaufania. Aplikacja musi mieć pełne uprawnienia zaufania do używania efektów bitmapowych.  
  
<a name="applyeffects"></a>
## <a name="how-to-apply-an-effect"></a>Jak zastosować efekt  
 <xref:System.Windows.Media.Effects.BitmapEffect>jest własnością <xref:System.Windows.Media.Visual>na . Dlatego stosowanie efektów do wizualizacji, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Image>takich <xref:System.Windows.Media.DrawingVisual>jak <xref:System.Windows.UIElement>, , , lub , jest tak proste, jak ustawienie właściwości. <xref:System.Windows.UIElement.BitmapEffect%2A>można ustawić na <xref:System.Windows.Media.Effects.BitmapEffect> pojedynczy obiekt lub wiele efektów <xref:System.Windows.Media.Effects.BitmapEffectGroup> można przywiązywać za pomocą obiektu.  
  
 W poniższym przykładzie pokazano, jak zastosować <xref:System.Windows.Media.Effects.BitmapEffect> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 W poniższym przykładzie pokazano, jak zastosować <xref:System.Windows.Media.Effects.BitmapEffect> w kodzie.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Gdy <xref:System.Windows.Media.Effects.BitmapEffect> a jest stosowany do kontenera <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Canvas>układu, takich jak lub , efekt jest stosowany do drzewa wizualnego elementu lub wizualizacji, w tym wszystkie jego elementy podrzędne.  
  
<a name="customeffects"></a>
## <a name="creating-custom-effects"></a>Tworzenie efektów niestandardowych  
 WPF WPF udostępnia również interfejsy niezarządzane do tworzenia efektów niestandardowych, które mogą być używane w zarządzanych aplikacji WPF. Aby uzyskać dodatkowy materiał referencyjny do tworzenia niestandardowych efektów bitmapowych, zobacz dokumentację [Efekt bitmapowy Unmanaged WPF.](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Niezarządzany efekt mapy bitowej WPF](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Obrazowanie — przegląd](imaging-overview.md)
- [Zabezpieczenia](../security-wpf.md)
- [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md)
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
