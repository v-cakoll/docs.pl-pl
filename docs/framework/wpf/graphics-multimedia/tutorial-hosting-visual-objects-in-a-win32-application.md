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
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187426"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Samouczek: hosting obiektów Visual w aplikacji Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia bogate środowisko do tworzenia aplikacji. Jednak jeśli masz znaczne inwestycje w kod Win32, może [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] być bardziej skuteczne, aby dodać funkcje do aplikacji, a nie przepisać kod. Aby zapewnić obsługę win32 i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystemów graficznych używanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jednocześnie w aplikacji, zapewnia mechanizm hostowania obiektów w oknie Win32.  
  
 W tym samouczku opisano sposób pisania przykładowej aplikacji, [Hit Test z Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting), który obsługuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty wizualne w oknie Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Wymagania  
 W tym samouczku przyjęto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] założenie, że należy zapoznać się z programowaniem obu i win32. Aby uzyskać podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wprowadzenie do programowania, zobacz [Przewodnik: Moja pierwsza aplikacja komputerowa WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Aby zapoznać się z wprowadzeniem do programowania Win32, zobacz dowolną z licznych książek na ten temat, w szczególności *programowanie systemu Windows* charlesa Petzolda.  
  
> [!NOTE]
> Ten samouczek zawiera kilka przykładów kodu z skojarzonego przykładu. Jednak dla czytelności nie zawiera pełnego przykładowego kodu. Aby uzyskać pełny przykładowy kod, zobacz [Hit Test z Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a>Tworzenie okna Host Win32  
 Kluczem do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostowania obiektów w oknie <xref:System.Windows.Interop.HwndSource> Win32 jest klasa. Ta klasa zawija [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiekty w oknie Win32, dzięki [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] czemu mają być włączone do okna jako dziecko.  
  
 Poniższy przykład pokazuje kod do <xref:System.Windows.Interop.HwndSource> tworzenia obiektu jako okno kontenera Win32 dla obiektów wizualnych. Aby ustawić styl okna, położenie i inne parametry dla okna <xref:System.Windows.Interop.HwndSourceParameters> Win32, użyj obiektu.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> Wartość <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> właściwości nie można ustawić na WS_EX_TRANSPARENT. Oznacza to, że okno Win32 hosta nie może być przezroczyste. Z tego powodu kolor tła okna Win32 hosta jest ustawiony na ten sam kolor tła, co jego okno nadrzędne.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Dodawanie obiektów wizualnych do okna Win32 hosta  
 Po utworzeniu okna kontenera usługi Win32 hosta dla obiektów wizualnych można dodawać do niego obiekty wizualne. Należy upewnić się, że wszelkie przekształcenia obiektów wizualnych, takich jak animacje, nie wykraczają poza granice prostokąta ograniczonego okna hosta Win32.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Interop.HwndSource> kod do tworzenia obiektu i dodawania obiektów wizualnych do niego.  
  
> [!NOTE]
> Właściwość <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> obiektu jest ustawiona na pierwszy obiekt wizualny dodany do okna win32 hosta. Główny obiekt wizualny definiuje najwyżej najpopularniejszy węzeł drzewa obiektów wizualnych. Wszystkie kolejne obiekty wizualne dodane do okna win32 hosta są dodawane jako obiekty podrzędne.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a>Implementowanie filtru wiadomości w uichwale usługi Win32  
 Okno Win32 hosta dla obiektów wizualnych wymaga procedury filtrowania komunikatów okna do obsługi wiadomości, które są wysyłane do okna z kolejki aplikacji. Procedura okna odbiera komunikaty z systemu Win32. Mogą to być komunikaty wejściowe lub komunikaty zarządzania oknami. Opcjonalnie można obsłużyć komunikat w procedurze okna lub przekazać wiadomość do systemu w celu domyślnego przetwarzania.  
  
 Obiekt <xref:System.Windows.Interop.HwndSource> zdefiniowany jako obiekt nadrzędny dla obiektów wizualnych musi odwoływać się do procedury filtrowania komunikatów okna, którą podasz. Podczas tworzenia <xref:System.Windows.Interop.HwndSource> obiektu należy <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> ustawić właściwość, aby odwoływać się do procedury okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 W poniższym przykładzie przedstawiono kod do obsługi komunikatów z lewym i prawym przyciskiem myszy. Wartość współrzędnych pozycji trafienia myszy jest `lParam` zawarta w wartości parametru.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a>Przetwarzanie wiadomości Win32  
 Kod w poniższym przykładzie pokazuje, jak test trafień jest wykonywany względem hierarchii obiektów wizualnych zawartych w oknie win32 hosta. Można określić, czy punkt znajduje się w geometrii <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> obiektu wizualnego, za pomocą metody, aby określić główny obiekt wizualny i wartość współrzędnych, aby trafić test. W takim przypadku główny obiekt wizualny <xref:System.Windows.Interop.HwndSource.RootVisual%2A> jest wartością właściwości <xref:System.Windows.Interop.HwndSource> obiektu.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Aby uzyskać więcej informacji na temat testowania trafień w obiektach wizualnych, zobacz [Testowanie trafień w warstwie wizualnej](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Interop.HwndSource>
- [Test trafień z próbką interoperacyjności Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Test trafienia w warstwie Visual](hit-testing-in-the-visual-layer.md)
