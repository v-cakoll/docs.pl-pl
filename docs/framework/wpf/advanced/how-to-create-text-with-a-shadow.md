---
title: 'Instrukcje: Tworzenie tekstu z cieniem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960444"
---
# <a name="how-to-create-text-with-a-shadow"></a>Instrukcje: Tworzenie tekstu z cieniem
W przykładach w tej sekcji pokazano, jak utworzyć efekt cieniowania wyświetlanego tekstu.  
  
## <a name="example"></a>Przykład  
 Obiekt umożliwia tworzenie różnorodnych efektów cienia dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektów. <xref:System.Windows.Media.Effects.DropShadowEffect> W poniższym przykładzie pokazano efekt cieniowania stosowany do tekstu. W tym przypadku cień jest miękką cienią, co oznacza, że kolor cienia jest zamazany.  
  
 ![Cień tekstu z miękką &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 Szerokość cienia można kontrolować przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwości. Wartość `4.0` wskazuje szerokość cienia wynoszącą 4 piksele. Możesz kontrolować miękkość lub rozmycie cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwość. Wartość nie wskazuje `0.0` na rozmyte. Poniższy przykład kodu pokazuje, jak utworzyć miękki cień.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Te efekty cienia nie przechodzą przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] potok renderowania tekstu. W związku z tym technologia ClearType jest wyłączona podczas korzystania z tych efektów.  
  
 Poniższy przykład pokazuje efekt trwałego cienia zastosowany do tekstu. W takim przypadku cień nie jest rozmyty.  
  
 ![Cień tekstu z niemiękką &#61; wartością 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 Można utworzyć twardą cień przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości na `0.0`, która wskazuje, że nie jest używane rozmycie. Kierunek cienia można kontrolować, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwość. Ustaw wartość kierunkową tej właściwości na poziom między `0` i. `360` Na poniższej ilustracji przedstawiono wartości <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> kierunkowe ustawienia właściwości.  
  
 ![Ustawienie stopnia DropShadow cienia](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 Poniższy przykład kodu pokazuje, jak utworzyć cień twardy.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Używanie efektu rozmycia  
 <xref:System.Windows.Media.Effects.BlurBitmapEffect> Można użyć do utworzenia efektu przypominającego cień, który może być umieszczony za obiektem tekstowym. Efekt mapy bitowej rozmywania stosowany do tekstu rozmywa tekst równomiernie we wszystkich kierunkach.  
  
 W poniższym przykładzie pokazano efekt rozmycia stosowany do tekstu.  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 Poniższy przykład kodu pokazuje, jak utworzyć efekt rozmycia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Używanie transformacji tłumaczenia  
 <xref:System.Windows.Media.TranslateTransform> Można użyć do utworzenia efektu przypominającego cień, który może być umieszczony za obiektem tekstowym.  
  
 Poniższy przykład kodu używa <xref:System.Windows.Media.TranslateTransform> do przesunięcia tekstu. W tym przykładzie nieznacznie przesunięta kopia tekstu poniżej podstawowego tekstu tworzy efekt cienia.  
  
 ![Cień tekstu przy użyciu TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 Poniższy przykład kodu pokazuje, jak utworzyć transformację dla efektu cienia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
