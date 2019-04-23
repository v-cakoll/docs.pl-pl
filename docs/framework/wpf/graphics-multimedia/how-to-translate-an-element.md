---
title: 'Instrukcje: Przesuwanie elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 9c1b873a89820e85efb99789f483c4832fb23cf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231191"
---
# <a name="how-to-translate-an-element"></a>Instrukcje: Przesuwanie elementu
W tym przykładzie pokazano, jak do tłumaczenia (przenoszenie) elementu za pomocą <xref:System.Windows.Media.TranslateTransform>.  
  
 <xref:System.Windows.Media.TranslateTransform> Klasa jest szczególnie przydatne w przypadku przenoszenia elementy wewnątrz paneli, które nie obsługują pozycjonowanie absolutne. Na przykład, stosując <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość elementu, można przenieść elementu z <xref:System.Windows.Controls.StackPanel> lub <xref:System.Windows.Controls.DockPanel>.  
  
 Użyj <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> Aby określić czas, w pikselach, aby przenieść element na osi x. Użyj <xref:System.Windows.Media.TranslateTransform.Y%2A> właściwość, aby określić czas, w pikselach, aby przenieść element wzdłuż osi y. Na koniec Zastosuj <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.TranslateTransform> aby przejść do kolejnego elementu 50 pikseli na prawo do 50 pikseli.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia — przegląd](transforms-overview.md)
