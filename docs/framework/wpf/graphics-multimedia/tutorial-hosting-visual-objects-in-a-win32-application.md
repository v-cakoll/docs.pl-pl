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
ms.openlocfilehash: c8baefbf01467a65626a77f300f34a145d5c7281
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962874"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Samouczek: hosting obiektów Visual w aplikacji Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje bogate środowisko do tworzenia aplikacji. Jeśli jednak masz znaczną inwestycję w [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kod, bardziej efektywne może być dodanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji do aplikacji zamiast ponownego pisania kodu. Aby zapewnić obsługę [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] systemu i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystemów graficznych używanych współbieżnie w aplikacji, program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] udostępnia mechanizm hostingu obiektów w oknie.  
  
 W tym samouczku opisano sposób pisania przykładowej aplikacji, [test trafień z próbką](https://go.microsoft.com/fwlink/?LinkID=159995)międzyoperacyjną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32, który hostuje obiekty [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] wizualizacji w oknie.  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawową znajomość obu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania. Aby zapoznać się z podstawowymi wprowadzeniem [do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania, zobacz Przewodnik: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md)klasyczna WPF. Aby zapoznać się z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] wprowadzeniem do programowania, zapoznaj się z wieloma książkami w temacie, w szczególności *programowaniem systemu Windows* przez Charles Petzold.  
  
> [!NOTE]
> Ten samouczek zawiera wiele przykładów kodu ze skojarzonego przykładu. Jednak w celu zapewnienia czytelności nie obejmuje kompletny kod przykładowy. Aby uzyskać kompletny przykładowy kod, zobacz [test trafień z funkcją międzyoperacyjna Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Tworzenie okna Win32 hosta  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie jest <xref:System.Windows.Interop.HwndSource> Klasa. Ta klasa otacza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie, umożliwiając ich dołączanie do swojego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okna jako elementu podrzędnego.  
  
 Poniższy przykład pokazuje kod służący do tworzenia <xref:System.Windows.Interop.HwndSource> obiektu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] jako okno kontenera dla obiektów wizualnych. Aby ustawić styl okna, położenie i inne parametry [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, <xref:System.Windows.Interop.HwndSourceParameters> Użyj obiektu.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> Wartość <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> właściwości nie może być ustawiona na WS_EX_TRANSPARENT. Oznacza to, że okno [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hosta nie może być przezroczyste. Z tego powodu kolor tła okna hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] jest ustawiony na ten sam kolor tła, co okno nadrzędne.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Dodawanie obiektów wizualnych do okna Win32 hosta  
 Po utworzeniu okna kontenera hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dla obiektów wizualnych można dodać do niego obiekty wizualne. Należy upewnić się, że wszelkie przekształcenia obiektów wizualizacji, takich jak animacje, nie wykraczają poza granice prostokąta ograniczonego okna hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] .  
  
 Poniższy przykład pokazuje kod służący do tworzenia <xref:System.Windows.Interop.HwndSource> obiektu i dodawania do niego obiektów wizualnych.  
  
> [!NOTE]
> Właściwość obiektu jest ustawiana na pierwszy obiekt wizualny dodany do okna hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> Główny obiekt wizualizacji definiuje najwyższy górny węzeł drzewa obiektów wizualnych. Wszystkie kolejne obiekty wizualne dodane do okna hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] są dodawane jako obiekty podrzędne.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementowanie filtru komunikatów Win32  
 Okno hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dla obiektów wizualnych wymaga procedury filtru komunikatów systemu Windows do obsługi komunikatów wysyłanych do okna z kolejki aplikacji. Procedura okna odbiera komunikaty z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] systemu. Mogą to być komunikaty wejściowe lub komunikaty zarządzania oknem. Opcjonalnie możesz obsłużyć komunikat w procedurze okna lub przekazać komunikat do systemu w celu przetworzenia domyślnego.  
  
 <xref:System.Windows.Interop.HwndSource> Obiekt, który został zdefiniowany jako element nadrzędny dla obiektów wizualizacji, musi odwoływać się do podania procedury filtru komunikatów systemu Windows. Podczas tworzenia <xref:System.Windows.Interop.HwndSource> obiektu należy <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> ustawić właściwość, aby odwoływała się do procedury okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Poniższy przykład pokazuje kod do obsługi komunikatów lewego i prawego przycisku myszy. Wartość współrzędnej pozycji trafień myszy jest zawarta w wartości `lParam` parametru.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Przetwarzanie komunikatów Win32  
 Kod w poniższym przykładzie pokazuje, jak test trafień jest wykonywany względem hierarchii obiektów wizualizacji zawartych w oknie hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] . Można określić, czy punkt znajduje się w geometrii obiektu wizualizacji, przy użyciu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody do określenia głównego obiektu wizualizacji i wartości współrzędnych, względem których ma zostać trafiony test. W takim przypadku główny obiekt wizualny jest wartością <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwości <xref:System.Windows.Interop.HwndSource> obiektu.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Aby uzyskać więcej informacji na temat testowania trafień względem obiektów wizualnych, zobacz [testowanie trafień w warstwie wizualnej](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [Test trafień z próbką międzyoperacyjną Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
