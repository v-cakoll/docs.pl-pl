---
title: "Jak uzyskać przezroczystość lub półprzezroczystość elementu interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec35ae2e064acf78d1165f64ce8c9e34b153299d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Jak uzyskać przezroczystość lub półprzezroczystość elementu interfejsu użytkownika
W tym przykładzie pokazano, jak utworzyć <xref:System.Windows.UIElement> przezroczysty lub półprzezroczysty. Do uczynienia elementu przezroczystym lub półprzezroczystym, ustaw jej <xref:System.Windows.UIElement.Opacity%2A> właściwości. Wartość `0.0` powoduje, że element jest całkowicie przezroczysty podczas wartość `1.0` powoduje, że element jest całkowicie przezroczystości. Wartość `0.5` powoduje, że element 50% nieprzezroczystych i tak dalej. Element <xref:System.Windows.UIElement.Opacity%2A> ustawiono `1.0` domyślnie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.UIElement.Opacity%2A> przycisku do `0.25`, ustawianie zawartością (w tym przypadku tekst przycisku) 25% nieprzezroczystego.  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Jeśli element zawartości mają swoje własne <xref:System.Windows.UIElement.Opacity%2A> ustawienia, te wartości są mnożone przed zawierającego elementy <xref:System.Windows.UIElement.Opacity%2A>.  
  
 Poniższy przykład przedstawia przycisk <xref:System.Windows.UIElement.Opacity%2A> do `0.25`i <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Image> kontroli objętych przycisk, aby `0.5`. W związku z tym obraz pojawia się 12,5% nieprzezroczyste: 0,25 * 0,5 = 0,125.  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Innym sposobem kontrolować nieprzezroczystość elementu jest skonfigurowanie nieprzezroczystość <xref:System.Windows.Media.Brush> który malowany element. Takie podejście umożliwia selektywne alter nieprzezroczystość części elementu i zapewnia korzyści wydajności w przypadku elementu <xref:System.Windows.UIElement.Opacity%2A> właściwości. W poniższym przykładzie <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> używana do malowania przycisku <xref:System.Windows.Controls.Control.Background%2A> ma ustawioną wartość `0.25`. W związku z tym pędzel tła jest 25% nieprzezroczyste, przy zachowaniu jego zawartości (tekst przycisku) przezroczystości 100%.  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Może też kontrolować nieprzezroczystość poszczególnych kolorów w pędzla. Aby uzyskać więcej informacji na temat kolorów i pędzle, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Na przykład przedstawiający sposób Animuj przezroczystość elementu zobacz [Animuj przezroczystość pędzla lub Element](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
