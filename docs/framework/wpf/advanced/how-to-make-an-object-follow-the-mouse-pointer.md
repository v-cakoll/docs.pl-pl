---
title: Jak sprawić, aby obiekt podążał za wskaźnikiem myszy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005066"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Jak sprawić, aby obiekt podążał za wskaźnikiem myszy
Ten przykład pokazuje, jak zmienić wymiary obiektu po przesunięciu wskaźnika myszy na ekranie.  
  
 Przykład zawiera plik [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], który tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i plik związany z kodem, który tworzy program obsługi zdarzeń.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML tworzy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], która składa się z <xref:System.Windows.Shapes.Ellipse> w <xref:System.Windows.Controls.StackPanel> i dołącza procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.UIElement.MouseMove>.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Poniższy kod w tle tworzy procedurę obsługi zdarzeń <xref:System.Windows.UIElement.MouseMove>.  Po przesunięciu wskaźnika myszy wysokość i szerokość <xref:System.Windows.Shapes.Ellipse> są zwiększane i zmniejszane.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd danych wejściowych](input-overview.md)
