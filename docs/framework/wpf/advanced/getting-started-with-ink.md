---
title: "Wprowadzenie do użycia atramentu"
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
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc8ffe9ad68060d9dfbcafe99133a736237a2bb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started-with-ink"></a>Wprowadzenie do użycia atramentu
Włączenie elektroniczne pismo odręczne aplikacji jest łatwiejsze niż kiedykolwiek. Odręczne powstał z jest następstwem COM i formularze systemu Windows metody programowania do osiągnięcia Pełna integracja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Nie trzeba zainstalować oddzielne zestawy SDK lub bibliotek środowiska uruchomieniowego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć w poniższych przykładach, należy najpierw zainstalować program Microsoft Visual Studio 2005 i [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Należy także zrozumienie sposobu pisania aplikacji dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby uzyskać więcej informacji na temat rozpoczynania pracy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="quick-start"></a>Szybki Start  
 Ta sekcja pomoże Ci napisać prosty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, która gromadzi odręczne.  
  
 Jeśli jeszcze tego nie zrobiono, zainstaluj program Microsoft Visual Studio 2005 i [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje zazwyczaj muszą być skompilowane zanim będzie możliwe wyświetlenie ich, nawet jeśli ich składać się wyłącznie z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Jednak [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] obejmuje aplikacji edytor XamlPad, zaprojektowane, aby przyspieszyć proces wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]— na podstawie interfejsu użytkownika. Aby wyświetlić i tinker z pierwszego kilka przykładów w tym dokumencie, można użyć tej aplikacji. Proces tworzenia skompilowanych aplikacji z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest uwzględnione w dalszej części tego dokumentu.  
  
 Aby uruchomić Edytor XAMLPad, kliknij przycisk **Start** menu wskaż **wszystkie programy**, wskaż polecenie **Microsoft Winndows SDK**, wskaż polecenie **narzędzia**i kliknij przycisk **Edytor XAMLPad**. W okienku renderowania Edytor XAMLPad renderuje kod XAML, napisany w okienku kodu. Można edytować kodu XAML, a zmiany są natychmiast widoczne w okienku renderowania.  
  
#### <a name="got-ink"></a>Otrzymano odręczne?  
 Aby uruchomić pierwszego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, która obsługuje odręczne:  
  
1.  Otwórz program Microsoft Visual Studio 2005  
  
2.  Utwórz nową **aplikacji systemu Windows (WPF)**  
  
3.  Typ `<InkCanvas/>` między `<Grid>` tagów  
  
4.  Naciśnij klawisz **F5** do uruchamiania aplikacji w debugerze  
  
5.  Przy użyciu pióro lub mysz, zapisać **Witaj świecie** w oknie  
  
 Napisanych odpowiednikiem odręczne aplikacja "hello world" o tylko 12 naciśnięcia klawiszy!  
  
#### <a name="spice-up-your-application"></a>Przypraw się na aplikację  
 Teraz korzystać z niektórych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Zastąp wszystko pomiędzy otwierającym \<okna > i zamykanie \</Window > tagów z następujący kod, aby uzyskać pędzla gradientu tła powierzchni pisma odręcznego.  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a>Przy użyciu animacji  
 Dla zabawy umożliwia animować kolory pędzla gradientu. Dodaj następujące [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] po upływie `</InkCanvas>` tag, ale przed zamknięciem `</Page>` tagu.  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a>Dodanie niektórych kodzie XAML  
 Gdy XAML ułatwia bardzo Projektowanie interfejsu użytkownika, dowolnej aplikacji rzeczywistych musi Dodaj kod obsługi zdarzenia. Poniżej przedstawiono prosty przykład, który powiększa pismo odręczne w odpowiedzi kliknij prawym przyciskiem myszy:  
  
 Ustaw `MouseRightButtonUp` obsługi w Twojej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 W Eksploratorze rozwiązań programu Visual Studio rozwiń Windows1.xaml i Otwórz plik CodeBehind Window1.xaml.cs lub Window1.xaml.vb, jeśli używasz programu Visual Basic. Dodaj następujący kod obsługi zdarzenia:  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 Teraz uruchom aplikację. Dodaj część pisma odręcznego, a następnie prawym przyciskiem myszy lub wykonaj odpowiednika naciśnij i przytrzymaj za pomocą pióra.  
  
#### <a name="using-procedural-code-instead-of-xaml"></a>Przy użyciu kodu procedurach zamiast XAML  
 Dostęp do wszystkich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji z kodu procedurach. Oto "odręczne aplikacji Hello World" dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] który nie używa żadnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wcale. Wklej poniższy kod do pustej aplikacji konsoli w programie Visual Studio. Dodaj odwołania do zestawów PresentationCore, PresentationFramework i WindowsBase i skompilować aplikację, naciskając klawisz **F5**:  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Elektroniczne pismo odręczne](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [Zbieranie pisma odręcznego](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [Rozpoznawania pisma ręcznego](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [Przechowywanie odręcznego](../../../../docs/framework/wpf/advanced/storing-ink.md)
