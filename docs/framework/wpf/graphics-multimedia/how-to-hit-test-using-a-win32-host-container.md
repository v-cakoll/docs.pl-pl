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
ms.openlocfilehash: b71783f2d061c9139de4449d8e0106eb00345894
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740178"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Jak przeprowadzić test trafień za pomocą konteneru hosta Win32
Obiekty wizualne można tworzyć w oknie Win32, dostarczając kontener okna hosta dla obiektów wizualnych. Aby zapewnić obsługę zdarzeń dla zawartych obiektów wizualizacji, przetwarzasz komunikaty przesyłane do pętli filtru komunikatów kontenera okna hosta. Zapoznaj się z [samouczkiem: hosting obiektów wizualnych w aplikacji Win32,](tutorial-hosting-visual-objects-in-a-win32-application.md) Aby uzyskać więcej informacji na temat hostowania obiektów wizualizacji w oknie Win32.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, jak skonfigurować programy obsługi zdarzeń myszy dla okna Win32, które jest używane jako kontener hosta dla obiektów wizualnych.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Poniższy przykład pokazuje, jak skonfigurować test trafień w odpowiedzi na zalewkowanie określonych zdarzeń myszy.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Obiekt <xref:System.Windows.Interop.HwndSource> prezentuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartość w oknie Win32. Wartość właściwości <xref:System.Windows.Interop.HwndSource.RootVisual%2A> obiektu <xref:System.Windows.Interop.HwndSource> reprezentuje węzeł najwyższego poziomu w hierarchii drzewa wizualnego.  
  
 Aby zapoznać się z kompletnym przykładem przy testowaniu obiektów przy użyciu kontenera hosta Win32, zobacz [test trafień z funkcją międzyoperacyjności Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
- [Samouczek: hosting obiektów wizualnych w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
