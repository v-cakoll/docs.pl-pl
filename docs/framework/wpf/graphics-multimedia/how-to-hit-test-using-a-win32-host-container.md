---
title: Jak przeprowadzić test trafień za pomocą konteneru hosta Win32
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: bb175e0f8aeb126b7f7fa85d5af1c4afcf5bea61
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46585283"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Jak przeprowadzić test trafień za pomocą konteneru hosta Win32
Można utworzyć obiektów wizualnych w ramach [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna, zapewniając hosta okna kontener dla obiektów wizualnych. Zapewnienie obsługi dla zawartych obiektów wizualnych zdarzeń można przetwarzać komunikaty przesyłane do kontenera okna hosta pętli komunikatów dla filtru. Zapoznaj się [samouczek: Hosting obiektów Visual w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) Aby uzyskać więcej informacji na temat sposobu obsługi obiektów wizualnych w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób konfigurowania obsługi zdarzeń myszy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, która jest używana jako kontenera hosta dla obiektów wizualnych.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Poniższy przykład pokazuje, jak skonfigurować hit test w odpowiedzi na generują pułapki zdarzeń myszy określone.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> Obiektu przedstawia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartość w ramach [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna. Wartość <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource> obiekt reprezentuje węzeł najważniejsze w hierarchii drzewa wizualnego.  
  
 Aby uzyskać pełny przykład testowania trafień obiektów za pomocą konteneru hosta Win32, zobacz [Test trafień Win32 — współdziałanie przykład](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndSource>  
 [Test trafienia w warstwie wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Samouczek: hosting obiektów wizualnych w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
