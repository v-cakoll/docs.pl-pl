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
ms.openlocfilehash: b260f96246f0d9e5447b74a05e1396bfef176197
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053083"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Samouczek: hosting obiektów Visual w aplikacji Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje rozbudowane środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, może być bardziej efektywne dodać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji do aplikacji, zamiast ponownego zapisywania kodu. Aby zapewnić obsługę [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystemów grafiki jednocześnie używane w aplikacji, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia mechanizm hosting obiektów w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
 W tym samouczku opisano sposób pisania aplikacji przykładowej, [Test trafień Win32 — współdziałanie przykład](https://go.microsoft.com/fwlink/?LinkID=159995), które hosty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual obiekty w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  

<a name="requirements"></a>   
## <a name="requirements"></a>Wymagania  
 W tym samouczku założono podstawowe znajomość zarówno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania. Aby uzyskać wstęp do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programowania, zobacz [wskazówki: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Wprowadzenie do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programowania, zobacz dowolny wiele książek, które w szczególności na ten temat *programowania Windows* przez Charles Petzold.  
  
> [!NOTE]
>  Ten samouczek zawiera szereg przykładów kodu z próbki skojarzone. Jednak aby zwiększyć czytelność, nie obejmuje pełny przykładowy kod. Aby uzyskać kompletny przykładowy kod, zobacz [Test trafień Win32 — współdziałanie przykład](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Utworzenie okna hosta Win32  
 Kluczem do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno jest <xref:System.Windows.Interop.HwndSource> klasy. Ta klasa jest zawijany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, umożliwiając im należy włączyć do Twojej [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako okna podrzędnego.  
  
 Poniższy przykład przedstawia kod dla tworzenia <xref:System.Windows.Interop.HwndSource> obiektu jako [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno kontenera dla obiektów wizualnych. Aby ustawić styl okna, położenie i inne parametry [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oknie, użyj <xref:System.Windows.Interop.HwndSourceParameters> obiektu.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  Wartość <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> ws_ex_transparent — nie można ustawić właściwości. Oznacza to, że host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno nie może być przezroczysty. Z tego powodu kolor tła hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno jest ustawione na ten sam kolor tła jako okna nadrzędnego.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Dodawanie obiektów wizualnych do okna hosta Win32  
 Po utworzeniu hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno kontenera obiektów wizualnych obiektów wizualnych można dodać do niego. Można upewnić się, wszystkie przekształcenia obiektów wizualnych, np. animacji, nie zostanie rozszerzony poza granice hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna użytkownika prostokąt ograniczający.  
  
 Poniższy przykład przedstawia kod dla tworzenia <xref:System.Windows.Interop.HwndSource> obiektu i dodawanie obiektów wizualnych do niego.  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Właściwość <xref:System.Windows.Interop.HwndSource> obiekt jest ustawiony na pierwszy obiekt wizualny dodane do hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Obiekt wizualny głównego definiuje najważniejsze węzeł drzewa obiektów wizualnych. Kolejne obiektów wizualnych dodane do hosta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna są dodawane jako obiekty podrzędne.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementowanie filtr komunikatu Win32  
 Host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dla obiektów wizualnych wymaga procedury filtru komunikat w oknie do obsługi komunikatów, które są wysyłane do okna z kolejki aplikacji. Procedurę okna odbiera komunikaty z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] systemu. Mogą to być komunikaty wejściowe lub Zarządzanie oknem wiadomości. Możesz opcjonalnie obsługi wiadomości w Twojej procedurę okna lub przekazać komunikat do systemu pod kątem przetwarzania domyślne.  
  
 <xref:System.Windows.Interop.HwndSource> Obiekt, który jest zdefiniowany jako element nadrzędny obiektów wizualnych musi odwoływać się do procedury filtru okno komunikatu, należy podać. Po utworzeniu <xref:System.Windows.Interop.HwndSource> obiektu, należy ustawić <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> właściwości w celu odwołania procedurę okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Poniższy przykład pokazuje kod dla przycisku myszy w lewy i prawy komunikaty obsługi. Wartość współrzędnych myszy trafień pozycja jest zawarty w wartości `lParam` parametru.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Przetwarzanie komunikatów Win32  
 W kodzie, w poniższym przykładzie pokazano, jak hit test jest wykonywane względem hierarchii obiektów wizualnych znajdujących się na hoście [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Można zidentyfikować, czy punkt znajduje się w geometrię obiektu visual przy użyciu <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę, aby określić obiekt wizualny głównego i współrzędnych wartość, aby trafić Testuj pod względem. W tym przypadku obiekt wizualny główny jest wartością <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource> obiektu.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Aby uzyskać więcej informacji na temat testowania trafień względem obiektów wizualnych, zobacz [trafień testowania w warstwie wizualnej](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [Hit Test przykład współdziałanie Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
