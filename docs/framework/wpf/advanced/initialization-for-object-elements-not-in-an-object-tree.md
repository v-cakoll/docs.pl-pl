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
ms.openlocfilehash: 1a1d956ee7f41ac1ac0fc9bd051a18b9ff438930
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459833"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Inicjalizacja elementów obiektu poza drzewem obiektu
Niektóre aspekty inicjalizacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] są odroczone do procesów, które zwykle polegają na tym elemencie połączonym z drzewem logicznym lub drzewem wizualnym. W tym temacie opisano kroki, które mogą być konieczne w celu zainicjowania elementu, który nie jest połączony z żadnym drzewem.  

## <a name="elements-and-the-logical-tree"></a>Elementy i Drzewo logiczne  
 Podczas tworzenia wystąpienia klasy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w kodzie należy pamiętać, że kilka aspektów inicjalizacji obiektów dla klasy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nie jest częścią kodu, który jest wykonywany podczas wywoływania konstruktora klasy. Szczególnie w przypadku klasy formantów większość wizualizacji wizualnych tej kontrolki nie jest definiowana przez konstruktora. Zamiast tego reprezentacja wizualna jest definiowana przez szablon kontrolki. Szablon może pochodzić z różnych źródeł, ale najczęściej szablon jest uzyskiwany ze stylów motywu. Szablony są efektywnie późne. wymagany szablon nie jest dołączony do kontrolki, dopóki kontrolka nie będzie gotowa do układu. I formant nie jest gotowy do układu, dopóki nie zostanie dołączony do drzewa logicznego, które nawiązuje połączenie z powierzchnią renderowania w katalogu głównym. Jest to ten element poziomu głównego, który inicjuje renderowanie wszystkich elementów podrzędnych zgodnie z definicją w drzewie logicznym.  
  
 Drzewo wizualne uczestniczy również w tym procesie. Elementy, które są częścią drzewa wizualnego za pomocą szablonów, również nie są w pełni tworzone do momentu połączenia.  
  
 Konsekwencje tego zachowania polegają na tym, że niektóre operacje, które opierają się na zakończonych cechach wizualnych elementu, wymagają dodatkowych kroków. Przykładem jest to, że próbujesz uzyskać charakterystykę wizualną klasy, która została skonstruowana, ale jeszcze nie dołączona do drzewa. Na przykład jeśli chcesz wywołać <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> na <xref:System.Windows.Media.Imaging.RenderTargetBitmap>, a Wizualizacja, którą przekazujesz, jest elementem niepołączonym z drzewem, ten element nie zostanie wykonany wizualnie do momentu ukończenia dodatkowych kroków inicjalizacji.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Korzystanie z BeginInit i EndInit w celu zainicjowania elementu  
 Różne klasy w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementują interfejs <xref:System.ComponentModel.ISupportInitialize>. Za pomocą metod <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> i <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> interfejsu można zwrócić uwagę na region w kodzie, który zawiera kroki inicjowania (takie jak ustawienie wartości właściwości, które wpływają na renderowanie). Po wywołaniu <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> w sekwencji, system układu może przetworzyć element i rozpocząć wyszukiwanie stylu niejawnego.  
  
 Jeśli element, którego właściwości są ustawiane, jest <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> klasie pochodnej, można wywołać wersje klasy <xref:System.Windows.FrameworkElement.BeginInit%2A> i <xref:System.Windows.FrameworkElement.EndInit%2A> zamiast rzutowania na <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Przykładowy kod  
 Poniższy przykład to przykładowy kod dla aplikacji konsolowej, która używa renderowania interfejsów API i <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> luźnego pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aby zilustrować odpowiednie rozmieszczenie <xref:System.Windows.FrameworkElement.BeginInit%2A> i <xref:System.Windows.FrameworkElement.EndInit%2A> wokół innych wywołań interfejsu API, które dostosowują właściwości, które wpływają na renderowanie.  
  
 Przykład ilustruje tylko główną funkcję. Funkcje `Rasterize` i `Save` (niepokazywany) są funkcjami narzędzi, które zapoznają się z przetwarzaniem obrazów i we/wy.  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Zobacz także

- [Drzewa w WPF](trees-in-wpf.md)
- [Renderowanie grafiki WPF — przegląd](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
