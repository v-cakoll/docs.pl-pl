---
title: 'Instrukcje: Utwórz tekst z cieniem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 4d200aa980e8f2e6d22291669dfb07db54a5f0c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370686"
---
# <a name="how-to-create-text-with-a-shadow"></a>Instrukcje: Utwórz tekst z cieniem
Przykłady w tej sekcji pokazano, jak utworzyć efekt dla tekstu wyświetlanego w tle.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Effects.DropShadowEffect> Obiektu służy do tworzenia różnych upuszczania efekty dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektów. Poniższy przykład pokazuje efektem cienia tekstu. W tym przypadku cień jest elastyczne w tle, co oznacza rozmywa kolor cienia.  
  
 ![Cień tekstu z miękkości &#61; 0,25](./media/shadowtext01.jpg "ShadowText01")  
Przykład tekstu z cieniem miękkie  
  
 Szerokość w tle można kontrolować przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwości. Wartość `4.0` wskazuje 4 pikseli szerokości w tle. Można kontrolować miękkość, lub Rozmycie cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości. Wartość `0.0` wskazuje nie Rozmycie. Poniższy przykład kodu pokazuje sposób tworzenia nietrwałego w tle.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Efekty cieniowania te nie odbywają się za pośrednictwem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] potoku renderowania tekstu. W rezultacie ClearType jest wyłączona, korzystając z tych skutków.  
  
 Poniższy przykład pokazuje twardych efektem cienia tekstu. W tym przypadku nie zostało rozmyte cienia.  
  
 ![Cień tekstu z miękkości &#61; 0](./media/shadowtext02.jpg "ShadowText02")  
Przykład tekstu z cieniem twarde  
  
 Utworzyć twardy w tle, ustawiając <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości `0.0`, co oznacza, że Rozmycie nie jest używany. Możesz kontrolować kierunku cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwości. Ustaw kierunkowe wartość tej właściwości w zakresie między `0` i `360`. Na poniższej ilustracji przedstawiono wartości kierunkowe <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> ustawienie właściwości.  
  
 ![Ustawienie stopnia DropShadow w tle](./media/shadowtext08.png "ShadowText08")  
Kierunek DropShadow diagramu  
  
 Poniższy przykład kodu pokazuje, jak utworzyć twardy w tle.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Przy użyciu efektu rozmycia  
 Element <xref:System.Windows.Media.Effects.BlurBitmapEffect> może służyć do tworzenia efekt podobne w tle, który można umieścić za obiektem tekstu. Efekt mapy bitowej Rozmycie tekstu rozmywa tekst równomiernie we wszystkich kierunkach.  
  
 Poniższy przykład przedstawia efekt rozmycia tekstu.  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")  
Przykład tekstu przy użyciu efektu rozmycia  
  
 W poniższym przykładzie kodu pokazano, jak utworzyć efekt Rozmycie.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Za pomocą przekład — przekształcenie  
 Element <xref:System.Windows.Media.TranslateTransform> może służyć do tworzenia efekt podobne w tle, który można umieścić za obiektem tekstu.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> na przesunięcie tekstu. W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efekt w tle.  
  
 ![Cień tekstu przy użyciu TranslateTransform](./media/shadowtext07.jpg "ShadowText07")  
Przykład tekstu przy użyciu transformacji dla efektu w tle  
  
 Poniższy przykład kodu pokazuje sposób tworzenia transformacji dla efektu w tle.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
