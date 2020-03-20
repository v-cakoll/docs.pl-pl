---
title: Jak utworzyć tekst z cieniem
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186850"
---
# <a name="how-to-create-text-with-a-shadow"></a>Jak utworzyć tekst z cieniem
Przykłady w tej sekcji pokazują, jak utworzyć efekt cienia dla wyświetlanego tekstu.  
  
## <a name="example"></a>Przykład  
 Obiekt <xref:System.Windows.Media.Effects.DropShadowEffect> umożliwia tworzenie różnych efektów cienia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dla obiektów. W poniższym przykładzie przedstawiono efekt cienia zastosowany do tekstu. W tym przypadku cień jest miękkim cieniem, co oznacza, że kolor cienia się zaciera.  
  
 ![Cień tekstu z miękkością &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 Szerokość cienia można kontrolować, ustawiając <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwość. Wartość `4.0` wskazuje szerokość cienia 4 pikseli. Miękkość lub rozmycie cienia można kontrolować, <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> modyfikując właściwość. Wartość wskazuje, `0.0` że nie rozmycie. W poniższym przykładzie kodu pokazano, jak utworzyć cień miękki.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Te efekty cienia nie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przechodzą przez potok renderowania tekstu. W rezultacie ClearType jest wyłączona podczas korzystania z tych efektów.  
  
 W poniższym przykładzie przedstawiono efekt twardego cienia zastosowany do tekstu. W takim przypadku cień nie jest rozmyty.  
  
 ![Cień tekstu z miękkością &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 Twardy cień można utworzyć, <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> ustawiając `0.0`właściwość na , co oznacza, że nie jest używane rozmycie. Można kontrolować kierunek cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwość. Ustaw wartość kierunkową tej właściwości na `0` `360`stopień między . Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> wartości kierunkowe ustawienia właściwości.  
  
 ![Ustawienie stopnia DropShadow cienia](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 W poniższym przykładzie kodu pokazano, jak utworzyć twardy cień.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Korzystanie z efektu rozmycia  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> może służyć do tworzenia efektu podobnego do cienia, który można umieścić za obiektem tekstowym. Efekt rozmycia bitmapy zastosowanej do tekstu rozmywa tekst równomiernie we wszystkich kierunkach.  
  
 W poniższym przykładzie przedstawiono efekt rozmycia zastosowany do tekstu.  
  
 ![Cień tekstu przy użyciu efektu BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 W poniższym przykładzie kodu pokazano, jak utworzyć efekt rozmycia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Korzystanie z transformacji tłumaczenia  
 A <xref:System.Windows.Media.TranslateTransform> może służyć do tworzenia efektu podobnego do cienia, który można umieścić za obiektem tekstowym.  
  
 Poniższy przykład kodu <xref:System.Windows.Media.TranslateTransform> używa do przesunięcia tekstu. W tym przykładzie nieznacznie odsunięta kopia tekstu poniżej tekstu podstawowego tworzy efekt cienia.  
  
 ![Cień tekstu przy użyciu translatetransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 Poniższy przykład kodu pokazuje, jak utworzyć transformację dla efektu cienia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
