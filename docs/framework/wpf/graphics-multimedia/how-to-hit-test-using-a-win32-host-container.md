---
title: "Jak przeprowadzić test trafień za pomocą konteneru hosta Win32"
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
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a5cb77a53cbb106593b70d618bab67ef816e901
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Jak przeprowadzić test trafień za pomocą konteneru hosta Win32
Można utworzyć obiekty widoczne w [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna, podając hosta okna kontenera obiektów visual. Zapewnienie obsługi dla zawarte obiekty visual zdarzeń proces wiadomości przekazany do pętli filtru komunikatów kontenera okno hosta. Zapoznaj się [samouczek: hostingu Visual obiektów w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) Aby uzyskać więcej informacji na temat sposobu obsługi obiektów visual [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób konfigurowania obsługi zdarzeń myszy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, która służy jako kontener hosta dla obiektów visual.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Poniższy przykład pokazuje, jak skonfigurować testu trafienia w odpowiedzi na generują pułapki myszy określonych zdarzeń.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> Przedstawia obiektu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartości w ramach [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna. Wartość <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource> obiekt reprezentuje najwyższy węzeł w hierarchii w drzewie wizualnym.  
  
 Dla kompletnego przykładu testowania trafień obiekty przy użyciu kontenera hosta Win32, zobacz [trafień testu z przykładowych współdziałanie Win32](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndSource>  
 [Testowanie w warstwie Visual trafień](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Samouczek: Hostingu Visual obiektów w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
