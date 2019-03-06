---
title: 'Instrukcje: Powiąż moduł definiowania układu z elementem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: 4943121aaf8ee6524be3fc9004eafee4fa92e527
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353923"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Instrukcje: Powiąż moduł definiowania układu z elementem
W tym przykładzie pokazano, jak programowo powiązać moduł definiowania układu do określonego <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Przykład  
 Aby powiązać moduł definiowania układu do określonego <xref:System.Windows.UIElement>, wykonaj następujące kroki:  
  
1.  Wywołaj `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można pobrać <xref:System.Windows.Documents.AdornerLayer> dla obiektu <xref:System.Windows.UIElement> do być powiązany. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> przeprowadza górę drzewa wizualnego, rozpoczynając od określonego **UIElement**i zwraca pierwszą warstwą moduł definiowania układu kodu znajdzie. (Jeśli nie warstwy moduł definiowania układu kodu nie zostaną znalezione, metoda zwraca wartość null.)  
  
2.  Wywołaj <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z obiektem docelowym **UIElement**.  
  
 Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), aby <xref:System.Windows.Controls.TextBox> o nazwie *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać moduł definiowania układu z innego elementu nie jest obecnie obsługiwane.  
  
## <a name="see-also"></a>Zobacz także
- [Moduły indeksowania układu — omówienie](adorners-overview.md)
