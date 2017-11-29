---
title: "Jak utworzyć tekst z cieniem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bbc3da54c10304e52f93d38365a8d9ed005505
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a>Jak utworzyć tekst z cieniem
Przykłady w tej sekcji pokazano, jak utworzyć efekt cieniowania dla wyświetlanego tekstu.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Effects.DropShadowEffect> Obiektu służy do tworzenia różnych spadku efektów cienia do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektów. W poniższym przykładzie przedstawiono efektem cienia tekstu. W takim przypadku cień jest cienia miękkie, co oznacza rozmywa kolor cienia.  
  
 ![Cień tekstu z miękkości &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Przykład tekstu w tle elastyczne  
  
 Szerokość cienia można kontrolować przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwości. Wartość `4.0` wskazuje na tle szerokości 4 pikseli. Można kontrolować miękkość, lub rozmycia cienia modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości. Wartość `0.0` wskazuje nie rozmycia. Poniższy przykład kodu pokazuje, jak utworzyć nietrwałego cienia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Te efekty cienia przechodzi przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] potoku renderowania tekstu. W związku z tym ClearType jest wyłączona, korzystając z tych skutków.  
  
 W poniższym przykładzie przedstawiono twardych efektem cienia tekstu. W takim przypadku nie zostało rozmyte cienia.  
  
 ![Cień tekstu z miękkości &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")  
Przykład tekstu w tle twardych  
  
 Można utworzyć twardy cienia przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości `0.0`, co oznacza, że nie rozmycia jest używana. Można kontrolować kierunku cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwości. Ustaw kierunkową wartość tej właściwości w zakresie między `0` i `360`. Na poniższej ilustracji przedstawiono wartości kierunkową <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> ustawienie właściwości.  
  
 ![Ustawienie stopnia cień tle](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
Diagram kierunek cień  
  
 Poniższy przykład kodu pokazuje, jak utworzyć twardy cienia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Za pomocą efektu rozmycia  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> może służyć do tworzenia efektu przypominającej tle, który można umieścić za obiektu tekstu. Efekt mapy bitowej rozmycia zastosowany do tekstu rozmywa tekst równomiernie we wszystkich kierunkach.  
  
 W poniższym przykładzie przedstawiono efekt rozmycia zastosowany do tekstu.  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Przykład tekstu z efektem rozmycia  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia efektu rozmycia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Przy użyciu translacji transformacji  
 A <xref:System.Windows.Media.TranslateTransform> może służyć do tworzenia efektu przypominającej tle, który można umieścić za obiektu tekstu.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> do Przesunięcie tekstu. W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efektem cienia.  
  
 ![Cień tekstu przy użyciu TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")  
Przykład przy użyciu transformacji dla efektu cienia tekstu  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia transformacji dla efektem cienia.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
