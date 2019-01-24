---
title: Inicjalizacja elementów obiektu poza drzewem obiektu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: ed1f7781453503682648d740b57dd7af0a1715c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524133"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Inicjalizacja elementów obiektu poza drzewem obiektu
Niektóre aspekty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] inicjowania mają być opóźniane do procesów, które są zwykle oparte na ten element jest podłączony do drzewa logicznego lub drzewa wizualnego. W tym temacie opisano kroki, które mogą być wymagane, aby zainicjować element, który nie jest podłączony do obu drzewa.  
  
 
  
## <a name="elements-and-the-logical-tree"></a>Elementy i drzewo logiczne  
 Po utworzeniu wystąpienia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasy w kodzie, należy pamiętać, że różne aspekty tego obiektu inicjowanie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasy celowo nie są częścią kodu, który jest wykonywany podczas wywoływania konstruktora klasy. Szczególnie w przypadku klasy kontrolki większość wizualnej reprezentacji tej kontrolki nie jest zdefiniowany przez konstruktora. Wizualna reprezentacja jest zdefiniowany przez szablon kontrolki. Szablon potencjalnie pochodzą z różnych źródeł, ale w większości przypadków szablonu są uzyskiwane ze stylów motywu. Szablony są wydajnie późnego wiązania; niezbędne szablonu nie jest dołączony do danego kontroli, aż formant będzie gotowa do układu. I kontrolki nie jest gotowa do układu, dopóki nie jest on dołączony do drzewa logicznego, który nawiązuje połączenie z powierzchnię renderowania w katalogu głównym. Jest ten element poziomu głównego, który inicjuje wszystkie jego elementy podrzędne renderowania, zgodnie z definicją w drzewie logicznym.  
  
 Drzewo wizualne również uczestniczy w ramach tego procesu. Elementy, które są częścią drzewa wizualnego, za pomocą szablonów również nie są w pełni są tworzone, aż do chwili podłączenia.  
  
 Konsekwencje tego zachowania to, że niektórych operacji, które opierają się na ukończone visual właściwości elementu wymagają wykonania dodatkowych czynności. Przykładem jest, jeśli próbujesz pobrać visual cech klasy, które zostało wykonane, ale nie są jeszcze dołączone do drzewa. Na przykład jeśli chcesz wywołać <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> i wizualizacji, które przekazujesz jest elementem nie jest podłączony do drzewa tego elementu nie zostało zakończone wizualnie, aż inicjowanie dodatkowych kroków.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Przy użyciu BeginInit i EndInit, aby zainicjować Element  
 Różnymi klasami w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zaimplementować <xref:System.ComponentModel.ISupportInitialize> interfejsu. Możesz użyć <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> i <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> metody interfejsu, aby wskazać region, w kodzie, które zawiera kroków inicjowania (takie jak ustawienie właściwości wartości tego renderowanie wpływ). Po <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> jest wywoływana w sekwencji, system układu można przetworzyć elementu i rozpoczęcia wyszukiwania stylu niejawnego.  
  
 Jeśli element właściwości są ustawiane na <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> pochodne klasy, wówczas może wywołać klasy wersje <xref:System.Windows.FrameworkElement.BeginInit%2A> i <xref:System.Windows.FrameworkElement.EndInit%2A> zamiast rzutowania <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Przykładowy kod  
 Poniższy przykład przedstawia przykładowy kod dla aplikacji konsoli, która korzysta z renderowania [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] i <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> luzem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku, aby zilustrować właściwe rozmieszczenie <xref:System.Windows.FrameworkElement.BeginInit%2A> i <xref:System.Windows.FrameworkElement.EndInit%2A> wokół nawzajem [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wywołania właściwości, które wpływają na renderowanie, Dostosuj.  
  
 W przykładzie pokazano tylko funkcji main. Funkcje `Rasterize` i `Save` (niewyświetlany) są funkcje narzędzia, które powinien zachować ostrożność, przetwarzanie obrazu i we/wy.  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Zobacz także
- [Drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
- [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
