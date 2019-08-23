---
title: 'Instrukcje: Powiązywanie modułu definiowania układu z elementem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923494"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Instrukcje: Powiązywanie modułu definiowania układu z elementem
W tym przykładzie pokazano, jak programowo powiązać moduł definiowania układu z określonym <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Przykład  
 Aby powiązać moduł definiowania układu z konkretną <xref:System.Windows.UIElement>, wykonaj następujące kroki:  
  
1. Wywołaj `static` metodę <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> , aby <xref:System.Windows.Documents.AdornerLayer> uzyskaćobiekt<xref:System.Windows.UIElement> dla elementu do. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>wyszukuje drzewo wizualne, rozpoczynając od określonego elementu **UIElement**i zwraca początkową warstwę modułu definiowania układu. (Jeśli nie zostaną znalezione żadne warstwy modułu definiowania układu, metoda zwróci wartość null).  
  
2. Wywołaj <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z docelowym elementem **UIElement**.  
  
 Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej) z nazwanym <xref:System.Windows.Controls.TextBox> obiektem *TextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> Używanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do powiązania modułu definiowania układu z innym elementem nie jest obecnie obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Moduły indeksowania układu — omówienie](adorners-overview.md)
