---
title: "Przegląd Efekty mapy bitowej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f642c699a0ecf3e3cce328363f90110766002e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-effects-overview"></a>Przegląd Efekty mapy bitowej
Włącz efekty mapy bitowej projektanci i deweloperzy umożliwia stosowanie efektów wizualnych renderowane [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] zawartości. Na przykład efekty mapy bitowej pozwalają łatwo zastosować <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efekt lub efekt rozmycia obrazu lub przycisku.  
  
> [!IMPORTANT]
>  W [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] lub nowszym, <xref:System.Windows.Media.Effects.BitmapEffect> klasa jest przestarzała. Jeśli spróbujesz użyć <xref:System.Windows.Media.Effects.BitmapEffect> klasy, wystąpi wyjątek przestarzałe. Aktualna alternatywa do <xref:System.Windows.Media.Effects.BitmapEffect> jest klasa <xref:System.Windows.Media.Effects.Effect> klasy. W większości przypadków <xref:System.Windows.Media.Effects.Effect> klasy jest znacznie szybsze.  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Efekty mapy bitowej WPF  
 Bitmap efekty (<xref:System.Windows.Media.Effects.BitmapEffect> obiektu) są pikseli proste operacje przetwarzania. Efekt mapy bitowej przyjmuje <xref:System.Windows.Media.Imaging.BitmapSource> jako dane wejściowe i tworzy nowy <xref:System.Windows.Media.Imaging.BitmapSource> po zastosowaniu efekt, takich jak cień rozmycia lub Usuń. Każdy efekt mapy bitowej udostępnia właściwości, które można kontrolować filtrowania właściwości, takie jak <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> z <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 W szczególnych przypadkach w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], efekty można ustawić jako właściwości na żywo <xref:System.Windows.Media.Visual> obiekty, takie jak <xref:System.Windows.Controls.Button> lub <xref:System.Windows.Controls.TextBox>. Przetwarzanie pikseli jest stosowane i renderowane w czasie wykonywania. W takim przypadku w czasie renderowania <xref:System.Windows.Media.Visual> jest automatycznie konwertowany do jego <xref:System.Windows.Media.Imaging.BitmapSource> równoważne i jest podawany jako dane wejściowe <xref:System.Windows.Media.Effects.BitmapEffect>. Dane wyjściowe zastępuje <xref:System.Windows.Media.Visual> obiektu domyślne zachowanie renderowania. Jest to dlaczego <xref:System.Windows.Media.Effects.BitmapEffect> obiektów wymusić elementy wizualne do renderowania w oprogramowaniu tylko tzn. nie przyspieszanie sprzętowe na elementy wizualne, gdy zostaną one zastosowane.  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect>symuluje obiektu znajdującego się poza fokusu.  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>Tworzy otoczki kolor obwodzie obiektu.  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>Tworzy cieniowanie obiektu.  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect>Tworzy fazy, która zwiększa obszar obrazu zgodnie z określonym krzywej.  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect>tworzy mapowanie nierówności <xref:System.Windows.Media.Visual> do dają pogląd głębokość i tekstury ze źródła światła sztuczne.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]efekty mapy bitowej są renderowane w trybie oprogramowania. Każdy obiekt, który ma zastosowanie efektu będą również renderowane w oprogramowaniu. Zmniejsza wydajność najbardziej po przy użyciu mapy bitowej wpływ na elementy wizualne dużych lub animowania właściwości efekt mapy bitowej. To jest nie efekty mapy bitowej nie należy używać w ten sposób na wszystkie, że należy zachować ostrożność i przetestować dokładnie, aby upewnić się, że użytkownicy uzyskują środowisko oczekiwanych.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]efekty mapy bitowej nie obsługuje wykonywania częściowej relacji zaufania. Aplikacja musi mieć uprawnienia pełnego zaufania efekty mapy bitowej.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Jak stosować efektu  
 <xref:System.Windows.Media.Effects.BitmapEffect>jest to właściwość na <xref:System.Windows.Media.Visual>. W związku z tym stosowanie efektów do elementy wizualne, takie jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, lub <xref:System.Windows.UIElement>, jest równie proste jak ustawienie właściwości. <xref:System.Windows.UIElement.BitmapEffect%2A>można ustawić jednej <xref:System.Windows.Media.Effects.BitmapEffect> można powiązać wiele efektów lub obiektu za pomocą <xref:System.Windows.Media.Effects.BitmapEffectGroup> obiektu.  
  
 W poniższym przykładzie pokazano sposób stosowania <xref:System.Windows.Media.Effects.BitmapEffect> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 W poniższym przykładzie pokazano sposób stosowania <xref:System.Windows.Media.Effects.BitmapEffect> w kodzie.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Gdy <xref:System.Windows.Media.Effects.BitmapEffect> jest stosowany do kontener układu, takich jak <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.Canvas>, efekt jest stosowany do drzewa wizualnego elementu lub visual, w tym wszystkie jego elementy podrzędne.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Tworzenie niestandardowych efektów  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]dostępne są także niezarządzane interfejsy do tworzenia niestandardowych efektów, które mogą być używane w zarządzanych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Dla materiału dodatkowe odwołania do tworzenia niestandardowych mapy bitowej efekty, zobacz [niezarządzane efekt mapy bitowej WPF](https://msdn.microsoft.com/library/ms735092.aspx) dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [Efekt mapy bitowej niezarządzane WPF](https://msdn.microsoft.com/library/ms735092.aspx)  
 [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Zabezpieczenia](../../../../docs/framework/wpf/security-wpf.md)  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
