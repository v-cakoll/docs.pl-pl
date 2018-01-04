---
title: "Inicjalizacja elementów obiektu poza drzewem obiektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5d617176852e72b4b46e48ff9a4528bec373272
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Inicjalizacja elementów obiektu poza drzewem obiektu
Niektóre aspekty [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] inicjowania są odroczone do procesów, które są zwykle oparte na elementu podłączonych do drzewa logicznego lub wizualnego drzewa. W tym temacie opisano kroki, które mogą być konieczne w celu zainicjowania elementu, który nie jest podłączony do obu drzewa.  
  
 
  
## <a name="elements-and-the-logical-tree"></a>Elementy i drzewie logicznym  
 Podczas tworzenia wystąpienia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasy w kodzie, należy zwrócić uwagę, że kilka aspektów obiekt inicjowania dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasy celowo nie są częścią kod, który jest wykonywany podczas wywoływania konstruktora klasy. Klasy formantu, szczególnie w przypadku większości wizualną reprezentację tego formantu nie jest zdefiniowany przez konstruktora. Zamiast tego wizualnej reprezentacji jest definiowana przez szablon formantu. Szablon potencjalnie pochodzą z różnych źródeł, ale najczęściej szablonu są uzyskiwane ze stylów motywu. Szablony są wydajnie późnego wiązania; niezbędne szablonu nie jest dołączony do danego formantu, dopóki formant jest gotowy do układu. I kontrolka nie jest gotowy do układu, dopóki nie jest podłączona do drzewa logicznego, który łączy powierzchnię renderowania w katalogu głównym. To tego elementu poziomu głównego, który inicjuje renderowania wszystkich jego elementów podrzędnych, zgodnie z definicją w drzewie logicznym.  
  
 Drzewa wizualnego jest również elementem tego procesu. Elementy, które są częścią drzewa wizualnego za pomocą szablonów są również nie są w pełni utworzona, aż do chwili podłączenia.  
  
 Konsekwencje tego zachowania są, że niektóre operacje, które opierają się na ukończone visual właściwości elementu wymagają dodatkowych czynności. Przykładem jest, jeśli próbujesz uzyskać visual właściwości klasy, które zostało utworzone, ale nie została jeszcze dołączony do drzewa. Na przykład jeśli chcesz wywołać <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> i element wizualny jest przekazywany jest elementem nie jest podłączony do drzewa, tego elementu nie została ukończona wizualnie, aż inicjowanie dodatkowych kroków.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Przy użyciu BeginInit i EndInit zainicjować Element  
 Różnych klas w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zaimplementować <xref:System.ComponentModel.ISupportInitialize> interfejsu. Możesz użyć <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> i <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> metod interfejsu do oznaczania regionu w swój kod, który zawiera kroki inicjowania (takie jak ustawienie właściwości wartości renderowania tego efektu domina). Po <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> jest wywoływana w sekwencji, system układu można przetworzyć elementu i rozpocząć wyszukiwanie informacji w stylu niejawnej.  
  
 Jeśli element właściwości są ustawiane na <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> pochodnej klasy, wówczas może wywołać wersje klasy <xref:System.Windows.FrameworkElement.BeginInit%2A> i <xref:System.Windows.FrameworkElement.EndInit%2A> zamiast rzutowania <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Przykładowy kod  
 Poniższy przykład jest przykładowy kod do aplikacji konsoli, która używa renderowania [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] i <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> z utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku do właściwego położenia zilustrowania <xref:System.Windows.FrameworkElement.BeginInit%2A> i <xref:System.Windows.FrameworkElement.EndInit%2A> wokół innych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wywołania właściwości, które mają wpływ na renderowanie który Dostosuj.  
  
 Główna funkcja pokazano w przykładzie. Funkcje `Rasterize` i `Save` (tego nie pokazano) to narzędzie funkcje zajmie się przetwarzania obrazów i we/wy.  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Zobacz też  
 [Drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
