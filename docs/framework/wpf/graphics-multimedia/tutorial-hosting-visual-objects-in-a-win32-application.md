---
title: 'Samouczek: hosting obiektów Visual w aplikacji Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: 621684e14f9d1b599c4ef60e3731f0f58f31aacd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740165"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Samouczek: hosting obiektów Visual w aplikacji Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia rozbudowane środowisko do tworzenia aplikacji. Jednakże, jeśli masz znaczną inwestycję w kod Win32, może być bardziej efektywne Dodawanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji do aplikacji zamiast pisania kodu. Aby zapewnić obsługę systemu Win32 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystemów graficznych używanych współbieżnie w aplikacji, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia mechanizm hostingu obiektów w oknie Win32.  
  
 W tym samouczku opisano sposób pisania przykładowej aplikacji, [test trafień z próbką międzyoperacyjną Win32](https://go.microsoft.com/fwlink/?LinkID=159995), który umożliwia hostowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów wizualnych w oknie Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawową wiedzę na temat programowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i środowiska Win32. Aby uzyskać podstawowe wprowadzenie do programowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Aby zapoznać się z wprowadzeniem do programowania Win32, zapoznaj się z wieloma książkami w temacie, w szczególności *programowaniem w systemie Windows* przez Charles Petzold.  
  
> [!NOTE]
> Ten samouczek zawiera wiele przykładów kodu ze skojarzonego przykładu. Jednak w celu zapewnienia czytelności nie obejmuje kompletny kod przykładowy. Aby uzyskać kompletny przykładowy kod, zobacz [test trafień z funkcją międzyoperacyjna Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Tworzenie okna Win32 hosta  
 Klucz służący do hostowania obiektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w oknie Win32 jest klasą <xref:System.Windows.Interop.HwndSource>. Ta klasa otacza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów w oknie Win32, umożliwiając ich dołączanie do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego.  
  
 Poniższy przykład pokazuje kod służący do tworzenia obiektu <xref:System.Windows.Interop.HwndSource> jako okno kontenera Win32 dla obiektów wizualnych. Aby ustawić styl okna, położenie i inne parametry okna Win32, użyj obiektu <xref:System.Windows.Interop.HwndSourceParameters>.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> Wartość właściwości <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> nie może być ustawiona na WS_EX_TRANSPARENT. Oznacza to, że okno Win32 hosta nie może być przezroczyste. Z tego powodu kolor tła okna Win32 hosta jest ustawiony na ten sam kolor tła, co okno nadrzędne.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Dodawanie obiektów wizualnych do okna Win32 hosta  
 Po utworzeniu okna kontenera Win32 dla obiektów wizualnych można dodać do niego obiekty wizualne. Należy upewnić się, że wszelkie przekształcenia obiektów wizualnych, takich jak animacje, nie wykraczają poza granice prostokąta ograniczonego okna Win32.  
  
 Poniższy przykład pokazuje kod służący do tworzenia obiektu <xref:System.Windows.Interop.HwndSource> i dodawania do niego obiektów wizualnych.  
  
> [!NOTE]
> Właściwość <xref:System.Windows.Interop.HwndSource.RootVisual%2A> obiektu <xref:System.Windows.Interop.HwndSource> jest ustawiana na pierwszy obiekt wizualny dodany do okna Win32 hosta. Główny obiekt wizualizacji definiuje najwyższy górny węzeł drzewa obiektów wizualnych. Wszystkie kolejne obiekty wizualne dodane do okna platformy Win32 są dodawane jako obiekty podrzędne.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementowanie filtru komunikatów Win32  
 Okno Win32 dla obiektów wizualnych wymaga procedury filtru komunikatów systemu Windows do obsługi komunikatów wysyłanych do okna z kolejki aplikacji. Procedura okna odbiera komunikaty z systemu Win32. Mogą to być komunikaty wejściowe lub komunikaty zarządzania oknem. Opcjonalnie możesz obsłużyć komunikat w procedurze okna lub przekazać komunikat do systemu w celu przetworzenia domyślnego.  
  
 Obiekt <xref:System.Windows.Interop.HwndSource>, który został zdefiniowany jako element nadrzędny dla obiektów wizualizacji, musi odwoływać się do podania procedury filtru komunikatów systemu Windows. Podczas tworzenia obiektu <xref:System.Windows.Interop.HwndSource> ustaw właściwość <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>, aby odwoływała się do procedury okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Poniższy przykład pokazuje kod do obsługi komunikatów lewego i prawego przycisku myszy. Wartość współrzędnej pozycji trafień myszy jest zawarta w wartości parametru `lParam`.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Przetwarzanie komunikatów Win32  
 Kod w poniższym przykładzie pokazuje, jak test trafień jest wykonywany względem hierarchii obiektów wizualizacji zawartych w oknie Win32 hosta. Można określić, czy punkt znajduje się w geometrii obiektu wizualizacji, za pomocą metody <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>, aby określić główny obiekt wizualizacji i wartość współrzędnej, względem której ma zostać trafiony test. W takim przypadku główny obiekt wizualny jest wartością właściwości <xref:System.Windows.Interop.HwndSource.RootVisual%2A> obiektu <xref:System.Windows.Interop.HwndSource>.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Aby uzyskać więcej informacji na temat testowania trafień względem obiektów wizualnych, zobacz [testowanie trafień w warstwie wizualnej](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [Test trafień z próbką międzyoperacyjną Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
