---
title: 'Instrukcje: Przeprowadzanie testu trafienia za pomocą kontenera hosta Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: ac5cae5bcd94dc8bf80ff95b8971914e1fa5ba2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081466"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Instrukcje: Przeprowadzanie testu trafienia za pomocą kontenera hosta Win32
Można utworzyć obiektów wizualnych w ramach [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna, zapewniając hosta okna kontener dla obiektów wizualnych. Zapewnienie obsługi dla zawartych obiektów wizualnych zdarzeń można przetwarzać komunikaty przesyłane do kontenera okna hosta pętli komunikatów dla filtru. Zapoznaj się [samouczka: Hosting obiektów Visual w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) Aby uzyskać więcej informacji na temat sposobu obsługi obiektów wizualnych w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób konfigurowania obsługi zdarzeń myszy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, która jest używana jako kontenera hosta dla obiektów wizualnych.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Poniższy przykład pokazuje, jak skonfigurować hit test w odpowiedzi na generują pułapki zdarzeń myszy określone.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> Obiektu przedstawia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartość w ramach [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna. Wartość <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource> obiekt reprezentuje węzeł najważniejsze w hierarchii drzewa wizualnego.  
  
 Aby uzyskać pełny przykład testowania trafień obiektów za pomocą konteneru hosta Win32, zobacz [Test trafień Win32 — współdziałanie przykład](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
- [Samouczek: Hosting obiektów Visual w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
