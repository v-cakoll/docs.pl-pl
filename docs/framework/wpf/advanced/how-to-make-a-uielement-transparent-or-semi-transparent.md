---
title: 'Instrukcje: Uzyskaj przezroczystość lub półprzezroczystość elementu interfejsu użytkownika'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370530"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Instrukcje: Uzyskaj przezroczystość lub półprzezroczystość elementu interfejsu użytkownika
W tym przykładzie pokazano, jak wprowadzić <xref:System.Windows.UIElement> przezroczystym lub półprzezroczystym. Do uczynienia elementu przezroczystym lub półprzezroczystym, ustaw jego <xref:System.Windows.UIElement.Opacity%2A> właściwości. Wartość `0.0` sprawia, że element jest całkowicie przezroczysty podczas wartość `1.0` sprawia, że element jest całkowicie nieprzezroczysty. Wartość `0.5` sprawia, że element 50% nieprzezroczystych i tak dalej. Element <xref:System.Windows.UIElement.Opacity%2A> ustawiono `1.0` domyślnie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia <xref:System.Windows.UIElement.Opacity%2A> przycisku, aby `0.25`, co on i jego zawartości (w tym przypadku tekst przycisku) 25% nieprzezroczystości.  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Jeśli element zawartości mają swoje własne <xref:System.Windows.UIElement.Opacity%2A> ustawienia, te wartości są mnożone przed zawierającego elementy <xref:System.Windows.UIElement.Opacity%2A>.  
  
 W poniższym przykładzie ustawiono przycisku <xref:System.Windows.UIElement.Opacity%2A> do `0.25`i <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Image> kontroli zawarte w przycisk, aby `0.5`. W rezultacie obraz jest wyświetlany 12,5% nieprzezroczysty: 0.25 * 0.5 = 0.125.  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Innym sposobem na kontrolowanie nieprzezroczystość elementu jest aby ustawić nieprzezroczystość <xref:System.Windows.Media.Brush> , malowany element. Takie podejście umożliwia selektywne zmienić nieprzezroczystość części elementu oraz zapewnia korzyści w wydajności przy użyciu elementu <xref:System.Windows.UIElement.Opacity%2A> właściwości. Poniższy przykład ustawia <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> używany do rysowania przycisku <xref:System.Windows.Controls.Control.Background%2A> ustawiono `0.25`. W rezultacie pędzel tła jest 25% nieprzezroczyste, ale jego zawartość (tekst przycisku) pozostają nieprzezroczyste w 100%.  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Może także kontrolować nieprzezroczystość poszczególnych kolory pędzla. Aby uzyskać więcej informacji na temat kolorów i pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać przykład pokazujący sposób animować nieprzezroczystość elementu, zobacz [animować nieprzezroczystość elementu lub pędzla](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
