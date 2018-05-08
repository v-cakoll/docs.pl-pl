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
ms.openlocfilehash: cc78dfd22b0ad2726ce8870a4e03f539ec691d85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Samouczek: hosting obiektów Visual w aplikacji Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczących inwestycji [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, może być bardziej skuteczne dodać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje do aplikacji, zamiast ponownego zapisywania kodu. Aby zapewnić obsługę [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystemów grafiki jednocześnie używane w aplikacji, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia mechanizm obsługi obiektów w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
 Ten przewodnik opisuje sposób tworzenia aplikacji przykładowej, [trafień testu z przykładowych współdziałanie Win32](http://go.microsoft.com/fwlink/?LinkID=159995), że hosty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual obiekty w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  

  
<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawowa znajomość zarówno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania. Podstawowe wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania, zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Aby obejrzeć wprowadzenie do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania, zobacz dowolny wiele książek na ten temat, w szczególności *programowania Windows* przez Petzold Charlesa.  
  
> [!NOTE]
>  Ten samouczek zawiera szereg przykłady kodu z skojarzone próbki. Jednak aby zwiększyć czytelność, go nie ma kompletnego przykładowego kodu. Zakończenie przykładowy kod, zobacz [trafień testu z przykładowych współdziałanie Win32](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Utworzenie okna Win32 hosta  
 Klucz do hostingu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno jest <xref:System.Windows.Interop.HwndSource> klasy. Ta klasa jest zawijana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, dzięki czemu można włączyć do Twojej [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego.  
  
 W poniższym przykładzie przedstawiono kod służący do tworzenia <xref:System.Windows.Interop.HwndSource> obiekt jako [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna kontenera obiektów visual. Aby ustawić styl okna, położenie i inne parametry [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, użyj <xref:System.Windows.Interop.HwndSourceParameters> obiektu.  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  Wartość <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> ws_ex_transparent — nie można ustawić właściwości. Oznacza to, że host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno nie może być przezroczysty. Z tego powodu kolor tła hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno ma ustawioną wartość taki sam jak jej okna nadrzędnego kolor tła.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Dodawanie obiektów Visual dla okna Win32 hosta  
 Po utworzeniu hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna kontenera obiektów visual dla obiekt visual można dodać do niego. Będzie konieczne zapewnienie wszelkie przekształcenia visual obiekty, takie jak animacji, nie zostanie rozszerzony poza zakresem hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna do ograniczenia prostokąta.  
  
 W poniższym przykładzie przedstawiono kod służący do tworzenia <xref:System.Windows.Interop.HwndSource> obiektu i dodawanie obiektów visual do niego.  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Właściwość <xref:System.Windows.Interop.HwndSource> obiektu ma ustawioną wartość pierwszy obiekt visual dodane do hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Obiekt główny visual definiuje najwyższy węzeł drzewa obiektu visual. Wszystkie kolejne visual obiekty dodane do hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna są dodawane jako obiekty podrzędne.  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementacja filtru komunikatów Win32  
 Host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obiekty widoczne w oknie wymaga procedurę okna komunikatu filtr do obsługi komunikatów, które są wysyłane do okna z kolejki aplikacji. Procedurę okna odbiera komunikaty z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] systemu. Mogą to być komunikaty wejściowe lub komunikaty zarządzania systemem Windows. Można opcjonalnie obsługi wiadomości w odpowiedniej procedury okna lub przekazywania wiadomości w systemie przetwarzania domyślne.  
  
 <xref:System.Windows.Interop.HwndSource> Obiekt, który jest zdefiniowany jako elementu nadrzędnego dla obiekt visual musi odwoływać się podanie procedury filtru okno komunikatu. Po utworzeniu <xref:System.Windows.Interop.HwndSource> obiekt, ustaw <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> właściwości, aby odwołać procedurę okna.  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Poniższy przykład zawiera kod obsługi przycisku myszy w lewy i prawy zapasowych wiadomości. Wartość współrzędnych myszy trafień pozycja jest zawarty w wartości `lParam` parametru.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Przetwarzanie komunikatów Win32  
 Kod w poniższym przykładzie prezentuje realizację testu trafienia względem hierarchii visual obiektów zawartych w hoście [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Można określić, czy punkt znajduje się w geometrii obiektu visual przy użyciu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę, aby określić obiekt wizualny głównego i współrzędnych wartość do testowania przed trafienia. W takim przypadku główny obiekt visual jest wartość <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource> obiektu.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Aby uzyskać więcej informacji na temat testowania trafień względem obiektów visual, zobacz [trafień testowania w warstwie Visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndSource>  
 [Kliknij przycisk Test z przykładowych współdziałanie Win32](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Test trafienia w warstwie wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
